# Lenovo MDS (Enterprise Operations Portal) Design System

> **Theme Identity:** Lenovo MDS / Motorola Service & Operations Portal Theme (derived from the classic Airport/Aircraft enterprise administrative design system with modern high-density operational styling).
> **Target Use-Case:** Dashboards, BI analytics, reporting tools, ERP/CRM portals, supply chain monitoring, and high-density operational web applications.

---

## 1. Design System Overview & Architecture

The Lenovo MDS UI is an **enterprise-grade, high-density dashboard and operations interface**. It prioritizes **data scannability, vertical compact layout, distinct functional zoning, and responsive operational workflows**.

### Key Architectural Pillars:
1. **Persistent Global Navbar**: Dark gradient header (`#4d5b76` to `#6f80a1`) providing brand identity, quick top-level global module links, and user context.
2. **Dedicated 240px Fixed/Collapsible Sidebar**: Hierarchical accordion navigation with distinct category headers, active indicator left-borders (`4px solid`), and item badges.
3. **Structured Content Canvas**: Left-bordered main panel with subtle gray background `#f8fafc` or pure white `#ffffff`, separated from navigation by crisp 1px borders.
4. **Dedicated Header & Sub-Header Ribbon**: Breadcrumbs bar styled with a subtle metallic gradient (`#efeff0` to `#fafafa`) and integrated KPI/quick-action toolbars.
5. **High-Density Data Presentation**: Compact base typography (`13px`), tight table rows (`padding: 6px 10px`), and high-contrast status pills.

---

## 2. Color Palette & Design Tokens

### Primary Theme: `theme-blue` (Lenovo MDS Default)
The core aesthetic uses a slate steel-blue header with neutral cool grays for work surfaces.

```css
:root {
  /* Primary Brand & Header Gradients */
  --mds-primary-gradient-start: #4d5b76;
  --mds-primary-gradient-end: #6f80a1;
  --mds-primary: #4d5b76;
  --mds-primary-hover: #3b475d;
  --mds-primary-light: #eff3f8;

  /* Surfaces & Backgrounds */
  --mds-bg-body: #f8fafc;
  --mds-bg-surface: #ffffff;
  --mds-bg-sidebar: #fafafa;
  --mds-bg-sidebar-hover: #efeff0;
  --mds-bg-sidebar-active: #e5e5ea;
  --mds-bg-subtle: #eeeeee;

  /* Borders & Dividers */
  --mds-border-subtle: #eee;
  --mds-border-default: #dcdcdc;
  --mds-border-strong: #c8c8cb;
  --mds-border-nav-active: #909096;

  /* Typography Colors */
  --mds-text-primary: #222222;
  --mds-text-secondary: #444444;
  --mds-text-muted: #666666;
  --mds-text-disabled: #999999;
  --mds-text-inverse: #ffffff;

  /* Functional & Status Colors */
  --mds-success-bg: #c1e2b3;
  --mds-success-border: #a3d48e;
  --mds-success-text: #09ae00;

  --mds-warning-bg: #f7ecb5;
  --mds-warning-border: #f2e187;
  --mds-warning-text: #de8d00;
  --mds-yellow-action: #caba00;

  --mds-danger-bg: #fcf2f2;
  --mds-danger-border: #dfb5b4;
  --mds-danger-text: #8e0018;

  --mds-info-bg: #d9edf7;
  --mds-info-border: #85c5e5;
  --mds-info-text: #0077ae;

  /* Elevation & Shadows */
  --mds-shadow-navbar: 0px 1px 3px rgba(0, 0, 0, 0.15);
  --mds-shadow-card: 0 1px 2px rgba(0, 0, 0, 0.05);
  --mds-shadow-dialog: 0 4px 16px rgba(0, 0, 0, 0.15);

  /* Layout Constants */
  --mds-sidebar-width: 240px;
  --mds-navbar-height: 48px;
  --mds-radius-sm: 3px;
  --mds-radius-md: 4px;
}
```

---

### Alternative Theme Palettes (Multi-Tenant / Multi-Environment Support)
The system supports alternate header colorways via body classes:

