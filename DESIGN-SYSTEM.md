# Design System — Time to Integrate
## Tom Æon · The Essence Way

This file is the single source of truth for all visual rules governing the webpage.
Edit values here first, then apply them to index.html.

---

## Color Palette

| Token | Hex | Use |
|---|---|---|
| `--crimson` | `#a02020` | Primary action color: CTA buttons, title accents, blockquote borders, rule lines, phase numbers |
| `--crimson-dark` | `#7a1515` | Button hover state |
| `--crimson-glow` | `rgba(160,32,32,0.35)` | Button hover glow shadow |
| `--charcoal` | `#1c1c1c` | High-contrast headings (h1, h2, h3) |
| `--forest` | `#3d5a3e` | Section labels, table row labels, nature SVG graphics, nav logo |
| `--forest-mid` | `#4e7050` | Hover states for forest elements |
| `--forest-light` | `#6a8f6c` | Subtle accents, journey timeline line |
| `--gold` | `#9a7818` | Price display (€333), price box border |
| `--gold-mid` | `#b89428` | Gold hover |
| `--gold-light` | `#d4b04a` | Gold subtle accents |
| `--cream` | `#f7f3ee` | Primary page background |
| `--cream-mid` | `#eee8de` | Alternating section background (slightly deeper) |
| `--cream-deep` | `#e5ded4` | Investment section background |
| `--ink` | `#252018` | Body text, dark headings |
| `--ink-mid` | `#524639` | Paragraph text, secondary text |
| `--ink-soft` | `#8c7d6c` | Captions, labels, subtle text |
| `--gray` | `#7a7a7a` | Neutral secondary |
| `--border` | `rgba(61,90,62,0.15)` | Section dividers, card borders |
| `--border-gold` | `rgba(154,120,24,0.2)` | Price box border |

---

## Typography

| Role | Font | Size | Weight | Style |
|---|---|---|---|---|
| Body | Cormorant Garamond | 18px | 300 | Normal |
| H1 (hero) | Cormorant Garamond | clamp(52px,9vw,100px) | 300 | Normal; `em` → crimson italic |
| H2 (section) | Cormorant Garamond | clamp(30px,4.5vw,50px) | 300 | Normal; `em` → crimson italic |
| H3 | Cormorant Garamond | 20px | 400 | Normal |
| Nav logo | Cormorant Garamond | 17px | 400 | Italic |
| Section labels | Inter | 10px | 500 | Uppercase, 0.28em spacing, forest green |
| Buttons | Inter | 11–12px | 500 | Uppercase, 0.12–0.14em spacing |
| Blockquote | Cormorant Garamond | 21px | 300 | Italic, crimson left border |
| Captions | Inter | 10px | 400 | Uppercase, 0.14em spacing |

**Google Fonts import:**
```
Cormorant+Garamond:ital,wght@0,300;0,400;0,500;0,600;1,300;1,400;1,500
Inter:wght@300;400;500
```

---

## Buttons

### Primary (Crimson filled)
- Background: `--crimson`
- Hover: `--crimson-dark`, lift `translateY(-3px)`, glow `box-shadow: 0 8px 28px var(--crimson-glow)`
- Shimmer: white glint sweeps left→right on hover (`::before` pseudo, `shimmer` keyframe)
- Padding: `18px 52px`

### Outline (Crimson bordered)
- Border + text: `--crimson`, transparent background
- Hover: subtle crimson fill `rgba(160,32,32,0.07)`, same lift + shadow

### Light (for dark/forest background)
- Border + text: `rgba(240,236,230,0.45)` / `#f0ece6`
- Hover: slightly brighter background, lift + shadow

---

## Scroll Reveal System

All section content uses the `.reveal` class. JavaScript (IntersectionObserver) adds `.in` when the element enters the viewport.

```css
.reveal          → fade up (default)
.reveal.slide-left → slide from left
.reveal.scale-up   → slight scale-in
.r-d1 through .r-d6 → staggered delays: 0.1s → 0.75s
```

**Threshold:** 12% visible · **Root margin:** 0 0 -40px 0 (triggers slightly before bottom of screen)

---

## 3D Depth / Layering

Sections feel like stacked cards you descend through:
- `layer-card` class → `box-shadow: 0 6px 40px rgba(0,0,0,0.07)`
- `layer-deep` class → `box-shadow: 0 10px 60px rgba(0,0,0,0.1)`
- Background color alternates: cream → cream-mid → cream-deep → cream (cycling)
- Hero parallax: `.hero-tree` moves at 25% of scroll speed via JS (`translateY(scrollY * 0.25)px`)

---

## Navigation

- Left: "From Knowing to Living" — italic Cormorant Garamond, 17px
- Right: Single "Apply Now" button — crimson filled, 12px Inter uppercase, padding 12px 32px
- Background: `rgba(247,243,238,0.96)` with `backdrop-filter: blur(14px)`
- Height: 72px

---

## Animations

| Name | Use |
|---|---|
| `shimmer` | Button hover glint sweep |
| `breathe` | Hero tree subtle pulse (opacity 0.04→0.09, 8s loop) |
| `fadeUp` | Hero section load-in (opacity 0→1 + translateY) |
| Scroll reveal | IntersectionObserver → `.reveal` gets `.in` class |

---

## Responsive Breakpoints

| Breakpoint | Change |
|---|---|
| `≤860px` | About section: stacked column, photo unsticky |
| `≤700px` | Nav simplified, all sections reduce to 24px horizontal padding, bonus grid stacked |

---

## Content → Email

All CTA buttons link to: `mailto:hello@tomaeon.com`

---

## Files in This Folder

| File | Purpose |
|---|---|
| `index.html` | The complete single-page website |
| `tom.jpg` | Photo of Tom Æon (save your photo here with this exact filename) |
| `Launch Webpage.bat` | Double-click to open the page in your browser |
| `DESIGN-SYSTEM.md` | This file — visual rules and design tokens |
