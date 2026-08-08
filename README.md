<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.5, user-scalable=yes">
  <title>Liquid Store · iOS 27 Glass</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
  <style>
    /* ============================================================
       CSS VARIABLES · THEME SYSTEM
       ============================================================ */
    :root {
      /* ----- DARK THEME (vibrant 3D) ----- */
      --bg-primary: radial-gradient(circle at 20% 30%, #0d0a1a, #05030a);
      --bg-card: linear-gradient(145deg, rgba(60, 30, 120, 0.25), rgba(20, 10, 60, 0.15));
      --bg-glass: rgba(255, 255, 255, 0.03);
      --bg-glass-dark: rgba(15, 10, 35, 0.50);
      --bg-input: rgba(30, 15, 70, 0.25);
      --bg-user-item: rgba(60, 30, 
120, 0.15);
      --border-glass: rgba(180, 130, 255, 0.12);
      --border-glass-light: rgba(180, 130, 255, 0.06);
      --text-primary: #f0ecff;
      --text-secondary: rgba(220, 210, 255, 0.85);
      --text-muted: rgba(180, 160, 255, 0.45);
      --text-dim: rgba(180, 160, 255, 0.15);
      --shadow-glass: 0 30px 70px -20px #2a1a5a, 0 0 0 1px rgba(180, 130, 255, 0.05) inset, 0 0 40px -10px rgba(120, 80, 255, 0.05);
      --shadow-card: 0 20px 50px -18px #2a1a5a, 0 0 0 1px rgba(180, 130, 255, 0.04) inset;
      --shadow-login: 0 50px 100px -30px #1a0a3a, 0 0 80px -20px rgba(120, 80, 255, 0.08), 0 0 120px -30px rgba(200, 100, 255, 0.05);
      --btn-primary-bg: linear-gradient(135deg, rgba(160, 100, 255, 0.25), rgba(255, 80, 200, 0.15));
      --btn-primary-border: rgba(180, 130, 255, 0.15);
      --btn-primary-shadow: 0 0 50px -10px rgba(160, 100, 255, 0.15), 0 0 80px -20px rgba(200, 80, 255, 0.05);
      --btn-primary-hover: linear-gradient(135deg, rgba(160, 100, 255, 0.40), rgba(255, 80, 200, 0.25));
      --btn-secondary-bg: rgba(255, 255, 255, 0.02);
      --btn-secondary-border: rgba(180, 130, 255, 0.06);
      --gradient-brand: linear-gradient(135deg, #b8a0ff, #8a6aff, #ff6bcb, #ff8a6b);
      --gradient-login: linear-gradient(135deg, #c8b0ff, #8a6aff, #ff6bcb, #ff9a7a);
      --orb-1: rgba(160, 100, 255, 0.15);
      --orb-2: rgba(255, 80, 200, 0.10);
      --login-overlay: conic-gradient(from 0deg, transparent, rgba(160, 100, 255, 0.04), transparent, rgba(255, 80, 200, 0.04), transparent);
      --glow-color: rgba(160, 100, 255, 0.15);
      --icon-gradient: linear-gradient(135deg, #b8a0ff, #8a6aff, #ff6bcb);
    }

    /* ----- LIGHT THEME ----- */
    [data-theme="light"] {
      --bg-primary: radial-gradient(circle at 0% 30%, #f0eef8, #e8e4f0);
      --bg-card: linear-gradient(135deg, rgba(255, 255, 255, 0.40), rgba(220, 210, 255, 0.25));
      --bg-glass: rgba(255, 255, 255, 0.15);
      --bg-glass-dark: rgba(255, 255, 255, 0.25);
      --bg-input: rgba(255, 255, 255, 0.35);
      --bg-user-item: rgba(255, 255, 255, 0.15);
      --border-glass: rgba(255, 255, 255, 0.25);
      --border-glass-light: rgba(255, 255, 255, 0.15);
      --text-primary: #1a1a2e;
      --text-secondary: rgba(26, 26, 46, 0.75);
      --text-muted: rgba(26, 26, 46, 0.35);
      --text-dim: rgba(26, 26, 46, 0.10);
      --shadow-glass: 0 30px 70px -20px rgba(0, 0, 0, 0.08), 0 0 0 1px rgba(255, 255, 255, 0.4) inset;
      --shadow-card: 0 18px 40px -18px rgba(0, 0, 0, 0.06), 0 0 0 1px rgba(255, 255, 255, 0.3) inset;
      --shadow-login: 0 50px 100px -30px rgba(0, 0, 0, 0.08), 0 0 80px -30px rgba(138, 106, 255, 0.08), 0 0 120px -40px rgba(255, 80, 180, 0.05);
      --btn-primary-bg: linear-gradient(135deg, rgba(138, 106, 255, 0.20), rgba(255, 80, 180, 0.12));
      --btn-primary-border: rgba(138, 106, 255, 0.15);
      --btn-primary-shadow: 0 0 40px -12px rgba(138, 106, 255, 0.10);
      --btn-primary-hover: linear-gradient(135deg, rgba(138, 106, 255, 0.35), rgba(255, 80, 180, 0.20));
      --btn-secondary-bg: rgba(255, 255, 255, 0.15);
      --btn-secondary-border: rgba(255, 255, 255, 0.20);
      --gradient-brand: linear-gradient(135deg, #5a3d9a, #8a6aff, #d45a9a);
      --gradient-login: linear-gradient(135deg, #5a3d9a, #8a6aff, #d45a9a, #e88a5a);
      --orb-1: rgba(138, 106, 255, 0.08);
      --orb-2: rgba(255, 80, 180, 0.06);
      --login-overlay: conic-gradient(from 0deg, transparent, rgba(138, 106, 255, 0.04), transparent, rgba(255, 80, 180, 0.04), transparent);
      --glow-color: rgba(138, 106, 255, 0.08);
      --icon-gradient: linear-gradient(135deg, #5a3d9a, #8a6aff, #d45a9a);
    }

    /* ============================================================
       BASE STYLES
       ============================================================ */
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', sans-serif;
    }

    body {
      min-height: 100vh;
      background: var(--bg-primary);
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 16px;
      position: relative;
      overflow-x: hidden;
      transition: background 0.6s ease;
    }

    body::before {
      content: '';
      position: fixed;
      top: -20%;
      left: -10%;
      width: 60%;
      height: 60%;
      background: radial-gradient(circle, var(--orb-1) 0%, transparent 70%);
      filter: blur(100px);
      z-index: 0;
      animation: orbFloat 20s ease-in-out infinite alternate;
      transition: background 0.6s ease;
    }
    body::after {
      content: '';
      position: fixed;
      bottom: -20%;
      right: -10%;
      width: 60%;
      height: 60%;
      background: radial-gradient(circle, var(--orb-2) 0%, transparent 70%);
      filter: blur(100px);
      z-index: 0;
      animation: orbFloat 25s ease-in-out infinite alternate-reverse;
      transition: background 0.6s ease;
    }
    @keyframes orbFloat {
      0% { transform: translate(0, 0) scale(1); }
      100% { transform: translate(50px, 40px) scale(1.3); }
    }

    .app-container {
      width: 100%;
      max-width: 1400px;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      gap: 24px;
      position: relative;
      z-index: 1;
    }

    /* ---------- GLASS 3D ---------- */
    .glass {
      background: var(--bg-glass);
      backdrop-filter: blur(40px) saturate(250%);
      -webkit-backdrop-filter: blur(40px) saturate(250%);
      border-radius: 48px;
      border: 1px solid var(--border-glass);
      box-shadow: var(--shadow-glass);
      transition: all 0.4s cubic-bezier(0.2, 0.9, 0.4, 1), background 0.4s ease;
      color: var(--text-primary);
    }

    .glass-dark {
      background: var(--bg-glass-dark);
      backdrop-filter: blur(44px) saturate(250%);
      -webkit-backdrop-filter: blur(44px) saturate(250%);
      border: 1px solid var(--border-glass);
      box-shadow: var(--shadow-glass);
      transition: all 0.4s cubic-bezier(0.2, 0.9, 0.4, 1), background 0.4s ease;
    }

    .glass-card {
      background: var(--bg-card);
      backdrop-filter: blur(32px) saturate(250%);
      -webkit-backdrop-filter: blur(32px) saturate(250%);
      border-radius: 40px;
      border: 1px solid var(--border-glass-light);
      box-shadow: var(--shadow-card);
      transition: all 0.5s cubic-bezier(0.2, 0.9, 0.4, 1), background 0.4s ease;
      color: var(--text-primary);
    }

    .glass-card:hover {
      transform: translateY(-10px) scale(1.03);
      border-color: rgba(180, 130, 255, 0.15);
      box-shadow: 0 30px 80px -15px rgba(100, 60, 200, 0.25), 0 0 60px -15px rgba(160, 100, 255, 0.08);
    }

    /* ---------- PAGES ---------- */
    .page { display: none; flex-direction: column; gap: 24px; }
    .page.active { display: flex; }

    /* ---------- BUTTONS ---------- */
    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      padding: 14px 28px;
      border-radius: 60px;
      font-size: 0.95rem;
      font-weight: 500;
      letter-spacing: 0.02em;
      border: 1px solid var(--border-glass);
      background: var(--btn-secondary-bg);
      color: var(--text-primary);
      backdrop-filter: blur(12px);
      box-shadow: 0 8px 24px -8px rgba(0, 0, 0, 0.3);
      transition: all 0.3s cubic-bezier(0.2, 0.9, 0.4, 1);
      cursor: pointer;
      position: relative;
      min-height: 52px;
      text-decoration: none;
      user-select: none;
    }

    .btn:active { transform: scale(0.97); }

    .btn-primary {
      background: var(--btn-primary-bg);
      border-color: var(--btn-primary-border);
      box-shadow: var(--btn-primary-shadow);
    }
    .btn-primary:hover {
      background: var(--btn-primary-hover);
      border-color: rgba(180, 130, 255, 0.25);
      box-shadow: 0 0 70px -10px rgba(160, 100, 255, 0.20), 0 0 100px -20px rgba(200, 80, 255, 0.05);
      transform: translateY(-2px);
    }

    .btn-secondary {
      background: var(--btn-secondary-bg);
      border-color: var(--btn-secondary-border);
    }
    .btn-secondary:hover {
      background: rgba(255, 255, 255, 0.05);
      border-color: rgba(180, 130, 255, 0.10);
      transform: translateY(-2px);
    }

    .btn-danger {
      background: rgba(255, 70, 100, 0.06);
      border-color: rgba(255, 70, 100, 0.06);
    }
    .btn-danger:hover {
      background: rgba(255, 70, 100, 0.16);
      border-color: rgba(255, 70, 100, 0.12);
      box-shadow: 0 0 40px -10px rgba(255, 70, 100, 0.15);
      transform: translateY(-2px);
    }

    .btn-sm {
      padding: 8px 18px;
      min-height: 38px;
      font-size: 0.75rem;
      gap: 6px;
    }
    .btn-xs {
      padding: 4px 14px;
      min-height: 30px;
      font-size: 0.65rem;
      gap: 4px;
      border-radius: 40px;
    }
    .w-full { width: 100%; }

    /* Theme toggle */
    .theme-toggle {
      background: var(--bg-glass);
      border: 1px solid var(--border-glass);
      border-radius: 60px;
      padding: 6px 6px 6px 16px;
      display: flex;
      align-items: center;
      gap: 8px;
      cursor: pointer;
      transition: all 0.3s ease;
      color: var(--text-primary);
      font-size: 0.8rem;
      min-height: 42px;
    }
    .theme-toggle:hover {
      border-color: rgba(180, 130, 255, 0.15);
      box-shadow: 0 0 30px -8px rgba(160, 100, 255, 0.05);
    }
    .theme-toggle .toggle-track {
      width: 44px;
      height: 24px;
      border-radius: 40px;
      background: rgba(255, 255, 255, 0.06);
      border: 1px solid var(--border-glass-light);
      position: relative;
      transition: all 0.4s ease;
      flex-shrink: 0;
    }
    .theme-toggle .toggle-track .toggle-thumb {
      width: 18px;
      height: 18px;
      border-radius: 50%;
      background: linear-gradient(135deg, #8a6aff, #ff6bcb);
      position: absolute;
      top: 2px;
      left: 2px;
      transition: all 0.4s cubic-bezier(0.2, 0.9, 0.4, 1);
      box-shadow: 0 0 20px -4px rgba(138, 106, 255, 0.3);
    }
    [data-theme="light"] .theme-toggle .toggle-track .toggle-thumb {
      left: 22px;
      background: linear-gradient(135deg, #ffb37a, #ff6bcb);
    }
    .theme-toggle .toggle-label {
      font-size: 0.7rem;
      text-transform: uppercase;
      letter-spacing: 0.04em;
      color: var(--text-muted);
      min-width: 28px;
    }

    /* ---------- LOGIN ---------- */
    .login-wrapper {
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 80vh;
    }

    .login-card {
      width: 100%;
      max-width: 420px;
      padding: 50px 36px 44px;
      text-align: center;
      background: var(--bg-glass-dark);
      backdrop-filter: blur(56px);
      border: 1px solid var(--border-glass);
      border-radius: 64px;
      box-shadow: var(--shadow-login);
      position: relative;
      overflow: hidden;
      transition: background 0.4s ease, box-shadow 0.4s ease;
    }
    .login-card::before {
      content: '';
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: var(--login-overlay);
      animation: rotateGlow 30s linear infinite;
      pointer-events: none;
    }
    @keyframes rotateGlow {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
    }

    .login-card h1 {
      font-weight: 400;
      font-size: 2.8rem;
      background: var(--gradient-login);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      letter-spacing: -0.5px;
      text-shadow: 0 0 80px rgba(160, 100, 255, 0.15);
      position: relative;
      z-index: 1;
    }
    .login-card .sub {
      color: var(--text-muted);
      margin: 8px 0 32px;
      font-weight: 300;
      letter-spacing: 0.5px;
      position: relative;
      z-index: 1;
    }
    .login-card .login-switch {
      margin-top: 12px;
      position: relative;
      z-index: 1;
    }
    .login-card .login-switch .btn {
      font-size: 0.8rem;
      padding: 8px 20px;
      min-height: 38px;
    }

    .input-group {
      background: var(--bg-input);
      border-radius: 60px;
      padding: 4px 20px;
      margin-bottom: 18px;
      display: flex;
      align-items: center;
      border: 1px solid var(--border-glass-light);
      backdrop-filter: blur(6px);
      transition: 0.3s;
      position: relative;
      z-index: 1;
    }
    .input-group:focus-within {
      border-color: rgba(180, 130, 255, 0.20);
      box-shadow: 0 0 50px -10px rgba(160, 100, 255, 0.06);
    }
    .input-group i {
      color: var(--text-muted);
      width: 24px;
      font-size: 1rem;
    }
    .input-group input {
      background: transparent;
      border: none;
      padding: 16px 10px;
      width: 100%;
      color: var(--text-primary);
      font-size: 1rem;
      outline: none;
    }
    .input-group input::placeholder { color: var(--text-dim); }

    /* ---------- HEADER ---------- */
    .shop-header {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
      justify-content: space-between;
      padding: 12px 24px;
      gap: 14px;
      border-radius: 60px;
      background: var(--bg-glass-dark);
      backdrop-filter: blur(36px);
      border: 1px solid var(--border-glass);
      min-height: 76px;
      transition: background 0.4s ease;
    }

    .shop-header .brand {
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .shop-header .brand h2 {
      font-weight: 400;
      font-size: 1.5rem;
      background: var(--gradient-brand);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      text-shadow: 0 0 60px rgba(160, 100, 255, 0.08);
      white-space: nowrap;
    }
    .shop-header .brand i {
      font-size: 1.6rem;
      color: rgba(160, 100, 255, 0.4);
    }

    .header-actions {
      display: flex;
      align-items: center;
      gap: 10px;
      flex-wrap: wrap;
    }

    .search-box {
      background: var(--bg-input);
      border-radius: 60px;
      padding: 2px 14px 2px 18px;
      display: flex;
      align-items: center;
      width: 220px;
      border: 1px solid var(--border-glass-light);
      transition: 0.3s;
      min-height: 40px;
    }
    .search-box:focus-within {
      border-color: rgba(180, 130, 255, 0.15);
      box-shadow: 0 0 40px -8px rgba(160, 100, 255, 0.04);
      width: 260px;
    }
    .search-box i {
      color: var(--text-dim);
      font-size: 0.85rem;
      margin-right: 6px;
    }
    .search-box input {
      background: transparent;
      border: none;
      padding: 10px 6px;
      color: var(--text-primary);
      width: 100%;
      outline: none;
      font-size: 0.85rem;
    }
    .search-box input::placeholder {
      color: var(--text-dim);
      font-weight: 300;
    }

    .action-btn-group {
      display: flex;
      gap: 6px;
      align-items: center;
    }

    /* ---------- PRODUCT GRID ---------- */
    .product-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
      gap: 28px 20px;
      padding: 8px 0 30px;
    }

    .product-card {
      padding: 18px 14px 22px;
      text-align: center;
      cursor: pointer;
      animation: floatUp 0.6s ease backwards;
    }
    
    /* Product image/icon container */
    .product-media {
      width: 100%;
      aspect-ratio: 1/1;
      border-radius: 32px;
      display: flex;
      align-items: center;
      justify-content: center;
      background: var(--bg-card);
      border: 1px solid var(--border-glass-light);
      box-shadow: var(--shadow-card);
      transition: 0.4s;
      overflow: hidden;
      position: relative;
    }
    .product-media img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .product-media .product-icon {
      font-size: 4rem;
      background: var(--icon-gradient);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      text-shadow: 0 0 40px rgba(160, 100, 255, 0.1);
    }
    .product-card:hover .product-media {
      transform: scale(1.04);
      border-color: rgba(180, 130, 255, 0.10);
      box-shadow: 0 16px 50px -10px rgba(160, 100, 255, 0.08);
    }
    .product-card h3 {
      margin-top: 14px;
      font-weight: 400;
      font-size: 0.95rem;
      color: var(--text-secondary);
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
    }
    .product-card p {
      font-size: 0.7rem;
      color: var(--text-muted);
      margin-top: 4px;
      display: -webkit-box;
      -webkit-line-clamp: 2;
      -webkit-box-orient: vertical;
      overflow: hidden;
      line-height: 1.4;
    }

    /* ---------- DETAIL ---------- */
    .detail-container {
      display: flex;
      flex-wrap: wrap;
      gap: 30px;
      padding: 30px;
      background: var(--bg-glass-dark);
      backdrop-filter: blur(40px);
      border-radius: 60px;
      border: 1px solid var(--border-glass);
      transition: background 0.4s ease;
    }
    .detail-media {
      flex: 1 1 280px;
      display: flex;
      flex-direction: column;
      gap: 12px;
    }
    .detail-media .detail-main {
      width: 100%;
      aspect-ratio: 1/1;
      border-radius: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      background: var(--bg-card);
      border: 1px solid var(--border-glass-light);
      overflow: hidden;
      position: relative;
    }
    .detail-media .detail-main img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .detail-media .detail-main video {
      width: 100%;
      height: 100%;
      object-fit: contain;
      background: #0a0815;
    }
    .detail-media .detail-main .detail-icon {
      font-size: 8rem;
      background: var(--icon-gradient);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    .detail-thumbs {
      display: flex;
      gap: 10px;
      flex-wrap: wrap;
    }
    .detail-thumbs .thumb-item {
      width: 70px;
      height: 70px;
      border-radius: 20px;
      display: flex;
      align-items: center;
      justify-content: center;
      background: var(--bg-card);
      border: 1px solid var(--border-glass-light);
      cursor: pointer;
      transition: 0.3s;
      overflow: hidden;
      flex-shrink: 0;
    }
    .detail-thumbs .thumb-item img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .detail-thumbs .thumb-item video {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .detail-thumbs .thumb-item .thumb-icon {
      font-size: 2rem;
      background: var(--icon-gradient);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    .detail-thumbs .thumb-item:hover {
      transform: scale(0.95);
      border-color: rgba(180, 130, 255, 0.10);
    }
    .detail-info {
      flex: 2 1 300px;
      display: flex;
      flex-direction: column;
      gap: 12px;
    }
    .detail-info h2 {
      font-weight: 400;
      font-size: 2.2rem;
      background: var(--gradient-brand);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    .detail-info p {
      color: var(--text-muted);
      line-height: 1.7;
      font-weight: 300;
    }

    /* ---------- ADMIN ---------- */
    .admin-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 20px;
    }
    .admin-card {
      padding: 24px 20px;
      border-radius: 44px;
      background: var(--bg-glass-dark);
      backdrop-filter: blur(20px);
      border: 1px solid var(--border-glass);
      transition: background 0.4s ease;
    }
    .admin-card h4 {
      font-weight: 300;
      color: var(--text-muted);
      margin-bottom: 16px;
      font-size: 0.8rem;
      letter-spacing: 0.06em;
      text-transform: uppercase;
    }
    .admin-card input,
    .admin-card textarea {
      width: 100%;
      background: var(--bg-input);
      border: 1px solid var(--border-glass-light);
      border-radius: 40px;
      padding: 12px 16px;
      color: var(--text-primary);
      font-size: 0.9rem;
      margin-bottom: 12px;
      outline: none;
      backdrop-filter: blur(4px);
      transition: 0.3s;
    }
    .admin-card input:focus,
    .admin-card textarea:focus {
      border-color: rgba(180, 130, 255, 0.10);
      box-shadow: 0 0 50px -10px rgba(160, 100, 255, 0.03);
    }
    .admin-card textarea {
      border-radius: 24px;
      min-height: 60px;
      resize: vertical;
    }
    .admin-card .btn {
      width: 100%;
      justify-content: center;
    }

    .file-upload-area {
      display: flex;
      flex-direction: column;
      gap: 8px;
      margin-bottom: 12px;
    }
    .file-upload-area .upload-btn {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      padding: 12px;
      border-radius: 40px;
      background: var(--bg-input);
      border: 1px dashed var(--border-glass-light);
      cursor: pointer;
      transition: 0.3s;
      color: var(--text-muted);
      font-size: 0.85rem;
      min-height: 48px;
    }
    .file-upload-area .upload-btn:hover {
      border-color: rgba(180, 130, 255, 0.15);
    }
    .file-upload-area input[type="file"] {
      display: none;
    }
    .file-preview-grid {
      display: flex;
      gap: 8px;
      flex-wrap: wrap;
      margin-top: 6px;
    }
    .file-preview-grid .preview-item {
      width: 60px;
      height: 60px;
      border-radius: 16px;
      overflow: hidden;
      border: 1px solid var(--border-glass-light);
      background: #0a0815;
      position: relative;
    }
    .file-preview-grid .preview-item img,
    .file-preview-grid .preview-item video {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .file-preview-grid .preview-item .remove-file {
      position: absolute;
      top: -6px;
      right: -6px;
      width: 20px;
      height: 20px;
      border-radius: 50%;
      background: rgba(255, 70, 70, 0.8);
      border: none;
      color: white;
      font-size: 10px;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .user-list {
      display: flex;
      flex-direction: column;
      gap: 6px;
      margin-top: 10px;
    }
    .user-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      background: var(--bg-user-item);
      border-radius: 40px;
      padding: 6px 14px 6px 20px;
      border: 1px solid var(--border-glass-light);
      transition: background 0.4s ease;
    }
    .user-item span {
      font-size: 0.85rem;
      color: var(--text-secondary);
    }
    .user-item .btn {
      min-height: 30px;
      padding: 2px 14px;
      font-size: 0.65rem;
      width: auto;
    }

    /* ---------- UTILITIES ---------- */
    .flex-between {
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 12px;
    }
    .gap-8 { gap: 8px; }
    .mt-8 { margin-top: 8px; }
    .hidden { display: none !important; }
    .text-muted { color: var(--text-muted); }

    @keyframes floatUp {
      0% { opacity: 0; transform: translateY(28px) scale(0.96); }
      100% { opacity: 1; transform: translateY(0) scale(1); }
    }

    /* ---------- RESPONSIVE ---------- */
    @media (max-width: 850px) {
      .shop-header {
        flex-direction: column;
        align-items: stretch;
        padding: 16px 18px;
      }
      .shop-header .brand { justify-content: center; }
      .header-actions {
        flex-direction: column;
        align-items: stretch;
        gap: 10px;
      }
      .search-box {
        width: 100%;
        min-width: unset;
      }
      .search-box:focus-within {
        width: 100%;
      }
      .action-btn-group {
        justify-content: center;
        flex-wrap: wrap;
      }
      .login-card { padding: 32px 20px; }
      .product-grid {
        grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
        gap: 16px;
      }
      .detail-container { padding: 16px; }
      .admin-grid { grid-template-columns: 1fr; }
    }

    @media (max-width: 400px) {
      .btn { padding: 12px 18px; font-size: 0.85rem; min-height: 44px; }
      .btn-sm { padding: 6px 14px; min-height: 32px; font-size: 0.7rem; }
      .theme-toggle { font-size: 0.7rem; padding: 4px 4px 4px 12px; }
      .theme-toggle .toggle-track { width: 36px; height: 20px; }
      .theme-toggle .toggle-track .toggle-thumb { width: 14px; height: 14px; top: 2px; left: 2px; }
      [data-theme="light"] .theme-toggle .toggle-track .toggle-thumb { left: 18px; }
      .search-box { padding: 2px 10px 2px 14px; min-height: 36px; width: 100%; }
      .search-box input { font-size: 0.8rem; padding: 8px 4px; }
      .search-box:focus-within { width: 100%; }
    }
  </style>
</head>
<body>
<div class="app-container" id="app">

  <!-- ========== USER LOGIN PAGE ========== -->
  <div id="loginPage" class="page active">
    <div class="login-wrapper">
      <div class="login-card">
        <h1>✦ Liquid</h1>
        <div class="sub">User Sign in</div>
        <div class="input-group"><i class="fas fa-user"></i><input type="text" id="userLoginUser" placeholder="Username" value=""></div>
        <div class="input-group"><i class="fas fa-lock"></i><input type="password" id="userLoginPass" placeholder="Password" value=""></div>
        <button class="btn btn-primary w-full" id="userLoginBtn"><i class="fas fa-arrow-right"></i> Login</button>
        <div style="margin-top:12px; color: var(--text-dim); font-size:0.7rem;">demo: user / password</div>
        <div class="login-switch">
          <button class="btn btn-secondary btn-sm" id="goToAdminLoginBtn"><i class="fas fa-user-shield"></i> Admin Login</button>
        </div>
      </div>
    </div>
  </div>

  <!-- ========== ADMIN LOGIN PAGE ========== -->
  <div id="adminLoginPage" class="page">
    <div class="login-wrapper">
      <div class="login-card">
        <h1>⚡ Admin</h1>
        <div class="sub">Admin Panel Login</div>
        <div class="input-group"><i class="fas fa-user"></i><input type="text" id="adminLoginUser" placeholder="Username" value=""></div>
        <div class="input-group"><i class="fas fa-lock"></i><input type="password" id="adminLoginPass" placeholder="Password" value=""></div>
        <button class="btn btn-primary w-full" id="adminLoginBtn"><i class="fas fa-arrow-right"></i> Admin Login</button>
        <div style="margin-top:12px; color: var(--text-dim); font-size:0.7rem;">default: user / password</div>
        <div class="login-switch">
          <button class="btn btn-secondary btn-sm" id="backToUserLoginBtn"><i class="fas fa-user"></i> User Login</button>
        </div>
      </div>
    </div>
  </div>

  <!-- ========== MAIN SHOP ========== -->
  <div id="mainPage" class="page">
    <div class="shop-header glass">
      <div class="brand">
        <i class="fas fa-store-alt"></i>
        <h2>Store</h2>
      </div>
      <div class="header-actions">
        <div class="search-box">
          <i class="fas fa-search"></i>
          <input type="text" id="searchInput" placeholder="Search...">
        </div>
        <div class="action-btn-group">
          <div class="theme-toggle" id="themeToggle" title="Toggle theme">
            <span class="toggle-label" id="themeLabel">Dark</span>
            <div class="toggle-track">
              <div class="toggle-thumb"></div>
            </div>
          </div>
          <button class="btn btn-sm btn-secondary" id="userLogoutBtn"><i class="fas fa-sign-out-alt"></i></button>
        </div>
      </div>
    </div>
    <div class="product-grid" id="productGrid"></div>
  </div>

  <!-- ========== DETAIL ========== -->
  <div id="detailPage" class="page">
    <button class="btn btn-sm btn-secondary" id="backFromDetail" style="width:fit-content;"><i class="fas fa-arrow-left"></i> Back</button>
    <div class="detail-container glass">
      <div class="detail-media">
        <div class="detail-main" id="detailMainMedia"></div>
        <div class="detail-thumbs" id="detailThumbs"></div>
      </div>
      <div class="detail-info">
        <h2 id="detailTitle"></h2>
        <p id="detailDesc"></p>
        <p id="detailSpec" style="color:var(--text-dim); font-size:0.85rem;"></p>
      </div>
    </div>
  </div>

  <!-- ========== ADMIN DASHBOARD ========== -->
  <div id="adminPage" class="page">
    <div class="shop-header glass">
      <div class="brand">
        <i class="fas fa-user-cog"></i>
        <h2>Admin Dashboard</h2>
      </div>
      <div class="action-btn-group">
        <div class="theme-toggle" id="themeToggleAdmin" title="Toggle theme">
          <span class="toggle-label" id="themeLabelAdmin">Dark</span>
          <div class="toggle-track">
            <div class="toggle-thumb"></div>
          </div>
        </div>
        <button class="btn btn-sm btn-secondary" id="adminLogoutBtn"><i class="fas fa-sign-out-alt"></i> Logout</button>
      </div>
    </div>

    <div class="admin-grid">
      <!-- Add product -->
      <div class="admin-card glass-dark">
        <h4>➕ Add Product</h4>
        <input type="text" id="newProductName" placeholder="Product name">
        <input type="text" id="newProductCat" placeholder="Category (e.g. audio)">

        <div class="file-upload-area">
          <label class="upload-btn" for="productFiles">
            <i class="fas fa-cloud-upload-alt"></i> Upload Image or Video
          </label>
          <input type="file" id="productFiles" accept="image/*,video/*" multiple>
          <div class="file-preview-grid" id="filePreviewGrid"></div>
        </div>

        <input type="text" id="newProductImgUrl" placeholder="or image URL">
        <input type="text" id="newProductVideoUrl" placeholder="or video URL">
        <textarea id="newProductDesc" placeholder="Description"></textarea>
        <button class="btn btn-primary" id="addProductBtn">Add Product</button>
      </div>

      <!-- Delete -->
      <div class="admin-card glass-dark">
        <h4>🗑️ Delete Product</h4>
        <input type="number" id="deleteProductId" placeholder="Product ID">
        <button class="btn btn-danger" id="deleteProductBtn">Delete</button>
        <div style="margin-top:10px; color:var(--text-dim); font-size:0.65rem;">ID shown on cards</div>
      </div>

      <!-- Edit -->
      <div class="admin-card glass-dark">
        <h4>✏️ Edit Product</h4>
        <input type="number" id="editProductId" placeholder="Product ID">
        <input type="text" id="editProductName" placeholder="New name">
        <input type="text" id="editProductImg" placeholder="New image URL">
        <input type="text" id="editProductVideo" placeholder="New video URL">
        <textarea id="editProductDesc" placeholder="New description"></textarea>
        <button class="btn btn-secondary" id="editProductBtn">Update</button>
      </div>

      <!-- Add User -->
      <div class="admin-card glass-dark">
        <h4>👤 Add User</h4>
        <input type="text" id="newUsername" placeholder="Username">
        <input type="text" id="newUserPass" placeholder="Password">
        <button class="btn btn-primary" id="addUserBtn">Add User</button>
      </div>

      <!-- Manage Users -->
      <div class="admin-card glass-dark">
        <h4>👥 Manage Users</h4>
        <div class="user-list" id="userList"></div>
        <div style="margin-top:12px; border-top:1px solid var(--border-glass-light); padding-top:12px;">
          <input type="text" id="changePassUsername" placeholder="Username to change pass">
          <input type="text" id="changePassNew" placeholder="New password">
          <button class="btn btn-secondary btn-sm w-full" id="changeUserPassBtn">Change Password</button>
        </div>
      </div>
    </div>
  </div>
</div>

<script>
  (function() {
    // ---------- DATA ----------
    let products = [];
    let users = [];
    let uploadedFiles = [];

    // Default products with icons
    const DEFAULT_PRODUCTS = [
      { id: 1, name: 'Wireless Headphones', category: 'audio', icon: 'fa-headphones', img: '', video: '', desc: 'Premium sound with active noise cancellation. 30h battery, ergonomic design.' },
      { id: 2, name: 'Leather Messenger Bag', category: 'bags', icon: 'fa-bag-shopping', img: '', video: '', desc: 'Handcrafted genuine leather, 3 compartments, fits 14" laptop.' },
      { id: 3, name: 'Smart Watch Pro', category: 'wearables', icon: 'fa-clock', img: '', video: '', desc: 'AMOLED display, heart rate, GPS, 7-day battery, water resistant.' },
      { id: 4, name: 'Portable Speaker', category: 'audio', icon: 'fa-music', img: '', video: '', desc: 'Bluetooth 5.2, 30W, RGB lighting, IPX7, perfect for outdoors.' },
    ];

    const DEFAULT_USERS = [
      { username: 'admin123', password: 'password' },
      { username: 'user01', password: '123456' },
      { username: 'manager01', password: 'manager' },
    ];

    function loadData() {
      const storedProducts = localStorage.getItem('liquid_products');
      const storedUsers = localStorage.getItem('liquid_users');
      if (storedProducts) {
        try { products = JSON.parse(storedProducts); } catch(e) { products = []; }
      } else {
        products = JSON.parse(JSON.stringify(DEFAULT_PRODUCTS));
        saveProducts();
      }
      if (storedUsers) {
        try { users = JSON.parse(storedUsers); } catch(e) { users = []; }
      } else {
        users = JSON.parse(JSON.stringify(DEFAULT_USERS));
        saveUsers();
      }
    }

    function saveProducts() { localStorage.setItem('liquid_products', JSON.stringify(products)); }
    function saveUsers() { localStorage.setItem('liquid_users', JSON.stringify(users)); }

    // ---------- THEME ----------
    function getTheme() {
      return localStorage.getItem('liquid_theme') || 'dark';
    }

    function setTheme(theme) {
      document.documentElement.setAttribute('data-theme', theme);
      localStorage.setItem('liquid_theme', theme);
      const labels = document.querySelectorAll('.toggle-label');
      labels.forEach(el => el.textContent = theme === 'dark' ? 'Dark' : 'Light');
    }

    function toggleTheme() {
      const current = getTheme();
      const next = current === 'dark' ? 'light' : 'dark';
      setTheme(next);
    }

    // ---------- STATE ----------
    let currentUser = null;
    let detailProductId = null;

    const $ = id => document.getElementById(id);
    const loginPage = $('loginPage');
    const adminLoginPage = $('adminLoginPage');
    const mainPage = $('mainPage');
    const detailPage = $('detailPage');
    const adminPage = $('adminPage');
    const productGrid = $('productGrid');
    const searchInput = $('searchInput');

    const userLoginBtn = $('userLoginBtn');
    const userLoginUser = $('userLoginUser');
    const userLoginPass = $('userLoginPass');
    const userLogoutBtn = $('userLogoutBtn');
    const goToAdminLoginBtn = $('goToAdminLoginBtn');
    const backToUserLoginBtn = $('backToUserLoginBtn');

    const adminLoginBtn = $('adminLoginBtn');
    const adminLoginUser = $('adminLoginUser');
    const adminLoginPass = $('adminLoginPass');
    const adminLogoutBtn = $('adminLogoutBtn');

    const backFromDetail = $('backFromDetail');
    const detailMainMedia = $('detailMainMedia');
    const detailThumbs = $('detailThumbs');
    const detailTitle = $('detailTitle');
    const detailDesc = $('detailDesc');
    const detailSpec = $('detailSpec');

    const newProductName = $('newProductName');
    const newProductCat = $('newProductCat');
    const newProductDesc = $('newProductDesc');
    const newProductImgUrl = $('newProductImgUrl');
    const newProductVideoUrl = $('newProductVideoUrl');
    const addProductBtn = $('addProductBtn');
    const deleteProductId = $('deleteProductId');
    const deleteProductBtn = $('deleteProductBtn');
    const editProductId = $('editProductId');
    const editProductName = $('editProductName');
    const editProductImg = $('editProductImg');
    const editProductVideo = $('editProductVideo');
    const editProductDesc = $('editProductDesc');
    const editProductBtn = $('editProductBtn');
    const newUsername = $('newUsername');
    const newUserPass = $('newUserPass');
    const addUserBtn = $('addUserBtn');
    const userList = $('userList');
    const changePassUsername = $('changePassUsername');
    const changePassNew = $('changePassNew');
    const changeUserPassBtn = $('changeUserPassBtn');
    const fileInput = $('productFiles');
    const filePreviewGrid = $('filePreviewGrid');

    const themeToggle = $('themeToggle');
    const themeToggleAdmin = $('themeToggleAdmin');

    // ---------- FILE UPLOAD ----------
    fileInput.addEventListener('change', function(e) {
      const files = e.target.files;
      filePreviewGrid.innerHTML = '';
      uploadedFiles = [];
      
      for (let i = 0; i < files.length; i++) {
        const file = files[i];
        const reader = new FileReader();
        const fileIndex = i;
        
        reader.onload = function(ev) {
          const dataUrl = ev.target.result;
          const fileType = file.type.startsWith('video') ? 'video' : 'image';
          uploadedFiles.push({ type: fileType, data: dataUrl, name: file.name });
          
          const div = document.createElement('div');
          div.className = 'preview-item';
          if (fileType === 'video') {
            div.innerHTML = `<video src="${dataUrl}" muted playsinline></video>`;
          } else {
            div.innerHTML = `<img src="${dataUrl}" alt="preview">`;
          }
          
          const removeBtn = document.createElement('button');
          removeBtn.className = 'remove-file';
          removeBtn.innerHTML = '×';
          removeBtn.onclick = function(e) {
            e.stopPropagation();
            div.remove();
            uploadedFiles = uploadedFiles.filter((_, idx) => idx !== fileIndex);
          };
          div.appendChild(removeBtn);
          filePreviewGrid.appendChild(div);
        };
        reader.readAsDataURL(file);
      }
    });

    // ---------- RENDER ----------
    function renderProducts(filter = '') {
      const term = filter.trim().toLowerCase();
      let filtered = products.filter(p => p.name.toLowerCase().includes(term));
      productGrid.innerHTML = filtered.map(p => `
        <div class="product-card glass-card" data-id="${p.id}">
          <div class="product-media">
            ${p.img ? `<img src="${p.img}" alt="${p.name}">` : `<i class="fas ${p.icon || 'fa-box'} product-icon"></i>`}
          </div>
          <h3>${p.name}</h3>
          <p>${p.desc ? p.desc.slice(0, 30) : ''}...</p>
          <div style="font-size:0.5rem;color:var(--text-dim);margin-top:4px;">ID: ${p.id}</div>
        </div>
      `).join('');
      document.querySelectorAll('.product-card').forEach(card => {
        card.addEventListener('click', function() {
          const id = parseInt(this.dataset.id);
          showDetail(id);
        });
      });
    }

    function renderUsers() {
      userList.innerHTML = users.map(u => `
        <div class="user-item">
          <span>${u.username}</span>
          <div style="display:flex; gap:4px;">
            <button class="btn btn-danger btn-xs delete-user" data-username="${u.username}">Delete</button>
          </div>
        </div>
      `).join('');
      document.querySelectorAll('.delete-user').forEach(btn => {
        btn.addEventListener('click', function() {
          const uname = this.dataset.username;
          if (uname === 'admin123') { alert('Cannot delete main admin.'); return; }
          users = users.filter(u => u.username !== uname);
          saveUsers();
          renderUsers();
        });
      });
    }

    function showDetail(id) {
      const p = products.find(x => x.id === id);
      if (!p) return;
      detailProductId = id;
      detailTitle.textContent = p.name;
      detailDesc.textContent = p.desc || 'No description.';
      detailSpec.textContent = p.category ? `Category: ${p.category}` : '';

      // Main media
      if (p.video && p.video.length > 0) {
        detailMainMedia.innerHTML = `<video src="${p.video}" controls autoplay muted loop playsinline></video>`;
      } else if (p.img && p.img.length > 0) {
        detailMainMedia.innerHTML = `<img src="${p.img}" alt="${p.name}">`;
      } else {
        detailMainMedia.innerHTML = `<i class="fas ${p.icon || 'fa-box'} detail-icon"></i>`;
      }

      // Thumbs
      const thumbs = [];
      if (p.video && p.video.length > 0) thumbs.push({ type: 'video', src: p.video });
      if (p.img && p.img.length > 0) thumbs.push({ type: 'image', src: p.img });
      // Add icon as thumb if no media
      if (thumbs.length === 0) {
        thumbs.push({ type: 'icon', icon: p.icon || 'fa-box' });
        thumbs.push({ type: 'icon', icon: 'fa-star' });
        thumbs.push({ type: 'icon', icon: 'fa-heart' });
      }

      detailThumbs.innerHTML = thumbs.map(t => {
        if (t.type === 'video') {
          return `<div class="thumb-item"><video src="${t.src}" muted playsinline onclick="document.getElementById('detailMainMedia').innerHTML='<video src=\\'${t.src}\\' controls autoplay muted loop playsinline></video>'"></video></div>`;
        } else if (t.type === 'image') {
          return `<div class="thumb-item"><img src="${t.src}" alt="thumb" onclick="document.getElementById('detailMainMedia').innerHTML='<img src=\\'${t.src}\\' alt=\\'product\\'>'"></div>`;
        } else {
          return `<div class="thumb-item" onclick="document.getElementById('detailMainMedia').innerHTML='<i class=\\'fas ${t.icon} detail-icon\\'></i>'"><i class="fas ${t.icon} thumb-icon"></i></div>`;
        }
      }).join('');
      showPage('detail');
    }

    function showPage(page) {
      [loginPage, adminLoginPage, mainPage, detailPage, adminPage].forEach(p => p.classList.remove('active'));
      if (page === 'login') loginPage.classList.add('active');
      else if (page === 'adminLogin') adminLoginPage.classList.add('active');
      else if (page === 'main') { mainPage.classList.add('active'); renderProducts(searchInput.value); }
      else if (page === 'detail') detailPage.classList.add('active');
      else if (page === 'admin') { adminPage.classList.add('active'); renderUsers(); }
    }

    // ---------- AUTH ----------
    function userLogin(username, password) {
      const found = users.find(u => u.username === username && u.password === password);
      if (found) {
        currentUser = 'user';
        showPage('main');
        return true;
      }
      return false;
    }

    function adminLogin(username, password) {
      const found = users.find(u => u.username === username && u.password === password);
      if (found && username === 'admin123') {
        currentUser = 'admin';
        showPage('admin');
        return true;
      }
      return false;
    }

    // ---------- EVENTS ----------
    userLoginBtn.addEventListener('click', function() {
      const u = userLoginUser.value.trim();
      const p = userLoginPass.value.trim();
      if (!userLogin(u, p)) alert('Invalid credentials');
    });
    userLoginPass.addEventListener('keydown', e => { if (e.key === 'Enter') userLoginBtn.click(); });
    userLoginUser.addEventListener('keydown', e => { if (e.key === 'Enter') userLoginBtn.click(); });

    userLogoutBtn.addEventListener('click', function() {
      currentUser = null;
      showPage('login');
    });

    goToAdminLoginBtn.addEventListener('click', function() { showPage('adminLogin'); });
    backToUserLoginBtn.addEventListener('click', function() { showPage('login'); });

    adminLoginBtn.addEventListener('click', function() {
      const u = adminLoginUser.value.trim();
      const p = adminLoginPass.value.trim();
      if (!adminLogin(u, p)) alert('Invalid admin credentials');
    });
    adminLoginPass.addEventListener('keydown', e => { if (e.key === 'Enter') adminLoginBtn.click(); });
    adminLoginUser.addEventListener('keydown', e => { if (e.key === 'Enter') adminLoginBtn.click(); });

    adminLogoutBtn.addEventListener('click', function() {
      currentUser = null;
      showPage('login');
    });

    backFromDetail.addEventListener('click', function() { showPage('main'); });

    searchInput.addEventListener('input', function() { renderProducts(this.value); });

    // ---- Theme ----
    function initTheme() {
      const theme = getTheme();
      setTheme(theme);
    }
    themeToggle.addEventListener('click', toggleTheme);
    themeToggleAdmin.addEventListener('click', toggleTheme);

    // ---- Admin actions ----
    addProductBtn.addEventListener('click', function() {
      const name = newProductName.value.trim();
      let img = newProductImgUrl.value.trim();
      let video = newProductVideoUrl.value.trim();

      if (uploadedFiles.length > 0) {
        const imageFile = uploadedFiles.find(f => f.type === 'image');
        const videoFile = uploadedFiles.find(f => f.type === 'video');
        if (imageFile) img = imageFile.data;
        if (videoFile) video = videoFile.data;
      }

      const cat = newProductCat.value.trim() || 'general';
      const desc = newProductDesc.value.trim() || 'No description';
      if (!name) { alert('Product name required'); return; }

      const newId = products.length ? Math.max(...products.map(p => p.id)) + 1 : 1;
      const icon = 'fa-box';
      products.push({ id: newId, name, category: cat, icon, img, video, desc });
      saveProducts();
      renderProducts(searchInput.value);
      
      newProductName.value = '';
      newProductCat.value = '';
      newProductDesc.value = '';
      newProductImgUrl.value = '';
      newProductVideoUrl.value = '';
      fileInput.value = '';
      filePreviewGrid.innerHTML = '';
      uploadedFiles = [];
      alert('Product added successfully!');
    });

    deleteProductBtn.addEventListener('click', function() {
      const id = parseInt(deleteProductId.value.trim());
      if (isNaN(id)) { alert('Enter valid product ID'); return; }
      products = products.filter(p => p.id !== id);
      saveProducts();
      renderProducts(searchInput.value);
      deleteProductId.value = '';
    });

    editProductBtn.addEventListener('click', function() {
      const id = parseInt(editProductId.value.trim());
      if (isNaN(id)) { alert('Enter valid product ID'); return; }
      const p = products.find(x => x.id === id);
      if (!p) { alert('Product not found'); return; }
      if (editProductName.value.trim()) p.name = editProductName.value.trim();
      if (editProductImg.value.trim()) p.img = editProductImg.value.trim();
      if (editProductVideo.value.trim()) p.video = editProductVideo.value.trim();
      if (editProductDesc.value.trim()) p.desc = editProductDesc.value.trim();
      saveProducts();
      renderProducts(searchInput.value);
      editProductId.value = '';
      editProductName.value = '';
      editProductImg.value = '';
      editProductVideo.value = '';
      editProductDesc.value = '';
      alert('Product updated!');
    });

    addUserBtn.addEventListener('click', function() {
      const u = newUsername.value.trim();
      const p = newUserPass.value.trim();
      if (!u || !p) { alert('Username and password required'); return; }
      if (users.some(x => x.username === u)) { alert('User already exists'); return; }
      users.push({ username: u, password: p });
      saveUsers();
      renderUsers();
      newUsername.value = '';
      newUserPass.value = '';
      alert('User added!');
    });

    changeUserPassBtn.addEventListener('click', function() {
      const uname = changePassUsername.value.trim();
      const newPass = changePassNew.value.trim();
      if (!uname || !newPass) { alert('Username and new password required'); return; }
      const user = users.find(u => u.username === uname);
      if (!user) { alert('User not found'); return; }
      user.password = newPass;
      saveUsers();
      renderUsers();
      changePassUsername.value = '';
      changePassNew.value = '';
      alert('Password updated');
    });

    // ---------- INIT ----------
    loadData();
    initTheme();
    showPage('login');
    renderProducts();
    renderUsers();
  })();
</script>
</body>
</html>