| Class Name | Start Color | End Color | Theme Feel |
| :--- | :--- | :--- | :--- |
| `.theme-blue` (Default) | `#4d5b76` | `#6f80a1` | Lenovo MDS Slate Steel |
| `.theme-dark` | `#444444` | `#6a6a6a` | Industrial Charcoal |
| `.theme-navy` | `#334a78` | `#4a6bae` | Deep Cobalt Blue |
| `.theme-steel` | `#4b648b` | `#718ab2` | Modern Metallic Blue |
| `.theme-earth` | `#534a37` | `#817355` | Bronze Warm Gold |
| `.theme-slate` | `#252c38` | `#435066` | Midnight Navy / Black |
| `.theme-neutral` | `#777777` | `#9d9d9d` | Clean Enterprise Silver |
| `.theme-olive` | `#616055` | `#8a8879` | Tactical Khaki Olive |

---

## 3. Typography & Hierarchy

The typography focuses on **information density and rapid numerical scanning**.

- **Font Family:** `system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif`
- **Monospace Family (Data/IDs):** `"JetBrains Mono", "SF Mono", Menlo, Monaco, Consolas, monospace`
- **Base Body Size:** `13px` (compact enterprise standard)
- **Base Line Height:** `1.42857` (standard line height for high-density forms)

### Type Scale:
- **Display / Top Titles:** `26px` (`font-weight: 700`, `--mds-text-primary`)
- **Page Header `h1`:** `20px - 22px` (`font-weight: 600`, line-height: `1.2em`)
- **Section Header `h2`:** `16px - 18px` (`font-weight: 600`)
- **Card / Panel Header `h3`:** `14px - 15px` (`font-weight: 600`)
- **Body / Form Labels:** `13px` (`font-weight: 500`)
- **Table Data / Cells:** `12px - 13px` (`font-weight: 400` or `500`)
- **Muted Notes / Footnotes / Micro-Labels:** `11px` (`font-weight: 400`, color `#777`)

---

## 4. Layout Architecture & Structure

```
+-----------------------------------------------------------------------------------+
|  [Brand Icon] Lenovo MDS | Module 1 | Module 2 | Module 3         [User / Settings]  |  <-- Top Navbar (48px)
+------------------------+----------------------------------------------------------+
|  SIDEBAR (240px)       |  Breadcrumbs: Home > Operations > Service Orders         |  <-- Breadcrumbs Bar (34px)
|  --------------------  +----------------------------------------------------------+
|  v ORDER MANAGEMENT    |  PAGE TITLE (h1)                        [Action Buttons] |
|    * Open Orders       +----------------------------------------------------------+
|    * Basic Report (act)|  [FILTER PANEL / SEARCH WELL]                            |
|    * Inventory Status  |  Date: [____]  Vendor: [_____]  Status: [_____] [Filter] |
|                        +----------------------------------------------------------+
|  > PARTS & SHIPPING    |  [KPI SUMMARY WIDGETS]                                   |
|  > REPORTING           |  [ 1,248 Open ]  [ 98.4% SLA ]  [ 12 Escalated ]         |
|  > ADMINISTRATION      +----------------------------------------------------------+
|                        |  [HIGH-DENSITY DATA TABLE / AG-GRID / REPORT VIEW]      |
|                        |  | ID | Model | Country | Status | TAT | Action |         |
|                        |  |----------------------------------------------|         |
|                        |  |... | ..... | ....... | ...... | ... | ...... |         |
+------------------------+----------------------------------------------------------+
```

### Layout Grid Rules:
1. **Container Margin**: Content area offset `margin-left: 240px` when sidebar is open.
2. **Mobile / Responsive Fold**: At screen width `<= 768px`, the sidebar collapses offscreen or toggles into an overlay drawer, resetting `margin-left: 0`.
3. **Sticky Controls**: Top navigation bar remains sticky (`position: sticky; top: 0; z-index: 1000;`).
4. **Padding System**: Standard panel padding is `15px 20px`, compact form padding is `6px 10px`.

