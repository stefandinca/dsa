# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

DSA Environment - Romanian environmental consulting services website. A multi-page static website offering services for waste management, environmental reporting, permits/authorizations, and environmental control assistance.

**Language**: Romanian (ro)
**Company**: DSA Environment - Environmental consulting for Romanian businesses
**Location**: Corbeanca, Ilfov, Romania

## Architecture & Technology Stack

### Frontend Stack
- **HTML5**: Multi-page static website (no build process)
- **TailwindCSS**: Via CDN (`https://cdn.tailwindcss.com`)
- **Vanilla JavaScript**: Inline in each HTML file, no frameworks
- **CSS**: Custom animations and styles in `styles.css`
- **Fonts**: Google Fonts (Inter, Space Grotesk)

### Page Structure
The site consists of 5 main pages:
- `index.html` - Homepage with hero, services overview, expertise, articles carousel, contact form
- `managementul-deseurilor.html` - Waste Management services
- `raportari-afm.html` - AFM (Environmental Fund Administration) Reporting services
- `raportari-de-mediu.html` - Environmental Reporting services (SIM system)
- `asistenta-controale.html` - Environmental Control Assistance services

### Shared Components Pattern

All pages share identical navigation and footer structures. When updating navigation or footer:
1. Make changes to ALL 5 HTML files
2. Navigation includes dropdown menus (desktop) and mobile hamburger menu
3. Footer has 4 columns: logo/description, services, company, legal

## Design System

### Color Palette (Tailwind Config)
Defined inline via `<script>` tag in HTML files with Tailwind config:

