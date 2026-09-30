# Raptama Yahya Framer Portfolio - UI/UX Design System Reference

Dokumentasi komprehensif reverse-engineering UI/UX dan design tokens dari website [raptamayahya.framer.website](https://raptamayahya.framer.website/). Seluruh data, token, spesifikasi tipografi, anatomi komponen, dan visual styling diekstraksi langsung dari *computed styles*, stylesheets Framer, dan DOM runtime menggunakan Chromium/Edge DevTools.

---

## 1. Overview & Visual Identity

### Vibe, Tone & Aesthetic
- **Design Philosophy**: *Dark Minimalist / Neo-Brutalist Tech Luxury* (sering diasosiasikan dengan gaya modern *Linear*, *Vercel*, dan *Raycast*).
- **Mood & Tone**: Profesional, analitis, tenang, presisi tinggi (*data-driven engineering*), dan modern.
- **Visual Anchor**:
  - Background hitam murni (`#000000`) dengan card surface obsidian pekat (`#0d0d0d`).
  - Layering batas visual (*subtle borders*) yang tidak menggunakan warna solid tebal, melainkan kombinasi **inset highlight border** (`rgba(184, 180, 180, 0.14)`) serta frame padding 1.4px dengan fill `#3b3b3b`.
  - Efek pencahayaan halus menggunakan **radial gradient glow layers** di dalam tombol utama dan pill badges.
  - Showcase gambar berkonsep *monochrome-first* menggunakan CSS `filter: grayscale()` yang memberikan kesan visual elegan dan minim distorsi visual.
  - Tipografi display berskala besar (*massive headline scale*) hingga 92px menggunakan font **Satoshi** berbobot regular (400) yang kontras dengan body copy **Inter** yang bersih.

---

## 2. Color Palette

Berikut adalah daftar token warna yang diekstrak langsung dari CSS Variables `:root` Framer dan runtime computed styles:

| Token Name | Hex / RGBA Code | Computed Usage / Context |
| :--- | :--- | :--- |
| `--token-bg-canvas` | `#000000` (`rgb(0, 0, 0)`) | Background utama halaman (`body`, `html`) |
| `--token-surface-base` | `#0d0d0d` (`rgb(13, 13, 13)`) | Card background (Process card, FAQ, Stats banner, Badges) |
| `--token-surface-elevated` | `rgba(10, 10, 10, 0.4)` | Availability Status Pill background |
| `--token-surface-pill-glow` | `rgba(99, 99, 99, 0.3)` | "View Casestudy" interactive pill background |
| `--token-border-frame` | `#3b3b3b` (`rgb(59, 59, 59)`) | Frame pembungkus tombol utama (outer border simulation) |
| `--token-border-subtle` | `#ffffff1a` (`rgba(255, 255, 255, 0.1)`) | Garis tepi halus & divider |
| `--token-border-inset-top` | `rgba(184, 180, 180, 0.14)` | Top highlight stroke pada step badge & card inset |
| `--token-border-inset-dim` | `rgba(184, 180, 180, 0.08)` | Ambient inset border pada komponen sekunder |
| `--token-text-primary` | `#ffffff` (`rgb(255, 255, 255)`) | Heading H1, H2, judul card, dan tombol teks aktif |
| `--token-text-muted` | `#ffffffa6` (`rgba(255, 255, 255, 0.65)`) | Deskripsi body, subjudul, nav link default, label skill |
| `--token-text-faint` | `#a5a5a5` (`rgb(165, 165, 165)`) | Metadata, caption tanggal/periode, copyright |
| `--token-nav-glass-bg` | `rgba(0, 0, 0, 0.8)` | Fixed Header glassmorphism background |
| `--token-radial-glow-high` | `rgb(163, 163, 163)` | Hotspot radial glow primer di dalam tombol CTA |
| `--token-radial-glow-mid` | `rgb(115, 115, 115)` | Ambient radial glow sekunder di dalam tombol CTA |
| `--token-radial-glow-core` | `rgb(255, 255, 255)` | Specular highlight center pada hover button |
| `--token-shadow-dark` | `rgba(0, 0, 0, 0.4)` (`#0006`) | Ambient box shadow untuk card elevation |
| `--token-pulse-dot` | `rgb(189, 189, 189)` | Glowing ring pada status availability dot |

---

## 3. Typography Scale

Sistem tipografi menggunakan 3 font-family utama yang dimuat via Google Fonts / Fontshare:
1. **Satoshi** (`font-family: "Satoshi", "Satoshi Placeholder", sans-serif`): Digunakan khusus untuk Display, Headline H1, Section Title H2, dan Sub-heading H3.
2. **Inter Display** (`font-family: "Inter Display", "Inter Display Placeholder", sans-serif`): Digunakan untuk Lead Paragraph, Sub-headline, dan Tombol CTA berukuran besar.
3. **Inter** (`font-family: "Inter", sans-serif`): Digunakan untuk Body Text, Navbar Links, Status Pills, dan Badge Deskripsi.

### Skala Hierarki Tipografi

| Hierarchy / Level | Font Family | Size | Weight | Line Height | Letter Spacing | Color | Preset Class |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Hero Display (H1 Desktop)** | Satoshi | `92px` | 400 (Regular) | `92px` (1.0em) | `0em` | `#ffffff` | `.framer-styles-preset-1rsgxbj` |
| **Hero Display (H1 Tablet/Mobile)** | Satoshi | `44px` / `64px` | 400 (Regular) | `1.0em` | `0em` | `#ffffff` | `.framer-styles-preset-1rsgxbj` |
| **Section Title (H2)** | Satoshi | `44px` | 400 (Regular) | `44px` (1.0em) | `0em` | `#ffffff` | `.framer-styles-preset-1x8i0c5` |
| **Subsection / Card Title (H3)** | Satoshi | `30px` (or `34px`) | 500 (Medium) | `1.2em` (`36px`) | `-0.01em` | `#ffffff` | `.framer-styles-preset-1hm2l28` |
| **Body Large / Lead** | Inter Display | `18px` | 400 (Regular) | `1.6em` (`28.8px`) | `0em` | `#ffffff` | `.framer-styles-preset-gc0h9e` |
| **Body Subhead (Muted)** | Inter Display | `18px` | 400 (Regular) | `140%` (`25.2px`) | `0em` | `rgba(255, 255, 255, 0.65)` | `.framer-styles-preset-13fnooe` |
| **Body Base (Standard Text)** | Inter | `15px` | 400 (Regular) | `1.5em` (`22.5px`) | `-0.02em` (-0.3px) | `rgba(255, 255, 255, 0.65)` | `.framer-styles-preset-1af6am0` |
| **Nav Links / Pill Text** | Inter | `15px` | 400 (Regular) | `1.5em` (`22.5px`) | `-0.02em` | `rgba(255, 255, 255, 0.65)` | `.framer-styles-preset-1af6am0` |
| **Step Badge Number** | Inter / Satoshi | `14px` / `15px` | 500 (Medium) | `1.0em` | `0em` | `#ffffff` | Custom Inline |
| **Caption / Tiny Text** | Inter | `12px` | 400 (Regular) | `normal` | `0em` | `#a5a5a5` | Browser / Inline |

---

## 4. Spacing, Elevation & Radius

### A. Border Radius Scale
Sistem border radius dirancang dengan kurva sangat halus (*super-ellipse appearance*):
- `8px` (`rounded-lg`): Badge teknologi individual (Python, SQL, ML, dsb).
- `10px` (`rounded-[10px]`): Inner container tombol CTA.
- `11.5px` (`rounded-[12px]`): Outer border frame tombol CTA.
- `15px` (`rounded-[15px]`): Card FAQ accordion item.
- `17px` (`rounded-[17px]`): Thumbnail showcase project / card media preview.
- `18px` (`rounded-[18px]`): Stats banner wrapper container.
- `20px` (`rounded-[20px]`): Inner card container & About Me wrapper.
- `26px` (`rounded-[26px]`): Availability status pill badge.
- `30px` (`rounded-[30px]`): Process / Engineering workflow step cards.
- `40px` (`rounded-[40px]`): "View Casestudy" interactive pill button.
- `84px` - `100px` / `999px` (`rounded-full`): Status dot circular indicator, circular social icon link (`40px x 40px`), dan radial glow containers.

### B. Elevation & Box Shadow Layers
Semua shadow menggunakan lapisan pekat bernuansa hitam berdifusi tinggi (*wide spread ambient shadows*), dikombinasikan dengan *inset specular highlight stroke*:

1. **Card Floating Shadow**:
   ```css
   box-shadow: 16px 24px 20px 8px rgba(0, 0, 0, 0.4);
   ```
2. **Project Media Ambient Shadow**:
   ```css
   box-shadow: 20px 30px 20px 8px rgba(0, 0, 0, 0.4);
   ```
3. **FAQ Card Drop Shadow**:
   ```css
   box-shadow: 5px 18px 10px 8px rgba(0, 0, 0, 0.4);
   ```
4. **Specular Inset Highlight (Top Edge Light)**:
   ```css
   box-shadow: 0px 2px 0px 0px rgba(184, 180, 180, 0.14) inset;
   ```
5. **Interactive Pill Glow Shadow**:
   ```css
   box-shadow: 0px 0px 20px 4px rgba(92, 92, 92, 0.3);
   ```
6. **Availability Pulse Dot Glow**:
   ```css
   box-shadow: 0px 0px 14px 1px rgb(189, 189, 189);
   ```

### C. Backdrop Blur
- Header Navbar & Sticky Elements:
  ```css
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  ```
- Gradient Mask pada transisi overlay:
  ```css
  background: linear-gradient(180deg, rgba(0,0,0,0) 10%, #000000 20%);
  mask: linear-gradient(rgba(0,0,0,0) 0%, #000000 5%);
  ```

---

## 5. Core Components Breakdown

### 1. Floating Glass Navbar
- **Tag / Struktur**: `<header>` fixed di bagian paling atas viewport.
- **Height**: `72px` (Outer header), `64px` (Inner content row).
- **Background**: `rgba(0, 0, 0, 0.8)`.
- **Backdrop-Filter**: `blur(8px)`.
- **Padding**: `0px 40px`.
- **Layout**: Flex row, `justify-content: space-between`, `align-items: center`.
- **Brand Logo**: `width: 127px`, `height: 28px`.
- **Nav Links**:
  - Link item padding: `6px 12px`, `height: 64px`, `display: flex`, `align-items: center`.
  - Font: `Inter`, `15px`, `letter-spacing: -0.02em`.
  - Default Color: `rgba(255, 255, 255, 0.65)`.
  - Hover Color: `#ffffff`, dengan smooth transition `color 0.2s ease`.

```html
<!-- Navbar Anatomy Equivalent -->
<header class="fixed top-0 left-0 w-full h-[72px] bg-black/80 backdrop-blur-md z-50 flex items-center px-10 justify-between border-b border-white/5">
  <div class="flex items-center">
    <a href="#" class="inline-block w-[127px] h-[28px]">
      <img src="logo.svg" alt="Raptama Yahya" class="h-full w-auto" />
    </a>
  </div>
  <nav class="flex items-center gap-1">
    <a href="#projects" class="px-3 py-1.5 text-[15px] tracking-[-0.02em] text-white/65 hover:text-white transition-colors duration-200">Projects</a>
    <a href="#contact" class="px-3 py-1.5 text-[15px] tracking-[-0.02em] text-white/65 hover:text-white transition-colors duration-200">Contact</a>
  </nav>
</header>
```

---

### 2. Availability Status Pill Badge
- **Container**: `framer-189g6y2`
- **Height**: `42.5px`
- **Padding**: `10px 16px`
- **Background**: `rgba(10, 10, 10, 0.4)`
- **Border Radius**: `26px` (outer wrapper `40px`)
- **Layout**: `display: flex`, `gap: 10px`, `align-items: center`
- **Pulsing Indicator Dot**:
  - Ukuran: `7px x 7px` lingkaran (`border-radius: 84px` / `50%`)
  - Warna: `rgba(255, 255, 255, 0.65)`
  - Glow Shadow: `0px 0px 14px 1px rgb(189, 189, 189)` dengan animasi pulse
- **Typography**: Inter 15px, Regular (400), Line-height 22.5px, Color `#ffffff`

```html
<!-- Availability Pill Anatomy Equivalent -->
<div class="inline-flex items-center gap-2.5 px-4 py-2.5 rounded-[26px] bg-[#0a0a0a]/40 border border-white/10 backdrop-blur-sm">
  <span class="relative flex h-[7px] w-[7px]">
    <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-white/40 opacity-75"></span>
    <span class="relative inline-flex rounded-full h-[7px] w-[7px] bg-white/70 shadow-[0_0_14px_1px_rgba(189,189,189,0.8)]"></span>
  </span>
  <span class="text-[15px] font-normal leading-[1.5em] tracking-[-0.02em] text-white">
    Available for Data Science Internships
  </span>
</div>
```

---

### 3. Primary Glowing CTA Button ("See Projects" / "See My GitHub")
Tombol ini menggunakan teknik arsitektur multi-layer khas Framer untuk menghasilkan efek border illuminated & internal radial glow yang sangat dinamis:
- **Layer 1 (Outer Frame / Border Simulation)**:
  - Width: `~148px` - `170px`, Height: `47.6px` (48px)
  - Padding: `1.4px`
  - Background: `rgb(59, 59, 59)` (`#3b3b3b`)
  - Border-Radius: `11.5px`
- **Layer 2 (Inner Base Container)**:
  - Background: `rgb(0, 0, 0)` (`#000000`)
  - Border-Radius: `10px`
  - Padding: `8px 24px`
  - Position: `relative`, `overflow: hidden`
- **Layer 3 (Internal Radial Glow Accents)**:
  - Glow A: `radial-gradient(50% 50%, rgb(163, 163, 163) 0%, rgba(0, 0, 0, 0) 100%)` (77px x 41px, rounded-full)
  - Glow B: `radial-gradient(50% 50%, rgb(115, 115, 115) 0%, rgba(0, 0, 0, 0) 100%)` (92px x 40px, rounded-full)
- **Layer 4 (Typography)**:
  - Font: `Inter Display`, `18px`, Weight `400`, Line-height `1.6em`, Color `#ffffff`

```html
<!-- Primary Button Anatomy Equivalent -->
<a href="#projects" class="group relative inline-flex items-center justify-center p-[1.4px] rounded-[11.5px] bg-[#3b3b3b] shadow-[0_1px_9px_0_rgba(255,255,255,0)] transition-all duration-300 hover:bg-[#555555] hover:scale-[1.02]">
  <div class="relative flex items-center justify-center px-6 py-2 rounded-[10px] bg-black overflow-hidden w-full h-full">
    <!-- Ambient Internal Glows -->
    <div class="absolute -top-3 left-1/4 w-[77px] h-[41px] rounded-full bg-[radial-gradient(50%_50%,_rgb(163,163,163)_0%,_rgba(0,0,0,0)_100%)] opacity-70 group-hover:opacity-100 transition-opacity duration-300 pointer-events-none"></div>
    <div class="absolute -bottom-3 right-1/4 w-[92px] h-[40px] rounded-full bg-[radial-gradient(50%_50%,_rgb(115,115,115)_0%,_rgba(0,0,0,0)_100%)] opacity-60 group-hover:opacity-100 transition-opacity duration-300 pointer-events-none"></div>
    
    <!-- Text -->
    <span class="relative z-10 text-[18px] font-normal leading-[1.6em] text-white">
      See Projects
    </span>
  </div>
</a>
```

---

### 4. Interactive Casestudy Pill Button ("View Casestudy")
- **Tag**: `<a>`
- **Padding**: `12px 20px`
- **Border-Radius**: `40px` (Pill capsule)
- **Background**: `rgba(99, 99, 99, 0.3)`
- **Box-Shadow**: `0px 0px 20px 4px rgba(92, 92, 92, 0.3)`
- **Typography**: Inter 12px / 14px, Color `#ffffff`
- **Hover Behavior**: Box shadow intensifies, scale `1.04`

---

### 5. Project Showcase Card
- **Outer Wrapper**: `border-radius: 20px`, `box-shadow: 16px 24px 20px 8px rgba(0, 0, 0, 0.4)`
- **Image Container**:
  - `border-radius: 17px`
  - `box-shadow: 20px 30px 20px 8px rgba(0, 0, 0, 0.4)`
  - `filter: grayscale(100%)`
  - **Transition**: `filter 0.4s ease, transform 0.4s ease`
  - **Hover**: `filter: grayscale(0%)`, `transform: scale(1.015)`
- **Gap / Content Row**: `gap: 18px`, `display: flex`, `flex-direction: column`

---

### 6. Process / Engineering Workflow Step Card
- **Background**: `rgb(13, 13, 13)` (`#0d0d0d`)
- **Border Radius**: `30px`
- **Padding**: `44px 32px 32px 32px`
- **Gap**: `24px`
- **Shadow**: `16px 24px 20px 8px rgba(0, 0, 0, 0.4)`
- **Step Number Badge**:
  - Width & Height: `34px x 34px`
  - Shape: Lingkaran (`border-radius: 100px`)
  - Background: `#0d0d0d`
  - Border Highlight: `box-shadow: 0px 2px 0px 0px rgba(184, 180, 180, 0.14) inset`
  - Text: `1`, `2`, `3` warna `#ffffff`, font-weight 500

---

### 7. Stats Banner Container
- **Background**: `rgb(13, 13, 13)` (`#0d0d0d`)
- **Width**: `1200px` (responsive fluid)
- **Border Radius**: `18px`
- **Padding**: `48px 40px`
- **Gap**: `24px`
- **Numbers**: Satoshi Display `44px`, Weight 400, `#ffffff`
- **Labels**: Inter `15px`, `rgba(255, 255, 255, 0.65)`

---

### 8. FAQ Accordion Item Card
- **Background**: `rgb(13, 13, 13)` (`#0d0d0d`)
- **Border Radius**: `15px`
- **Padding**: `20px`
- **Gap**: `10px`
- **Shadow**: `5px 18px 10px 8px rgba(0, 0, 0, 0.4)`
- **Title (Question)**: Satoshi `18px`, Weight 500, `#ffffff`
- **Answer**: Inter `15px`, `rgba(255, 255, 255, 0.65)`

---

### 9. Social Icon Buttons (Footer)
- **Size**: `40px x 40px`
- **Border Radius**: `100px` (`rounded-full`)
- **Padding**: `8px`
- **Border**: `1px solid rgba(255, 255, 255, 0.15)` atau glass background
- **Hover**: Background `rgba(255, 255, 255, 0.1)`, `transform: translateY(-2px)`

---

## 6. Layout & Spacing Rules

### Breakpoints & Responsive Scale
Framer mendefinisikan 3 varian breakpoint utama yang teridentifikasi dalam stylesheets:
- **Desktop**: Min-width `1200px` (Canvas standar `1440px`).
- **Tablet**: Max-width `1199px`, Min-width `810px`.
- **Mobile**: Max-width `809px` (Phone canvas `390px`).

### Container Max-Width Scale
- **Hero Column Max-Width**: `840px` (membatasi teks judul agar tidak terlalu lebar di layar ultra-wide).
- **Standard Content Section**: `1200px` - `1280px` (`max-w-[1280px] mx-auto`).
- **Full Viewport Section Wrapper**: `1600px` / `1680px`.
- **FAQ Grid / Card Max-Width**: `498px` - `540px`.

### Grid & Flex Gap System
- **Section Stack Gap**: `80px` pada desktop (antara Hero heading dan CTA) / `44px` antar subsection.
- **Card Internals Gap**: `24px` (Process cards) / `18px` (Project items).
- **Badge & Pill Elements Gap**: `10px` / `6px` (Nav links & status pills).

---

## 7. Motion & Micro-Interactions

### Framer Motion & CSS Curves
Transisi pada site ini ditangani oleh **Framer Motion runtime** yang menggunakan model fisika *Spring Animation*:
- **Spring Parameter Utama**:
  ```javascript
  {
    type: "spring",
    damping: 25,
    stiffness: 250,
    mass: 1
  }
  ```
- **CSS Transition Fallback**:
  ```css
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  ```

### Interaction Specifications
1. **Grayscale Image Reveal**:
   - Initial: `filter: grayscale(100%)`
   - Hover: `filter: grayscale(0%)`, `transform: scale(1.02)`
   - Duration: `0.4s ease-out`
2. **Radial Glow Intensification**:
   - Initial: `opacity: 0.6`
   - Hover: `opacity: 1.0`, glow width bertambah ~10%
3. **Smooth Scrolling**:
   - Website mengintegrasikan library **Lenis** (`html.lenis`) untuk momentum smooth scroll yang elegan tanpa patah-patah.

---

## 8. Iconography & Assets

- **Icon Format**: Inline SVG murni.
- **ViewBox Standar**: `0 0 256 256` (merupakan spesifikasi ikon standar dari library **Phosphor Icons**).
- **Icon Sizing**:
  - Primary UI Icons: `25px x 25px` (rendered via `fill="currentColor"` atau `fill="#ffffff"`).
  - Social Links: `20px x 20px` di dalam container `40px x 40px`.
- **Image Assets**: Format `.webp` dan `.avif` modern yang di-host pada CDN `framerusercontent.com` dengan aspect ratio 16:9 atau 4:3.

---

## 9. Tailwind CSS Config Equivalent

Gunakan file konfigurasi `tailwind.config.js` berikut untuk mereplikasi sistem desain ini secara instan ke dalam project berbasis Tailwind CSS:

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  darkMode: 'class',
  content: [
    './pages/**/*.{js,ts,jsx,tsx,mdx}',
    './components/**/*.{js,ts,jsx,tsx,mdx}',
    './app/**/*.{js,ts,jsx,tsx,mdx}',
  ],
  theme: {
    extend: {
      colors: {
        canvas: '#000000',
        surface: {
          DEFAULT: '#0d0d0d',
          elevated: 'rgba(10, 10, 10, 0.4)',
          pill: 'rgba(99, 99, 99, 0.3)',
          frame: '#3b3b3b',
        },
        border: {
          subtle: 'rgba(255, 255, 255, 0.1)',
          inset: 'rgba(184, 180, 180, 0.14)',
          'inset-dim': 'rgba(184, 180, 180, 0.08)',
        },
        text: {
          primary: '#ffffff',
          muted: 'rgba(255, 255, 255, 0.65)',
          faint: '#a5a5a5',
        },
      },
      fontFamily: {
        satoshi: ['Satoshi', 'sans-serif'],
        inter: ['Inter', 'sans-serif'],
        'inter-display': ['Inter Display', 'sans-serif'],
      },
      fontSize: {
        'display-hero': ['92px', { lineHeight: '1.0em', letterSpacing: '0em', fontWeight: '400' }],
        'display-mobile': ['44px', { lineHeight: '1.0em', letterSpacing: '0em', fontWeight: '400' }],
        'section-title': ['44px', { lineHeight: '1.0em', letterSpacing: '0em', fontWeight: '400' }],
        'card-title': ['30px', { lineHeight: '1.2em', letterSpacing: '-0.01em', fontWeight: '500' }],
        'body-lead': ['18px', { lineHeight: '1.6em', letterSpacing: '0em', fontWeight: '400' }],
        'body-subhead': ['18px', { lineHeight: '140%', letterSpacing: '0em', fontWeight: '400' }],
        'body-base': ['15px', { lineHeight: '1.5em', letterSpacing: '-0.02em', fontWeight: '400' }],
      },
      borderRadius: {
        card: '30px',
        stats: '18px',
        preview: '17px',
        faq: '15px',
        btn: '11.5px',
        'btn-inner': '10px',
        pill: '26px',
        'capsule-lg': '40px',
      },
      boxShadow: {
        card: '16px 24px 20px 8px rgba(0, 0, 0, 0.4)',
        media: '20px 30px 20px 8px rgba(0, 0, 0, 0.4)',
        faq: '5px 18px 10px 8px rgba(0, 0, 0, 0.4)',
        'pill-glow': '0px 0px 20px 4px rgba(92, 92, 92, 0.3)',
        'pulse-dot': '0px 0px 14px 1px rgb(189, 189, 189)',
        'inset-top': '0px 2px 0px 0px rgba(184, 180, 180, 0.14) inset',
        'inset-dim': '0px 2px 0px 0px rgba(184, 180, 180, 0.08) inset',
      },
      maxWidth: {
        hero: '840px',
        content: '1280px',
        canvas: '1600px',
      },
      animation: {
        'pulse-subtle': 'pulse 2.5s cubic-bezier(0.4, 0, 0.6, 1) infinite',
      },
    },
  },
  plugins: [],
};
```

---

## 10. Web Font Imports

Untuk mengaktifkan font Satoshi dan Inter secara identik seperti di situs aslinya, tambahkan baris berikut ke `index.html` atau root CSS (`globals.css`):

```html
<!-- Satoshi Font via Fontshare -->
<link href="https://api.fontshare.com/v2/css?f[]=satoshi@400,500,700&display=swap" rel="stylesheet">

<!-- Inter & Inter Display via Google Fonts -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
```

---
*Dokumentasi ini dibuat berdasarkan reverse-engineering otomatis dan inspeksi DOM runtime live dari https://raptamayahya.framer.website/.*