---

## 5. UI Component Library Specifications

### 5.1 Top Navigation Bar (`.navbar`)
- **Height:** `48px`
- **Background:** Gradient `linear-gradient(to top, #4d5b76 0%, #6f80a1 100%)`
- **Brand Text / Icon:** White `#fff`, font-size `18px`, bold, icon `margin-right: 8px`
- **Nav Links:** Color `#ffffff`, hover background `#3b475d` or `rgba(255, 255, 255, 0.15)`
- **Divider:** Subtle vertical borders or clear spacing `padding: 0 14px`

### 5.2 Sidebar Navigation (`.sidebar-nav`)
- **Width:** `240px`
- **Background:** `#fafafa`
- **Category Header (`.nav-header`):**
  - Background: Gradient `linear-gradient(to top, #efeff0 0%, #fafafa 100%)`
  - Border: Top `1px solid #fcfcfc`, Bottom `1px solid #c8c8cb`
  - Text: Color `#444444`, font-size `13px`, font-weight `600`, line-height `2.4em`, padding `4px 12px`
  - Expand/Collapse Icon: Right-aligned chevron or caret (`.fa-collapse`)
- **Nav Items (`.nav-list > li > a`):**
  - Color `#222222`, padding `7px 16px`, font-size `13px`
  - Hover: Background `#d2d2dd` with `border-left: 4px solid #8989a6`
  - Active: Background `#e5e5ea`, `border-top: 1px solid #d0d0d6`, `border-bottom: 1px solid #d0d0d6`, `border-left: 4px solid #909096`

### 5.3 Breadcrumb Bar (`.breadcrumb`)
- **Background:** Gradient `linear-gradient(to top, #efeff0 0%, #fafafa 100%)`
- **Border Bottom:** `1px solid #c8c8cb`
- **Padding:** `6px 15px`
- **Font Size:** `12px - 13px`
- **Separator:** `/` or `>` in `#999`

### 5.4 Search & Filter Well (`.search-well` / `.well`)
- **Background:** Pure white `#ffffff` or muted `#fbfbfb`
- **Border:** `1px solid #cccccc`
- **Border Radius:** `3px`
- **Shadow:** `1px 1px 0px #ffffff`
- **Padding:** `12px 16px`
- **Layout:** Flex row with wrap or grid for inline form inputs, dropdowns, and date pickers.

### 5.5 Form Controls & Inputs
- **Height:** `32px` (compact enterprise input)
- **Border:** `1px solid #cccccc`, hover/focus `border-color: #6f80a1; outline: none; box-shadow: 0 0 4px rgba(111, 128, 161, 0.4);`
- **Border Radius:** `3px`
- **Font Size:** `13px`
- **Mandatory Marker:** Red asterisk `<span class="red-star">*</span>` (`color: #ff0000;`)

### 5.6 Data Tables (`.table.table-list` / AG-Grid)
- **Header (`th`):**
  - Background: Gradient `linear-gradient(to top, #e3e3e3 0%, #f9f9f9 100%)`
  - Border: `1px solid #cccccc`
  - Font Size: `12px`, Bold, Color `#333333`
  - Padding: `7px 10px`
  - Text Align: Left (Numbers right-aligned)
- **Rows (`td`):**
  - Padding: `6px 10px`
  - Border: `1px solid #e5e5e5`
  - Font Size: `12px - 13px`
- **Striping:** Alternating rows `#fafafa`
- **Hover:** Row highlight `#eef4fc`

### 5.7 Action Buttons (`.btn`)
- **Primary Button (`.btn-primary`):**
  - Background: `linear-gradient(to bottom, #6f80a1 0%, #4d5b76 100%)`
  - Border: `1px solid #3b475d`
  - Text: `#ffffff`, font-weight `600`
- **Operational Yellow (`.btn-yellow`):**
  - Background: `#caba00`
  - Border: `1px solid #b5a600`
  - Text: `#ffffff`