**Primary Colors** (Green theme):
- primary-50 to primary-950: Green gradient (#f0fdf4 to #052e16)
- Main brand green: primary-600 (#16a34a)

**Accent Colors**:
- accent-500 to accent-700: Pink/magenta (#ec4899 to #be185d)
- brand-red: #E11D48 (rose-600) - used for emphasis text

**Typography**:
- Display font: 'Space Grotesk' - headings and bold text
- Body font: 'Inter' - paragraphs and UI

### Key CSS Classes & Animations

**Glassmorphism** (`.glass`):
- Light mode: `rgba(255, 255, 255, 0.35)` with `backdrop-filter: blur(10px)`
- Dark mode: `rgba(0, 0, 0, 0.3)` with adjusted border

**Custom Animations**:
- `.gradient-bg` - Animated gradient background (15s loop)
- `.mesh-gradient` - Multi-color radial gradient overlay with blur
- `.fade-in` - Opacity + translateY animation (triggered via IntersectionObserver)
- `.float` - Vertical floating animation (6s)
- `.particle` - Particle floating effect for hero backgrounds
- `.carousel-track` - Horizontal infinite scroll (40s)

**Interactive Elements**:
- `.magnetic-btn` - Button with mouse-following effect
- `.hover-glow` - Radial glow on hover
- `.service-card` - Cards with shine-through effect on hover

### Dark Mode
- Class-based: Toggle `dark` class on `<html>` element
- Persisted via localStorage: `darkMode` key (string "true"/"false")
- Toggle button in navigation bar

## JavaScript Functionality

All JavaScript is inline in each HTML file (no external JS files). Each page implements:

### Core Features (Implemented on All Pages)
1. **Mobile Menu Toggle** - Hamburger menu with slide-in animation
2. **Dark Mode Toggle** - Persistent via localStorage
3. **Scroll Progress Bar** - Top of viewport, scales with scroll
4. **Fade-in Animations** - IntersectionObserver based
5. **Magnetic Button Effect** - Buttons follow mouse movement
6. **Smooth Scroll** - Anchor links with smooth scrolling
7. **Particle Background** - Animated particles in hero sections
8. **Mobile & Desktop Dropdown Menus** - Service and authorization menus

### Page-Specific Features
- **index.html only**: Contact form submission (currently shows alert), number counter animation
- **All pages**: Navbar background blur on scroll (planned but variable not always defined)

## Content Structure

### Navigation Menu Structure
**Servicii (Services)** dropdown:
- Managementul deșeurilor → `managementul-deseurilor.html`
- Raportări AFM → `raportari-afm.html`
- Raportări de mediu → `raportari-de-mediu.html`
- Asistență controale mediu → `asistenta-controale.html`

**Avize și autorizații (Permits)** dropdown:
- Acordul de Mediu → `#avize`
- Acordul de preluare ape uzate → `#avize`
- Autorizația de Mediu → `#avize`

### Contact Information
- **Phone**: +40 721 900 280
- **Email**: contact@dsa-environment.ro
- **Address**: Șos. Unirii 236, Corbeanca, Ilfov
- **Google Maps**: https://maps.app.goo.gl/s2RUzgURwtJqLxp48

### Company Credentials
- **ISO Certifications**: ISO 9001 & 14001
- **Credentials**: Elaborator Studii (environmental impact studies)
- **Experience**: 500+ clients, 5000+ environmental reports, 20000+ consulting hours

## Development Workflow

### No Build Process
- Direct HTML/CSS editing
- TailwindCSS loaded via CDN (no compilation needed)
- Changes are immediately visible on page refresh
- No package.json, no dependencies, no build tools

### Making Changes

**Updating Navigation/Footer**:
1. Update all 5 HTML files (index.html, managementul-deseurilor.html, raportari-afm.html, raportari-de-mediu.html, asistenta-controale.html)
2. Ensure consistency across all pages
3. Test mobile menu on each page

**Updating Tailwind Config**:
- Modify the inline `<script>tailwind.config = {...}</script>` in each HTML file
- index.html, managementul-deseurilor.html, raportari-afm.html, and raportari-de-mediu.html have inline config
- asistenta-controale.html references styles.css only

**Adding New Animations**:
- Add CSS to `styles.css` for shared animations
- Inline styles in `<style>` tags are avoided; use Tailwind utilities or styles.css

**Images**:
- Stored in `/img/` directory
- Logo files: `logo-dsa-light.png`, `logo-dsa.png`
- Service icons: 50x50 PNG files (management-50x50.png, etc.)
- Hero/content images: AVIF format for optimization

### Common Patterns

**Section Structure**:
```html
<section class="py-20/py-32 bg-white dark:bg-gray-950">
    <div class="container mx-auto px-6">
        <div class="text-center mb-16 fade-in">
            <h2 class="font-display font-black text-4xl md:text-6xl mb-6">
                Title <span class="gradient-text">Highlighted</span>
            </h2>
            <p class="text-xl text-gray-600 dark:text-gray-400">
                Subtitle text
            </p>
        </div>
        <!-- Content -->
    </div>
</section>
```

**Service Cards**:
```html
<div class="service-card glass rounded-3xl p-8 hover:shadow-2xl transition-all fade-in">
    <div class="w-16 h-16 bg-gradient-to-br from-primary-500 to-primary-700 rounded-2xl flex items-center justify-center mb-6">
        <!-- Icon SVG -->
    </div>
    <h3 class="font-display font-bold text-2xl mb-4">Title</h3>
    <p class="text-gray-600 dark:text-gray-400">Description</p>
</div>
```

## Legal & Compliance Context

The website deals with Romanian environmental law and EU directives:
- **OUG 92/2021** - Waste management ordinance
- **Legea 249/2015** - Packaging waste recycling targets
- **Decizia Comisiei UE 2000/532/CE** - Waste classification
- **AFM** - Administrația Fondului pentru Mediu (Environmental Fund Administration)
- **APM** - Agenția pentru Protecția Mediului (Environmental Protection Agency)
- **Garda de Mediu** - Environmental Guard (enforcement agency)

## Testing Checklist

When making changes, verify:
- [ ] All 5 pages load without errors
- [ ] Dark mode toggle works and persists
- [ ] Mobile menu opens/closes smoothly on all pages
- [ ] Desktop dropdowns appear on hover
- [ ] Mobile dropdowns expand on click
- [ ] Smooth scroll works for anchor links
- [ ] Contact form (index.html) shows alert on submit
- [ ] All navigation links point to correct pages
- [ ] Responsive design works on mobile, tablet, desktop viewports
- [ ] Fade-in animations trigger on scroll

## Git Status Notes

Initial uncommitted changes per git status:
- Modified: `asistenta-controale.html`, `index.html`
- New files: `managementul-deseurilor.html`, `raportari-afm.html`, `raportari-de-mediu.html`, `styles.css`
- New images in `/img/` directory
- Documentation: `CLAUDE.md`