- **Default / Secondary (`.btn-default`):**
  - Background: `linear-gradient(to bottom, #ffffff 0%, #e6e6e6 100%)`
  - Border: `1px solid #cccccc`
  - Text: `#333333`
- **Sizes:**
  - Standard: `padding: 5px 12px; font-size: 13px; height: 32px;`
  - Small (`.btn-sm`): `padding: 3px 8px; font-size: 12px; height: 26px;`

### 5.8 KPI Stat Widgets (`.stat-widget`)
- **Container:** Flex / Grid of 3-4 cards across the top
- **Card Box:** Border `1px solid #ccc`, background gradient or flat white with soft shadow
- **Title:** `12px`, uppercase, color `#777777`
- **Value:** `24px - 28px`, bold, high-contrast `#222222` or status color
- **Sub-label:** `11px`, muted `#999999`

### 5.9 Alert Banners & Callouts (`.bs-callout`)
- **Danger Callout:** Border-left `4px solid #8e0018`, Background `#fcf2f2`, Text `#8e0018`
- **Warning Callout:** Border-left `4px solid #de8d00`, Background `#fefbed`, Text `#de8d00`
- **Info Callout:** Border-left `4px solid #0077ae`, Background `#f0f7fd`, Text `#0077ae`
- **Success Callout:** Border-left `4px solid #09ae00`, Background `#f0fbf0`, Text `#09ae00`

---

## 6. Ready-to-Use CSS Stylesheet (`lenovo-theme.css`)

Drop this CSS into any project to instantly adopt the Lenovo MDS theme:

```css
/* ==========================================================================
   Lenovo MDS Design System - Global Stylesheet
   ========================================================================== */

/* 1. Global Reset & Body */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  font-size: 13px;
  line-height: 1.42857;
  color: #222222;
  background-color: #f8fafc;
  min-height: 100vh;
}

/* 2. Top Header Navigation */
.navbar-mds {
  position: sticky;
  top: 0;
  z-index: 1000;
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 48px;
  padding: 0 16px;
  background: #4d5b76;
  background: linear-gradient(to top, #4d5b76 0%, #6f80a1 100%);
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.2);
  color: #ffffff;
}

.navbar-mds .brand {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 16px;
  font-weight: 700;
  color: #ffffff;
  text-decoration: none;
}

.navbar-mds .nav-menu {
  display: flex;
  align-items: center;
  gap: 4px;
  list-style: none;
}

.navbar-mds .nav-menu a {
  display: flex;
  align-items: center;
  padding: 6px 12px;
  color: #ffffff;
  font-size: 13px;
  text-decoration: none;
  border-radius: 3px;
  transition: background 0.15s ease;
}

.navbar-mds .nav-menu a:hover,
.navbar-mds .nav-menu a.active {
  background: rgba(255, 255, 255, 0.18);
}

/* 3. App Shell Layout */
.app-container {
  display: flex;
  min-height: calc(100vh - 48px);
}

/* 4. Left Sidebar Navigation */
.sidebar-mds {
  width: 240px;
  flex-shrink: 0;
  background: #fafafa;
  border-right: 1px solid #dcdcdc;
  user-select: none;
}

.sidebar-mds .nav-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 6px 14px;
  background: #efeff0;
  background: linear-gradient(to top, #efeff0 0%, #fafafa 100%);
  border-top: 1px solid #ffffff;
  border-bottom: 1px solid #c8c8cb;
  font-size: 12px;
  font-weight: 700;
  color: #444444;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  cursor: pointer;
}

.sidebar-mds .nav-list {
  list-style: none;
}

.sidebar-mds .nav-list li a {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 8px 16px;
  color: #333333;
  font-size: 13px;
  text-decoration: none;
  border-left: 4px solid transparent;
  transition: all 0.15s ease;
}

.sidebar-mds .nav-list li a:hover {
  background: #e8e8ed;
  border-left-color: #8989a6;
  color: #111111;
}

.sidebar-mds .nav-list li.active a {
  background: #e5e5ea;
  border-left-color: #909096;
  border-top: 1px solid #d0d0d6;
  border-bottom: 1px solid #d0d0d6;
  font-weight: 600;
  color: #000000;
}

/* 5. Main Content Area */
.content-mds {
  flex: 1;
  background: #ffffff;
  min-width: 0;
  display: flex;
  flex-direction: column;
}

/* 6. Breadcrumbs Bar */
.breadcrumb-mds {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 7px 18px;
  background: #efeff0;
  background: linear-gradient(to top, #efeff0 0%, #fafafa 100%);
  border-bottom: 1px solid #c8c8cb;
  font-size: 12px;
  color: #666666;
}

.breadcrumb-mds a {
  color: #4d5b76;
  text-decoration: none;
}

.breadcrumb-mds a:hover {
  text-decoration: underline;
}

.breadcrumb-mds .current {
  font-weight: 600;
  color: #222222;
}

/* 7. Page Content Wrapper */
.page-body {
  padding: 16px 20px;
}

.page-header-row {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 16px;
  padding-bottom: 8px;
  border-bottom: 1px solid #eeeeee;
}

.page-title {
  font-size: 20px;
  font-weight: 600;
  color: #222222;
}

/* 8. Filter / Search Well */
.search-well {
  background: #ffffff;
  border: 1px solid #dcdcdc;
  border-radius: 3px;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.04);
  padding: 12px 16px;
  margin-bottom: 16px;
}

.filter-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 12px;
  align-items: flex-end;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.form-group label {
  font-size: 12px;
  font-weight: 600;
  color: #444444;
}

.form-control {
  height: 32px;
  padding: 4px 8px;
  font-size: 13px;
  border: 1px solid #cccccc;
  border-radius: 3px;
  background: #ffffff;
  color: #222222;
}

.form-control:focus {
  border-color: #6f80a1;
  outline: none;
  box-shadow: 0 0 4px rgba(111, 128, 161, 0.4);
}

/* 9. Buttons */
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  height: 32px;
  padding: 0 14px;
  font-size: 13px;
  font-weight: 600;
  border-radius: 3px;
  cursor: pointer;
  border: 1px solid transparent;
  transition: all 0.15s ease;
  text-decoration: none;
}

.btn-primary {
  background: linear-gradient(to bottom, #6f80a1 0%, #4d5b76 100%);
  border-color: #3b475d;
  color: #ffffff;
}

.btn-primary:hover {
  background: #4d5b76;
}

.btn-default {
  background: linear-gradient(to bottom, #ffffff 0%, #ebebeb 100%);
  border-color: #cccccc;
  color: #333333;
}

.btn-default:hover {
  background: #e0e0e0;
}

.btn-yellow {
  background: #caba00;
  border-color: #b5a600;
  color: #ffffff;
}

.btn-yellow:hover {
  background: #b5a600;
}

/* 10. Stat KPI Cards */
.stats-row {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 12px;
  margin-bottom: 16px;
}

.stat-card {
  background: #ffffff;
  border: 1px solid #dcdcdc;
  border-radius: 3px;
  padding: 12px 14px;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.03);
}

.stat-card .stat-label {
  font-size: 11px;
  font-weight: 600;
  text-transform: uppercase;
  color: #666666;
  margin-bottom: 4px;
}

.stat-card .stat-number {
  font-size: 22px;
  font-weight: 700;
  color: #222222;
}

/* 11. Tables */
.table-container {
  border: 1px solid #dcdcdc;
  border-radius: 3px;
  overflow-x: auto;
  background: #ffffff;
}

.table-mds {
  width: 100%;
  border-collapse: collapse;
  font-size: 12px;
}

.table-mds th {
  background: #efeff0;
  background: linear-gradient(to top, #e3e3e3 0%, #f9f9f9 100%);
  border-bottom: 1px solid #c8c8cb;
  border-right: 1px solid #e0e0e0;
  padding: 8px 10px;
  font-weight: 700;
  color: #333333;
  text-align: left;
  white-space: nowrap;
}

.table-mds td {
  padding: 6px 10px;
  border-bottom: 1px solid #eeeeee;
  border-right: 1px solid #f0f0f0;
  color: #222222;
}

.table-mds tr:nth-child(even) {
  background-color: #fafafa;
}

.table-mds tr:hover {
  background-color: #eef4fc;
}

/* 12. Status Badges */
.badge-status {
  display: inline-block;
  padding: 2px 7px;
  border-radius: 2px;
  font-size: 11px;
  font-weight: 600;
}

.badge-status.success {
  background: #c1e2b3;
  color: #09ae00;
  border: 1px solid #a3d48e;
}

.badge-status.warning {
  background: #f7ecb5;
  color: #de8d00;
  border: 1px solid #f2e187;
}

.badge-status.danger {
  background: #fcf2f2;
  color: #8e0018;
  border: 1px solid #dfb5b4;
}

.badge-status.info {
  background: #d9edf7;
  color: #0077ae;
  border: 1px solid #85c5e5;
}
```

---

## 7. HTML Boilerplate Template

Copy this boilerplate to scaffold any new website using the Lenovo MDS theme:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Operations Portal - Lenovo MDS Theme</title>
  <link rel="stylesheet" href="lenovo-theme.css">
  <!-- Icons (e.g. FontAwesome or Material Symbols) -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>
<body class="theme-blue">

  <!-- Top Navbar -->
  <header class="navbar-mds">
    <a href="#" class="brand">
      <i class="fa fa-paper-plane"></i>
      <span>Lenovo MDS Portal</span>
    </a>
    <ul class="nav-menu">
      <li><a href="#" class="active"><i class="fa fa-chart-line"></i> Dashboard</a></li>
      <li><a href="#"><i class="fa fa-boxes"></i> Inventory</a></li>
      <li><a href="#"><i class="fa fa-wrench"></i> Repairs</a></li>
      <li><a href="#"><i class="fa fa-file-alt"></i> Reports</a></li>
    </ul>
    <div style="font-size: 12px; color: #fff;">
      <i class="fa fa-user-circle"></i> Admin User
    </div>
  </header>

  <!-- Shell Layout -->
  <div class="app-container">
    
    <!-- Left Sidebar -->
    <aside class="sidebar-mds">
      <div class="nav-header">
        <span>Order Management</span>
        <i class="fa fa-chevron-down"></i>
      </div>
      <ul class="nav-list">
        <li><a href="#"><i class="fa fa-inbox"></i> Open Orders</a></li>
        <li class="active"><a href="#"><i class="fa fa-table"></i> Basic Report</a></li>
        <li><a href="#"><i class="fa fa-truck"></i> Shipping Status</a></li>
      </ul>

      <div class="nav-header">
        <span>Analytics & Metrics</span>
        <i class="fa fa-chevron-down"></i>
      </div>
      <ul class="nav-list">
        <li><a href="#"><i class="fa fa-clock"></i> TAT Performance</a></li>
        <li><a href="#"><i class="fa fa-shield-alt"></i> Escalations</a></li>
      </ul>
    </aside>

    <!-- Main Content Panel -->
    <main class="content-mds">
      
      <!-- Breadcrumb Bar -->
      <nav class="breadcrumb-mds">
        <a href="#">Home</a>
        <span>/</span>
        <a href="#">Order Management</a>
        <span>/</span>
        <span class="current">Basic Report</span>
      </nav>

      <!-- Page Content Body -->
      <div class="page-body">
        
        <!-- Header & Action Row -->
        <div class="page-header-row">
          <h1 class="page-title">Service Order Performance Report</h1>
          <div style="display: flex; gap: 8px;">
            <button class="btn btn-default"><i class="fa fa-download"></i> Export Excel</button>
            <button class="btn btn-yellow"><i class="fa fa-sync-alt"></i> Refresh Data</button>
          </div>
        </div>

        <!-- Filter Well -->
        <section class="search-well">
          <form class="filter-grid" onsubmit="event.preventDefault();">
            <div class="form-group">
              <label>Geography</label>
              <select class="form-control">
                <option>INDIA</option>
                <option>APAC</option>
                <option>EMEA</option>
              </select>
            </div>
            <div class="form-group">
              <label>Vendor Partner</label>
              <select class="form-control">
                <option>Reliance Retail Limited-Consign</option>
                <option>All Partners</option>
              </select>
            </div>
            <div class="form-group">
              <label>Date Range</label>
              <input type="date" class="form-control">
            </div>
            <div class="form-group">
              <button class="btn btn-primary" type="submit">
                <i class="fa fa-filter"></i> Apply Filters
              </button>
            </div>
          </form>
        </section>

        <!-- KPI Metric Summary -->
        <section class="stats-row">
          <div class="stat-card">
            <div class="stat-label">Total Open Orders</div>
            <div class="stat-number">1,482</div>
          </div>
          <div class="stat-card">
            <div class="stat-label">Resolved (Within SLA)</div>
            <div class="stat-number" style="color: #09ae00;">94.8%</div>
          </div>
          <div class="stat-card">
            <div class="stat-label">TAT &gt; 3 Days</div>
            <div class="stat-number" style="color: #de8d00;">86</div>
          </div>
          <div class="stat-card">
            <div class="stat-label">Escalations</div>
            <div class="stat-number" style="color: #8e0018;">14</div>
          </div>
        </section>

        <!-- High-Density Data Table -->
        <section class="table-container">
          <table class="table-mds">
            <thead>
              <tr>
                <th>Order ID</th>
                <th>Model / Series</th>
                <th>Partner</th>
                <th>Region</th>
                <th>TAT (Days)</th>
                <th>Status</th>
                <th>Actions</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td><strong>SO-2026-9812</strong></td>
                <td>Motorola Edge 50 Pro</td>
                <td>Reliance Retail</td>
                <td>North (IN)</td>
                <td>1.4</td>
                <td><span class="badge-status success">Completed</span></td>
                <td><a href="#" style="color: #4d5b76;">Details</a></td>
              </tr>
              <tr>
                <td><strong>SO-2026-9815</strong></td>
                <td>Moto G84 5G</td>
                <td>Reliance Retail</td>
                <td>West (IN)</td>
                <td>4.2</td>
                <td><span class="badge-status danger">TAT Breached</span></td>
                <td><a href="#" style="color: #4d5b76;">Details</a></td>
              </tr>
              <tr>
                <td><strong>SO-2026-9820</strong></td>
                <td>ThinkPhone by Lenovo</td>
                <td>Reliance Retail</td>
                <td>South (IN)</td>
                <td>2.8</td>
                <td><span class="badge-status warning">Pending Parts</span></td>
                <td><a href="#" style="color: #4d5b76;">Details</a></td>
              </tr>
            </tbody>
          </table>
        </section>

      </div>
    </main>
  </div>

</body>
</html>
```

---

## 8. Guidelines for Designing New Websites with This Theme

1. **Maintain Density**: Avoid oversized mobile padding on desktop views. Keep cell padding around `6px - 8px` and font sizes around `12px - 13px`.
2. **Preserve Navigation Hierarchy**: The combination of the top dark gradient navbar (`#4d5b76` to `#6f80a1`) and the left light gray sidebar (`#fafafa`) is the core signature of Lenovo MDS.
3. **Use Subtle Metallic Gradients**: For secondary headers, breadcrumbs, and table column titles, use the subtle gradient (`#efeff0` to `#fafafa` or `#e3e3e3` to `#f9f9f9`) with a 1px border.
4. **Action Hierarchy**:
   - Primary submissions & filters: Blue gradient `.btn-primary`
   - Refresh / Utility actions: Solid mustard yellow `.btn-yellow` (`#caba00`)
   - Neutral table row actions / Secondary links: `.btn-default` or plain `#4d5b76` anchor links.
5. **Multi-tenancy / Theming**: If you need to brand different sub-systems or environments (e.g. Staging vs Production, or Motorola vs Lenovo Think), toggle the root body class between `.theme-blue`, `.theme-dark`, `.theme-navy`, or `.theme-steel`.
