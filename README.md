[Uploading index.html…]()
<!DOCTYPE html>
<html lang="pt-BR" data-theme="dark">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Westie — Automações com IA</title>
<!--
GUIA DE EDIÇÃO
- Textos: procure o conteúdo entre as tags de cada seção (marcadas com <!-- SEÇÃO: ... -->).
- Cores: altere as variáveis em /* ===== VARIÁVEIS ===== */ no bloco :root.
- Espaçamentos e tipografia: também em :root (--space-*, --font-*).
- Seções: cada seção é um bloco <section> independente. Para remover uma, apague o bloco inteiro
  e o link correspondente no header. Para adicionar, copie um bloco existente e ajuste o id.
- Preços: alterados no array PLANOS dentro de // ===== PLANOS =====.
- Serviços (modais): array SERVICOS em // ===== MODAIS =====.
-->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Space+Grotesk:wght@500;600;700&display=swap">
<style>
/* Skip artifact shell — fixed styles served beside every artifact.
   Tokens, utilities and components (basecoat 1.0 markup, no CDN); artifacts
   override --accent for their own identity. */
:root {
  color-scheme: light dark;
  --accent: #2563eb;
  --accent-contrast: #ffffff;
  --accent-text: color-mix(in srgb, var(--accent) 72%, #000);
  --bg: #f8f9fb;
  --surface: #ffffff;
  --text: #14171f;
  --text-muted: #5b6472;
  --border: rgba(20, 23, 31, 0.10);
  --radius: 10px;
  --shadow: 0 1px 3px rgba(20, 23, 31, 0.08);
  --space: 16px;
  --success: #0a7a35;
  --danger: #c0262d;
  --warning: #8a5300;
}
/* Theme resolution. Without data-theme the viewer's system preference decides,
   as it always did. With it, the artifact's own choice wins in BOTH directions:
   a page that hardcodes one palette must not be handed the opposite set of
   tokens by the machine it happens to be opened on. The dark values appear
   twice because a media query cannot be folded into a selector list.
   The attribute sits inside :where() so these blocks keep the specificity of a
   bare :root — the page's own <style> is linked after this file and must go on
   overriding any token it wants, exactly as it could before. */
@media (prefers-color-scheme: dark) {
  :root:where(:not([data-theme="light"])) {
    --accent-text: color-mix(in srgb, var(--accent) 78%, #fff);
    --bg: #101318;
    --surface: #181c23;
    --text: #eef1f6;
    --text-muted: #9aa4b2;
    --border: rgba(238, 241, 246, 0.12);
    --shadow: 0 1px 3px rgba(0, 0, 0, 0.4);
    --success: #4ade80;
    --danger: #f87171;
    --warning: #fbbf24;
  }
}
:root:where([data-theme="dark"]) {
  color-scheme: dark;
  --accent-text: color-mix(in srgb, var(--accent) 78%, #fff);
  --bg: #101318;
  --surface: #181c23;
  --text: #eef1f6;
  --text-muted: #9aa4b2;
  --border: rgba(238, 241, 246, 0.12);
  --shadow: 0 1px 3px rgba(0, 0, 0, 0.4);
  --success: #4ade80;
  --danger: #f87171;
  --warning: #fbbf24;
}
:root:where([data-theme="light"]) { color-scheme: light; }
/* Pages generated before the shell had its own components still link the
   basecoat CDN, which reads its own tokens and switches theme only on a
   .dark class. Bridged to the shell's, whatever of it those pages use takes
   the page's accent and follows the declared theme. Its --accent token is a
   hover tint, renamed in its theme as --color-accent; the shell's --accent is
   the brand colour, so the tint is derived from it here. */
:root {
  --background: var(--bg);
  --foreground: var(--text);
  --card: var(--surface);
  --card-foreground: var(--text);
  --popover: var(--surface);
  --popover-foreground: var(--text);
  --primary: var(--accent);
  --primary-foreground: var(--accent-contrast);
  --secondary: color-mix(in srgb, var(--text) 7%, var(--surface));
  --secondary-foreground: var(--text);
  --muted: color-mix(in srgb, var(--text) 5%, var(--surface));
  --muted-foreground: var(--text-muted);
  --color-accent: color-mix(in srgb, var(--accent) 12%, var(--surface));
  --color-accent-foreground: var(--text);
  --destructive: var(--danger);
  --input: var(--border);
  --ring: var(--accent);
}
* { box-sizing: border-box; }
/* The reset the pages were written against: they all linked basecoat, which
   ships Tailwind's. Its components now live here, so the reset does too. */
*, ::before, ::after, ::backdrop { margin: 0; padding: 0; border: 0 solid; }
/* Preflight's rule too: without it a component class that sets display
   (.alert, .card, .btn…) beats the hidden attribute and shows the element. */
[hidden]:where(:not([hidden="until-found"])) { display: none !important; }
.hidden { display: none !important; }
h1, h2, h3, h4, h5, h6 { font-size: inherit; font-weight: inherit; }
a { color: inherit; text-decoration: inherit; }
b, strong { font-weight: bolder; }
ol, ul, menu { list-style: none; }
svg, video, canvas, iframe { display: block; vertical-align: middle; }
button, input, select, textarea { color: inherit; background-color: transparent; border-radius: 0; }
table { border-collapse: collapse; }
hr { height: 0; color: inherit; border-top-width: 1px; }
html, body { margin: 0; padding: 0; }
body {
  background: var(--bg);
  color: var(--text);
  font-family: system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
  line-height: 1.55;
  -webkit-font-smoothing: antialiased;
}
img { max-width: 100%; display: block; }

.shell-container { max-width: 1100px; margin: 0 auto; padding: 0 20px; }
.shell-section { padding: calc(var(--space) * 2) 0; }
.shell-grid { display: grid; gap: var(--space); grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); }
.shell-toolbar { display: flex; flex-wrap: wrap; gap: 10px; align-items: center; margin-bottom: var(--space); }
.shell-footer { padding: 24px 0 40px; color: var(--text-muted); font-size: 13px; }

.shell-hero { padding: calc(var(--space) * 3) 0 calc(var(--space) * 2); }
.shell-hero h1 { font-size: clamp(26px, 4vw, 40px); line-height: 1.15; margin: 0 0 10px; text-wrap: balance; }
.shell-hero p { color: var(--text-muted); max-width: 60ch; margin: 0; }

.panel {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  box-shadow: var(--shadow);
  padding: var(--space);
}

.kpi { display: flex; flex-direction: column; gap: 4px; }
.kpi .kpi-value { font-size: clamp(22px, 2.3vw, 28px); font-weight: 650; line-height: 1.1; overflow-wrap: anywhere; font-variant-numeric: tabular-nums; }
.kpi .kpi-label { font-size: 13px; color: var(--text-muted); }
.kpi .kpi-delta { font-size: 12.5px; font-weight: 600; }
.kpi .kpi-delta.up { color: var(--success); }
.kpi .kpi-delta.down { color: var(--danger); }

table.shell-table { border-collapse: collapse; width: 100%; font-size: 14px; }
table.shell-table th {
  text-align: left; font-size: 11.5px; letter-spacing: 0.05em; text-transform: uppercase;
  color: var(--text-muted); font-weight: 600;
}
table.shell-table th, table.shell-table td { padding: 9px 12px 9px 0; border-bottom: 1px solid var(--border); }
table.shell-table td.num, table.shell-table th.num { text-align: right; font-variant-numeric: tabular-nums; }
table.shell-table tbody tr:hover { background: color-mix(in srgb, var(--accent) 6%, transparent); }

.chart-box { width: 100%; min-height: 220px; }
.chart-box svg { width: 100%; height: auto; display: block; }
.chart-legend { display: flex; flex-wrap: wrap; justify-content: center; gap: 6px 16px; margin-top: 12px; font-size: 12.5px; color: var(--text-muted); }
.chart-legend span { display: inline-flex; align-items: center; gap: 6px; }
.chart-legend i { width: 9px; height: 9px; border-radius: 50%; display: inline-block; }
.chart-legend b { color: var(--text); font-weight: 600; font-variant-numeric: tabular-nums; }

.muted { color: var(--text-muted); }
.accent { color: var(--accent-text); }
.shell-badge, .eyebrow {
  display: inline-flex; align-items: center; gap: 6px;
  font-size: 12px; font-weight: 600; padding: 3px 10px; border-radius: 999px;
  background: color-mix(in srgb, var(--accent) 12%, transparent); color: var(--accent-text);
}
/* A pill keeps its content width inside flex and grid columns, which would
   otherwise stretch it across the card; a centred parent still centres it. */
.shell-badge, .eyebrow, .badge { width: fit-content; max-width: 100%; }

@media (prefers-reduced-motion: no-preference) {
  .shell-fade { animation: shell-fade 400ms ease both; }
  @keyframes shell-fade { from { opacity: 0; transform: translateY(6px); } to { opacity: 1; transform: none; } }
}

/* Layout and type utilities: what the pages kept spelling in style="".
   Spacing and type sizes follow Tailwind's scale; there is no Tailwind. */
.row { display: flex; flex-wrap: wrap; align-items: center; gap: 12px; }
.stack { display: flex; flex-direction: column; gap: var(--space); }
.between { justify-content: space-between; }
.grow { flex: 1 1 0; min-width: 0; }
.cols-2, .cols-3, .cols-4, .cols-5 { display: grid; gap: var(--space); grid-template-columns: minmax(0, 1fr); }
@media (min-width: 720px) {
  .cols-2, .cols-4 { grid-template-columns: repeat(2, minmax(0, 1fr)); }
  .cols-3 { grid-template-columns: repeat(3, minmax(0, 1fr)); }
  .cols-5 { grid-template-columns: repeat(3, minmax(0, 1fr)); }
}
@media (min-width: 1000px) { .cols-4 { grid-template-columns: repeat(4, minmax(0, 1fr)); } }
@media (min-width: 1100px) { .cols-5 { grid-template-columns: repeat(5, minmax(0, 1fr)); } }
.gap-1 { gap: 4px; } .gap-2 { gap: 8px; } .gap-3 { gap: 12px; } .gap-4 { gap: 16px; } .gap-6 { gap: 24px; }
.m-0 { margin: 0; }
.mt-1 { margin-top: 4px; } .mt-2 { margin-top: 8px; } .mt-3 { margin-top: 12px; } .mt-4 { margin-top: 16px; } .mt-6 { margin-top: 24px; }
.mb-1 { margin-bottom: 4px; } .mb-2 { margin-bottom: 8px; } .mb-3 { margin-bottom: 12px; } .mb-4 { margin-bottom: 16px; } .mb-6 { margin-bottom: 24px; }
.p-2 { padding: 8px; } .p-3 { padding: 12px; } .p-4 { padding: 16px; } .p-6 { padding: 24px; }
.text-xs { font-size: 12px; } .text-sm { font-size: 14px; } .text-base { font-size: 16px; }
.text-lg { font-size: 18px; } .text-xl { font-size: 20px; line-height: 1.35; }
.text-2xl { font-size: 24px; line-height: 1.25; } .text-3xl { font-size: 30px; line-height: 1.2; }
.font-medium { font-weight: 500; } .font-semibold { font-weight: 600; } .font-bold { font-weight: 700; }
.text-right { text-align: right; } .text-center { text-align: center; }
.nowrap { white-space: nowrap; }
.truncate { overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
.mono { font-family: ui-monospace, SFMono-Regular, Menlo, monospace; font-variant-numeric: tabular-nums; }
.w-full { width: 100%; }
.text-success { color: var(--success); } .text-danger { color: var(--danger); } .text-warning { color: var(--warning); }

/* Components, with basecoat 1.0 markup (variants and sizes are data
   attributes) and the shell tokens, so a page needs neither component CSS
   nor a CSS framework. An older page that also links basecoat gets these
   rules after it, over the same properties. */
button, input, select, textarea { font: inherit; }
input[type="checkbox"], input[type="radio"] { accent-color: var(--accent); }
:focus-visible { outline: 2px solid var(--accent); outline-offset: 2px; }

.btn {
  display: inline-flex; align-items: center; justify-content: center; gap: 6px;
  height: 36px; padding: 0 14px; border: 1px solid transparent; border-radius: calc(var(--radius) - 2px);
  background: var(--accent); color: var(--accent-contrast);
  font-size: 14px; font-weight: 500; line-height: 1; white-space: nowrap; text-decoration: none; cursor: pointer;
  transition: background-color 150ms ease, border-color 150ms ease, color 150ms ease;
}
.btn:hover { background: color-mix(in srgb, var(--accent) 86%, #000); }
.btn:disabled, .btn[aria-disabled="true"] { opacity: 0.5; pointer-events: none; }
.btn[data-variant="secondary"] { background: color-mix(in srgb, var(--text) 8%, var(--surface)); color: var(--text); }
.btn[data-variant="secondary"]:hover { background: color-mix(in srgb, var(--text) 14%, var(--surface)); }
.btn[data-variant="outline"] { background: var(--surface); color: var(--text); border-color: var(--border); }
.btn[data-variant="ghost"] { background: transparent; color: var(--text); }
.btn[data-variant="outline"]:hover, .btn[data-variant="ghost"]:hover { background: color-mix(in srgb, var(--accent) 10%, var(--surface)); }
.btn[data-variant="destructive"] { background: var(--danger); color: var(--bg); }
.btn[data-variant="destructive"]:hover { background: color-mix(in srgb, var(--danger) 86%, var(--text)); }
.btn[data-variant="link"] { height: auto; padding: 0; background: none; color: var(--accent-text); text-decoration: underline; text-underline-offset: 3px; }
.btn[data-size="sm"] { height: 30px; padding: 0 10px; font-size: 13px; }
.btn[data-size="lg"] { height: 42px; padding: 0 20px; font-size: 15px; }
.btn[data-size="icon"] { width: 36px; padding: 0; }

.badge {
  display: inline-flex; align-items: center; gap: 4px; padding: 2px 8px;
  border: 1px solid transparent; border-radius: 999px; background: var(--accent); color: var(--accent-contrast);
  font-size: 12px; font-weight: 600; line-height: 1.5; white-space: nowrap;
}
.badge[data-variant="secondary"] { background: color-mix(in srgb, var(--text) 8%, var(--surface)); color: var(--text); }
.badge[data-variant="outline"] { background: transparent; color: var(--text); border-color: var(--border); }
.badge[data-variant="destructive"] { background: color-mix(in srgb, var(--danger) 14%, var(--surface)); color: var(--danger); }

.alert {
  display: grid; gap: 4px; padding: 12px 16px; border: 1px solid var(--border); border-radius: var(--radius);
  background: var(--surface); color: var(--text); font-size: 14px;
}
.alert h2, .alert h3 { margin: 0; font-size: 14px; font-weight: 600; }
.alert p, .alert section { margin: 0; color: var(--text-muted); }
.alert[data-variant="destructive"] { border-color: color-mix(in srgb, var(--danger) 45%, var(--border)); background: color-mix(in srgb, var(--danger) 7%, var(--surface)); color: var(--danger); }

.card {
  display: flex; flex-direction: column; gap: 16px; padding: 20px 0;
  border: 1px solid var(--border); border-radius: calc(var(--radius) + 2px);
  background: var(--surface); color: var(--text); box-shadow: var(--shadow);
}
.card > header, .card > section, .card > footer { padding: 0 20px; }
.card > header { display: grid; gap: 4px; }
.card > header h2, .card > header h3 { margin: 0; font-size: 16px; font-weight: 600; line-height: 1.3; }
.card > header p { margin: 0; color: var(--text-muted); font-size: 14px; }
.card > footer { display: flex; flex-wrap: wrap; align-items: center; gap: 8px; }

.input {
  width: 100%; min-height: 36px; padding: 6px 12px; border: 1px solid var(--border); border-radius: calc(var(--radius) - 2px);
  background: var(--surface); color: var(--text); font-size: 14px;
}
textarea.input { min-height: 84px; resize: vertical; }
.input::placeholder { color: var(--text-muted); }
.input:focus { outline: none; border-color: var(--accent); box-shadow: 0 0 0 3px color-mix(in srgb, var(--accent) 25%, transparent); }
.field { display: grid; gap: 6px; }
.field label { font-size: 14px; font-weight: 500; }
.field [role="alert"] { color: var(--danger); font-size: 13px; }

dialog.dialog {
  width: min(520px, calc(100vw - 32px)); max-height: calc(100vh - 32px); margin: auto; padding: 0;
  border: 1px solid var(--border); border-radius: calc(var(--radius) + 4px);
  background: var(--surface); color: var(--text); box-shadow: 0 20px 50px rgba(0, 0, 0, 0.25);
}
dialog.dialog::backdrop { background: rgba(0, 0, 0, 0.5); }
dialog.dialog > div { display: grid; gap: 16px; padding: 24px; }
dialog.dialog header { display: grid; gap: 4px; }
dialog.dialog header h2 { margin: 0; font-size: 18px; font-weight: 600; }
dialog.dialog header p { margin: 0; color: var(--text-muted); font-size: 14px; }
dialog.dialog footer { display: flex; flex-wrap: wrap; justify-content: flex-end; gap: 8px; }

.tabs { display: grid; gap: 12px; }
.tabs > [role="tablist"] {
  display: inline-flex; gap: 4px; width: fit-content; max-width: 100%; padding: 4px; overflow-x: auto;
  border-radius: var(--radius); background: color-mix(in srgb, var(--text) 6%, var(--surface));
}
.tabs [role="tab"] {
  padding: 6px 12px; border: 0; border-radius: calc(var(--radius) - 4px); background: transparent;
  color: var(--text-muted); font-size: 14px; font-weight: 500; white-space: nowrap; cursor: pointer;
}
.tabs [role="tab"][aria-selected="true"] { background: var(--surface); color: var(--text); box-shadow: var(--shadow); }
.tabs [role="tabpanel"][hidden] { display: none; }

.accordion > details { border-bottom: 1px solid var(--border); }
.accordion > details > summary {
  display: flex; align-items: center; justify-content: space-between; gap: 12px;
  padding: 14px 0; font-weight: 500; list-style: none; cursor: pointer;
}
.accordion > details > summary::-webkit-details-marker { display: none; }
.accordion > details > summary::after { content: "+"; color: var(--text-muted); font-size: 18px; line-height: 1; }
.accordion > details[open] > summary::after { content: "\2212"; }
.accordion > details > :not(summary) { margin: 0 0 14px; color: var(--text-muted); }

.toaster {
  position: fixed; right: 16px; bottom: 16px; z-index: 50; display: flex; flex-direction: column-reverse; gap: 8px;
  width: min(360px, calc(100vw - 32px)); pointer-events: none;
}
.toaster .toast { pointer-events: auto; transition: opacity 200ms ease, transform 200ms ease; }
.toaster .toast[aria-hidden="true"] { opacity: 0; transform: translateY(8px); }
.toaster .toast-content {
  padding: 12px 14px; border: 1px solid var(--border); border-radius: var(--radius);
  background: var(--surface); color: var(--text); box-shadow: 0 8px 24px rgba(0, 0, 0, 0.12); font-size: 13px;
}
.toaster .toast-content h2 { margin: 0 0 2px; font-size: 14px; font-weight: 600; }
.toaster .toast-content p { margin: 0; color: var(--text-muted); }

/* skipUI building blocks. */
.skip-table-search { max-width: 320px; margin-bottom: 12px; }
.skip-table-wrap { overflow-x: auto; }
table.shell-table th[data-sort] { cursor: pointer; user-select: none; }
table.shell-table th[aria-sort="ascending"]::after { content: " \25B2"; font-size: 9px; }
table.shell-table th[aria-sort="descending"]::after { content: " \25BC"; font-size: 9px; }
table.shell-table td.skip-table-empty { color: var(--text-muted); text-align: center; padding: 24px 0; }
.skip-pager { display: flex; flex-wrap: wrap; align-items: center; justify-content: space-between; gap: 12px; margin-top: 12px; font-size: 13px; color: var(--text-muted); }
.toaster .toast[data-type="success"] .toast-content { border-left: 3px solid var(--success); }
.toaster .toast[data-type="error"] .toast-content { border-left: 3px solid var(--danger); }

</style>
<script>
/* Skip artifact shell — fixed helpers served beside every artifact. */
(function () {
  "use strict";

  var fmt = {
    num: function (v, opts) { return new Intl.NumberFormat("pt-BR", opts || {}).format(v); },
    brl: function (v) { return new Intl.NumberFormat("pt-BR", { style: "currency", currency: "BRL" }).format(v); },
    pct: function (v) { return new Intl.NumberFormat("pt-BR", { style: "percent", maximumFractionDigits: 1 }).format(v); },
    compact: function (v) { return new Intl.NumberFormat("pt-BR", { notation: "compact", maximumFractionDigits: 1 }).format(v); },
    brlCompact: function (v) { return new Intl.NumberFormat("pt-BR", { style: "currency", currency: "BRL", notation: "compact", maximumFractionDigits: 1 }).format(v); }
  };

  // axisLabels formats the five y-axis ticks in the unit the chart declared
  // (percent, BRL or plain numbers), compact so long values never clip, with
  // the fewest decimals that still print every tick exactly (1,5 mi, not 2 mi).
  function axisLabels(format, ticks) {
    function at(digits) {
      var opts = { notation: "compact", maximumFractionDigits: digits };
      if (format === "pct") opts = { style: "percent", maximumFractionDigits: digits };
      else if (format === "brl") opts = { style: "currency", currency: "BRL", notation: "compact", maximumFractionDigits: digits };
      var nf = new Intl.NumberFormat("pt-BR", opts);
      return ticks.map(function (t) { return nf.format(t); });
    }
    for (var digits = 0; digits < 2; digits++) {
      if (at(digits).join("|") === at(digits + 1).join("|")) return at(digits);
    }
    return at(2);
  }

  // yAxisPad formats the ticks and measures the left padding they need from
  // the longest one; drawYAxis then draws the grid and the labels.
  function yAxisPad(format, max) {
    var labels = axisLabels(format, [0, max / 4, max / 2, (max * 3) / 4, max]);
    var longest = labels.reduce(function (m, l) { return Math.max(m, l.length); }, 0);
    return { labels: labels, padL: Math.max(40, Math.round(longest * 6.2) + 14) };
  }
  function drawYAxis(svg, axis, W, padR, padT, plotH) {
    for (var g = 0; g <= 4; g++) {
      var gy = padT + plotH - (plotH * g) / 4;
      svg.appendChild(svgEl("line", { x1: axis.padL, y1: gy, x2: W - padR, y2: gy, stroke: "currentColor", "stroke-opacity": 0.08 }));
      var lbl = svgEl("text", { x: axis.padL - 8, y: gy + 4, "text-anchor": "end", "font-size": 10, fill: mutedColor() });
      lbl.textContent = axis.labels[g];
      svg.appendChild(lbl);
    }
  }

  // xLabelStep: show every k-th category label so labels never overlap, and
  // always the last one (counted back from the end).
  function xLabelStep(labels, step) {
    var longest = labels.reduce(function (m, l) { return Math.max(m, String(l).length); }, 0);
    return Math.max(1, Math.ceil((longest * 6.4 + 8) / Math.max(step, 1)));
  }
  function drawXLabel(svg, text, x, y, W, edgeGuard) {
    var anchor = "middle";
    var half = String(text).length * 3.2;
    if (edgeGuard && x - half < 4) anchor = "start";
    if (edgeGuard && x + half > W - 4) anchor = "end";
    var tx = svgEl("text", { x: x, y: y, "text-anchor": anchor, "font-size": 11, fill: mutedColor() });
    tx.textContent = text;
    svg.appendChild(tx);
  }
  // categoryLines fits a bar's category name in its slot: one line, two lines
  // split at a space, or cut with "…". A bar without its name can't be read, so
  // categories are never skipped; null when the slot is too narrow for that.
  function categoryLines(text, slot) {
    var fit = Math.floor((slot - 6) / 6.4);
    var s = String(text);
    if (fit < 4) return null;
    if (s.length <= fit) return [s];
    var cut = function (t) { return t.length <= fit ? t : t.slice(0, fit - 1).trimEnd() + "…"; };
    var best = -1;
    for (var i = 0; i < s.length; i++) {
      if (s[i] === " " && (best < 0 || Math.abs(s.length / 2 - i) < Math.abs(s.length / 2 - best))) best = i;
    }
    if (best < 0) return [cut(s)];
    return [cut(s.slice(0, best)), cut(s.slice(best + 1))];
  }
  function legend(el, items) {
    var box = document.createElement("div");
    box.className = "chart-legend";
    items.forEach(function (it) {
      var row = document.createElement("span");
      var dot = document.createElement("i");
      dot.style.background = it.color;
      row.appendChild(dot);
      row.appendChild(document.createTextNode((it.label || "") + (it.value ? " " : "")));
      if (it.value) {
        var v = document.createElement("b");
        v.textContent = it.value;
        row.appendChild(v);
      }
      box.appendChild(row);
    });
    resolve(el).appendChild(box);
  }
  var seriesPalette = ["#1baf7a", "#eda100", "#e34948", "#4a3aa7", "#e87ba4", "#0ea5b7"];

  // format accepts a function OR one of the fmt names ("num" | "brl" | "pct").
  // A page's function may return nothing or throw: the chart prints its
  // number instead of taking the rest of the page script down with it.
  function coerceFormat(spec) {
    if (typeof spec === "function") {
      return function (v) {
        try {
          var out = spec(v);
          return out == null ? "" : String(out);
        } catch (e) {
          return fmt.num(v);
        }
      };
    }
    if (typeof spec === "string" && fmt[spec]) return fmt[spec];
    return function (v) { return fmt.num(v); };
  }

  function accent() {
    return getComputedStyle(document.documentElement).getPropertyValue("--accent").trim() || "#2563eb";
  }
  function mutedColor() {
    return getComputedStyle(document.documentElement).getPropertyValue("--text-muted").trim() || "#5b6472";
  }
  function svgEl(tag, attrs) {
    var el = document.createElementNS("http://www.w3.org/2000/svg", tag);
    for (var k in attrs) el.setAttribute(k, attrs[k]);
    return el;
  }
  function frame(el, w, h) {
    var svg = svgEl("svg", { viewBox: "0 0 " + w + " " + h, role: "img" });
    el = resolve(el);
    el.innerHTML = "";
    el.appendChild(svg);
    return svg;
  }

  // maxOf guards the axis scale: empty values would give -Infinity (truthy,
  // so "|| 1" can't catch it) and a non-positive max would flip the chart.
  // finite reads a chart value as a number, 0 when it is not one (NaN,
  // Infinity, a stray string), so one bad value cannot blank the axis.
  function finite(v) {
    var n = +v;
    return isFinite(n) ? n : 0;
  }

  function maxOf(values) {
    var m = values.length ? Math.max.apply(null, values.map(finite)) : 0;
    return m > 0 ? m : 1;
  }

  // labelsFor pads or trims the category names to the n points drawn: pages
  // pass labels and values of different lengths, and one throw here loses
  // every section the page renders after the chart.
  function labelsFor(cfg, n) {
    var out = [];
    for (var i = 0; i < n; i++) out.push(cfg.labels && cfg.labels[i] != null ? String(cfg.labels[i]) : "");
    return out;
  }

  // niceMax rounds the scale up so the four grid steps land on round values
  // (1, 1.5, 2, 2.5, 3, 4, 5, 6 or 8 × 10^k) and the tick labels read exactly.
  function niceMax(max) {
    var raw = max / 4;
    var mag = Math.pow(10, Math.floor(Math.log10(raw)));
    var res = raw / mag;
    var steps = [1, 1.5, 2, 2.5, 3, 4, 5, 6, 8, 10];
    var nice = steps.filter(function (s) { return s >= res - 1e-9; })[0];
    return nice * mag * 4;
  }

  // bar(el, {labels:[], values:[], color?, format?}) — vertical bar chart.
  function bar(el, cfg) {
    var W = 640, H = 280, padB = 30, padT = 12, padR = 12;
    var max = niceMax(maxOf(cfg.values));
    var axis = yAxisPad(cfg.format, max);
    var svg = frame(el, W, H);
    var n = cfg.values.length;
    var labels = labelsFor(cfg, n);
    var plotW = W - axis.padL - padR;
    var step = plotW / n, bw = Math.min(step * 0.62, 64);
    var names = labels.map(function (l) { return categoryLines(l, step); });
    var named = names.every(Boolean);
    if (named && names.some(function (l) { return l.length > 1; })) padB = 42;
    var plotH = H - padT - padB;
    var color = cfg.color || accent();
    var f = coerceFormat(cfg.format);
    var every = xLabelStep(labels, step);
    drawYAxis(svg, axis, W, padR, padT, plotH);
    cfg.values.forEach(function (v, i) {
      var bh = Math.max(0, (finite(v) / max) * plotH);
      var x = axis.padL + i * step + (step - bw) / 2;
      var y = padT + plotH - bh;
      var r = svgEl("rect", { x: x, y: y, width: bw, height: bh, rx: 4, fill: (cfg.colors && cfg.colors[i]) || color });
      var t = svgEl("title", {});
      t.textContent = labels[i] + ": " + f(v);
      r.appendChild(t);
      svg.appendChild(r);
      if (named) {
        names[i].forEach(function (text, li) {
          drawXLabel(svg, text, x + bw / 2, padT + plotH + 18 + li * 13, W, false);
        });
      } else if ((n - 1 - i) % every === 0) {
        drawXLabel(svg, labels[i], x + bw / 2, H - 10, W, false);
      }
    });
  }

  // line(el, {labels:[], values:[] | series:[{label, values, color?}], color?, format?})
  // — one line, or several series on one scale with a legend under the chart.
  function line(el, cfg) {
    var W = 640, H = 280, padB = 30, padT = 12, padR = 16;
    var series = cfg.series && cfg.series.length
      ? cfg.series
      : [{ label: "", values: cfg.values || [], color: cfg.color }];
    var all = [];
    series.forEach(function (s) { all = all.concat(s.values || []); });
    var max = niceMax(maxOf(all));
    var axis = yAxisPad(cfg.format, max);
    var svg = frame(el, W, H);
    var n = series.reduce(function (m, s) { return Math.max(m, (s.values || []).length); }, 0);
    var labels = labelsFor(cfg, n);
    var plotW = W - axis.padL - padR, plotH = H - padT - padB;
    var f = coerceFormat(cfg.format);
    drawYAxis(svg, axis, W, padR, padT, plotH);
    var xs = labels.map(function (_, i) { return axis.padL + (n === 1 ? plotW / 2 : (plotW * i) / (n - 1)); });
    var every = xLabelStep(labels, n > 1 ? plotW / (n - 1) : plotW);
    labels.forEach(function (label, i) {
      if ((n - 1 - i) % every === 0) drawXLabel(svg, label, xs[i], H - 10, W, true);
    });
    var colors = series.map(function (s, si) {
      return s.color || (si === 0 ? (cfg.color || accent()) : seriesPalette[(si - 1) % seriesPalette.length]);
    });
    series.forEach(function (s, si) {
      var color = colors[si];
      var pts = (s.values || []).map(function (v, i) { return [xs[i], padT + plotH - (finite(v) / max) * plotH]; });
      var d = pts.map(function (p, i) { return (i ? "L" : "M") + p[0].toFixed(1) + " " + p[1].toFixed(1); }).join(" ");
      svg.appendChild(svgEl("path", { d: d, fill: "none", stroke: color, "stroke-width": 2, "stroke-linejoin": "round" }));
      pts.forEach(function (p, i) {
        var c = svgEl("circle", { cx: p[0], cy: p[1], r: 3.5, fill: color });
        var t = svgEl("title", {});
        t.textContent = (s.label ? s.label + " · " : "") + labels[i] + ": " + f(s.values[i]);
        c.appendChild(t);
        svg.appendChild(c);
      });
    });
    if (series.length > 1) {
      legend(el, series.map(function (s, si) { return { label: s.label, color: colors[si] }; }));
    }
  }

  // donut(el, {labels:[], values:[], colors?, format?, center?, centerLabel?, legend?})
  // — donut with a short total in the centre (compact, in the declared unit)
  // and, with legend: true, the labels and shares listed under it.
  function donut(el, cfg) {
    var W = 320, H = 280, cx = W / 2, cy = H / 2, R = 92, r = 58;
    var svg = frame(el, W, H);
    // At 100% of a wide container the donut outgrows the height pages give
    // the box and spills over the next section: keep it at its own size.
    svg.style.maxWidth = W + "px";
    svg.style.margin = "0 auto";
    var values = cfg.values.map(finite);
    var labels = labelsFor(cfg, values.length);
    var sum = values.reduce(function (a, b) { return a + b; }, 0);
    var total = sum || 1;
    var palette = cfg.colors || [accent()].concat(seriesPalette);
    // The hover keeps the full value; the centre has room for a short one.
    var full = coerceFormat(cfg.format);
    var short = typeof cfg.format === "function" ? full : cfg.format === "brl" ? fmt.brlCompact : fmt.compact;
    var a0 = -Math.PI / 2;
    values.forEach(function (v, i) {
      var a1 = a0 + (v / total) * Math.PI * 2;
      var large = a1 - a0 > Math.PI ? 1 : 0;
      var p = ["M", cx + R * Math.cos(a0), cy + R * Math.sin(a0),
        "A", R, R, 0, large, 1, cx + R * Math.cos(a1), cy + R * Math.sin(a1),
        "L", cx + r * Math.cos(a1), cy + r * Math.sin(a1),
        "A", r, r, 0, large, 0, cx + r * Math.cos(a0), cy + r * Math.sin(a0), "Z"].join(" ");
      var path = svgEl("path", { d: p, fill: palette[i % palette.length] });
      var t = svgEl("title", {});
      t.textContent = labels[i] + ": " + full(v) + " (" + fmt.pct(v / total) + ")";
      path.appendChild(t);
      svg.appendChild(path);
      a0 = a1;
    });
    // A share chart has no total worth printing: without its own centre text
    // the caption alone takes the middle.
    var text = cfg.center != null ? String(cfg.center) : (cfg.format === "pct" ? "" : short(sum));
    if (text) {
      var size = text.length > 9 ? 14 : text.length > 7 ? 17 : 20;
      var center = svgEl("text", { x: cx, y: cfg.centerLabel ? cy + 1 : cy + 6, "text-anchor": "middle", "font-size": size, "font-weight": 650, fill: "currentColor" });
      center.textContent = text;
      svg.appendChild(center);
    }
    if (cfg.centerLabel) {
      var cap = svgEl("text", { x: cx, y: text ? cy + 19 : cy + 5, "text-anchor": "middle", "font-size": 11, fill: mutedColor() });
      cap.textContent = cfg.centerLabel;
      svg.appendChild(cap);
    }
    if (cfg.legend) {
      legend(el, labels.map(function (label, i) {
        return { label: label, color: palette[i % palette.length], value: fmt.pct(values[i] / total) };
      }));
    }
  }

  // ---- Page building blocks: what dashboards and small systems kept
  // re-implementing — a searchable sortable table, a KPI row, tabs, toasts,
  // dialogs, saved state and mock data. Every call is opt-in, so a page that
  // brings its own versions keeps them.

  function resolve(target) {
    return typeof target === "string" ? document.querySelector(target) : target;
  }

  function node(tag, className, text) {
    var el = document.createElement(tag);
    if (className) el.className = className;
    if (text != null) el.textContent = text;
    return el;
  }

  function isNumberColumn(col) {
    return col.align === "right" || col.format === "num" || col.format === "brl" || col.format === "pct";
  }

  function cellText(col, row) {
    var value = row[col.key];
    if (value == null) return "";
    return col.format ? coerceFormat(col.format)(value) : String(value);
  }

  function compareValues(a, b) {
    if (typeof a === "number" && typeof b === "number") return a - b;
    return String(a == null ? "" : a).localeCompare(String(b == null ? "" : b), "pt-BR", { numeric: true });
  }

  // table(el, {columns, rows, search?, pageSize?, empty?, onRowClick?}) — a
  // table.shell-table with sortable headers, an optional search box and
  // pager. A column is {key, label, format?, align?, sortable? (true),
  // render?(value, row) returning a Node or an HTML string — the page writes
  // its cell templates as markup}. Plain values are always set as text.
  // Returns {setRows, rows}.
  function table(target, cfg) {
    var root = resolve(target);
    var cols = cfg.columns || [];
    var pageSize = cfg.pageSize || 0;
    var state = { rows: (cfg.rows || []).slice(), query: "", key: null, dir: 1, page: 0 };
    root.innerHTML = "";
    if (cfg.search) {
      var search = node("input", "input skip-table-search");
      search.type = "search";
      search.placeholder = typeof cfg.search === "string" ? cfg.search : "Buscar…";
      search.setAttribute("aria-label", search.placeholder);
      search.addEventListener("input", function () {
        state.query = search.value.trim().toLowerCase();
        state.page = 0;
        draw();
      });
      root.appendChild(search);
    }
    var tableEl = node("table", "shell-table");
    var headRow = node("tr");
    var heads = cols.map(function (col) {
      var th = node("th", isNumberColumn(col) ? "num" : "", col.label == null ? col.key : col.label);
      th.scope = "col";
      if (col.sortable !== false) {
        var toggle = function () {
          state.dir = state.key === col.key ? -state.dir : 1;
          state.key = col.key;
          draw();
        };
        th.setAttribute("data-sort", col.key);
        th.tabIndex = 0;
        th.addEventListener("click", toggle);
        th.addEventListener("keydown", function (e) {
          if (e.key === "Enter" || e.key === " ") { e.preventDefault(); toggle(); }
        });
      }
      headRow.appendChild(th);
      return th;
    });
    var thead = node("thead");
    var tbody = node("tbody");
    var wrap = node("div", "skip-table-wrap");
    var pager = node("div", "skip-pager");
    thead.appendChild(headRow);
    tableEl.appendChild(thead);
    tableEl.appendChild(tbody);
    wrap.appendChild(tableEl);
    root.appendChild(wrap);
    if (pageSize) root.appendChild(pager);

    function visibleRows() {
      var rows = state.rows;
      if (state.query) {
        rows = rows.filter(function (row) {
          return cols.some(function (col) { return cellText(col, row).toLowerCase().indexOf(state.query) >= 0; });
        });
      }
      if (state.key) {
        var key = state.key, dir = state.dir;
        rows = rows.slice().sort(function (a, b) { return dir * compareValues(a[key], b[key]); });
      }
      return rows;
    }

    function drawRow(row) {
      var tr = node("tr");
      cols.forEach(function (col) {
        var td = node("td", isNumberColumn(col) ? "num" : "");
        if (!col.render) {
          td.textContent = cellText(col, row);
        } else {
          var content = col.render(row[col.key], row);
          if (content instanceof Node) td.appendChild(content);
          else td.innerHTML = content == null ? "" : String(content);
        }
        tr.appendChild(td);
      });
      // The row stays a row (no role) and takes focus, so a keyboard reaches
      // the same action; keys pressed on a control inside a cell are its own.
      if (cfg.onRowClick) {
        tr.style.cursor = "pointer";
        tr.tabIndex = 0;
        tr.addEventListener("click", function () { cfg.onRowClick(row); });
        tr.addEventListener("keydown", function (e) {
          if (e.target !== tr || (e.key !== "Enter" && e.key !== " ")) return;
          e.preventDefault();
          cfg.onRowClick(row);
        });
      }
      return tr;
    }

    function pagerButton(label, disabled, step) {
      var button = node("button", "btn", label);
      button.type = "button";
      button.setAttribute("data-variant", "outline");
      button.setAttribute("data-size", "sm");
      button.disabled = disabled;
      button.addEventListener("click", function () { state.page += step; draw(); });
      return button;
    }

    function draw() {
      var rows = visibleRows();
      heads.forEach(function (th, i) {
        if (cols[i].key === state.key) th.setAttribute("aria-sort", state.dir > 0 ? "ascending" : "descending");
        else th.removeAttribute("aria-sort");
      });
      var pages = pageSize ? Math.max(1, Math.ceil(rows.length / pageSize)) : 1;
      state.page = Math.min(state.page, pages - 1);
      var shown = pageSize ? rows.slice(state.page * pageSize, (state.page + 1) * pageSize) : rows;
      tbody.innerHTML = "";
      if (!shown.length) {
        var empty = node("td", "skip-table-empty", cfg.empty || "Nenhum registro encontrado.");
        empty.colSpan = cols.length;
        tbody.appendChild(node("tr")).appendChild(empty);
      }
      shown.forEach(function (row) { tbody.appendChild(drawRow(row)); });
      if (!pageSize) return;
      pager.innerHTML = "";
      var from = rows.length ? state.page * pageSize + 1 : 0;
      pager.appendChild(node("span", "", from + "–" + Math.min(rows.length, (state.page + 1) * pageSize) + " de " + rows.length));
      var nav = node("div", "row gap-2");
      nav.appendChild(pagerButton("Anterior", state.page === 0, -1));
      nav.appendChild(pagerButton("Próxima", state.page >= pages - 1, 1));
      pager.appendChild(nav);
    }

    draw();
    return {
      setRows: function (rows) { state.rows = rows.slice(); draw(); },
      rows: visibleRows
    };
  }

  // kpis(el, [{label, value, format?, delta?, hint?}]) — KPI cards in a
  // responsive grid; delta is a fraction (0.12 renders as ▲ 12%).
  function kpis(target, items) {
    var root = resolve(target);
    root.innerHTML = "";
    root.classList.add("shell-grid");
    items.forEach(function (item) {
      var card = node("div", "panel kpi");
      card.appendChild(node("span", "kpi-label", item.label));
      // Large money values go compact ("R$ 27,5 mi"): the full amount does
      // not fit a KPI card at four per row.
      var kpiFormat = item.format === "brl" && Math.abs(item.value) >= 1e6 ? fmt.brlCompact : (item.format ? coerceFormat(item.format) : null);
      card.appendChild(node("span", "kpi-value", kpiFormat ? kpiFormat(item.value) : String(item.value)));
      if (typeof item.delta === "number") {
        var up = item.delta >= 0;
        card.appendChild(node("span", "kpi-delta " + (up ? "up" : "down"), (up ? "▲ " : "▼ ") + fmt.pct(Math.abs(item.delta))));
      }
      if (item.hint) card.appendChild(node("span", "kpi-label", item.hint));
      root.appendChild(card);
    });
  }

  // badge(text, variant?) — a .badge node for table cells and lists;
  // variant is "secondary" | "outline" | "destructive" (default: primary).
  function badge(text, variant) {
    var el = node("span", "badge", text);
    if (variant) el.setAttribute("data-variant", variant);
    return el;
  }

  // tabs(el) — wires one .tabs block: [role=tab] buttons inside
  // [role=tablist], each with aria-controls naming its [role=tabpanel].
  function tabs(target) {
    var root = resolve(target);
    var buttons = Array.prototype.slice.call(root.querySelectorAll('[role="tab"]'));
    function select(chosen) {
      buttons.forEach(function (b) {
        var on = b === chosen;
        b.setAttribute("aria-selected", on ? "true" : "false");
        b.tabIndex = on ? 0 : -1;
        var panel = document.getElementById(b.getAttribute("aria-controls"));
        if (panel) panel.hidden = !on;
      });
    }
    buttons.forEach(function (b, i) {
      b.addEventListener("click", function () { select(b); });
      b.addEventListener("keydown", function (e) {
        var step = e.key === "ArrowRight" ? 1 : e.key === "ArrowLeft" ? -1 : 0;
        if (!step) return;
        var next = buttons[(i + step + buttons.length) % buttons.length];
        next.focus();
        select(next);
      });
    });
    select(buttons.filter(function (b) { return b.getAttribute("aria-selected") === "true"; })[0] || buttons[0]);
  }

  // toast(message, {type?: "success" | "error", title?, duration?}) — a
  // .toast in a shared .toaster at the bottom of the page.
  function toast(message, opts) {
    opts = opts || {};
    var toaster = document.querySelector(".toaster") || document.body.appendChild(node("div", "toaster"));
    var item = node("div", "toast");
    item.setAttribute("role", opts.type === "error" ? "alert" : "status");
    item.setAttribute("aria-hidden", "true");
    if (opts.type) item.setAttribute("data-type", opts.type);
    var content = node("div", "toast-content");
    var section = node("section");
    if (opts.title) section.appendChild(node("h2", "", opts.title));
    section.appendChild(node("p", "", message));
    content.appendChild(section);
    item.appendChild(content);
    toaster.appendChild(item);
    requestAnimationFrame(function () { item.setAttribute("aria-hidden", "false"); });
    setTimeout(function () {
      item.setAttribute("aria-hidden", "true");
      setTimeout(function () { item.remove(); }, 400);
    }, opts.duration || 3000);
  }

  // Dialogs are native <dialog class="dialog">: a [data-dialog-open="id"]
  // anywhere opens one, a [data-dialog-close] inside closes it, and a click on
  // its backdrop closes it too. Plain dialog.showModal()/close() still work.
  document.addEventListener("click", function (e) {
    var target = e.target;
    if (!(target instanceof Element)) return;
    var opener = target.closest("[data-dialog-open]");
    if (opener) {
      var dialog = document.getElementById(opener.getAttribute("data-dialog-open"));
      if (dialog && dialog.showModal && !dialog.open) dialog.showModal();
      return;
    }
    var closer = target.closest("[data-dialog-close]");
    if (closer && closer.closest("dialog")) {
      closer.closest("dialog").close();
      return;
    }
    if (target.tagName === "DIALOG" && target.classList.contains("dialog") && target.open) target.close();
  });

  // store(key, fallback) — JSON state in localStorage that never throws (a
  // private window or a full quota falls back to memory): {get, set, update}.
  function store(key, fallback) {
    var memory;
    // Set while the last write did not reach localStorage: what is stored
    // there is older than memory until a write goes through again.
    var unsaved = false;
    var initial = function () { return fallback === undefined ? undefined : JSON.parse(JSON.stringify(fallback)); };
    function get() {
      if (!unsaved) {
        try {
          var raw = localStorage.getItem(key);
          if (raw != null) return JSON.parse(raw);
        } catch (e) { /* storage unavailable: memory below */ }
      }
      return memory !== undefined ? memory : initial();
    }
    function set(value) {
      memory = value;
      try {
        localStorage.setItem(key, JSON.stringify(value));
        unsaved = false;
      } catch (e) {
        unsaved = true;
      }
      return value;
    }
    return { get: get, set: set, update: function (fn) { return set(fn(get())); } };
  }

  // mock — seeded random data, so a page asks for 90 days of numbers in one
  // line instead of writing them out; the same seed gives the same data.
  var FIRST = ["Ana", "Bruno", "Carla", "Diego", "Eduarda", "Felipe", "Gabriela", "Henrique", "Isabela", "João",
    "Larissa", "Marcos", "Natália", "Otávio", "Paula", "Rafael", "Sofia", "Thiago", "Vanessa", "Lucas"];
  var LAST = ["Silva", "Santos", "Oliveira", "Souza", "Pereira", "Costa", "Rodrigues", "Almeida", "Nascimento", "Lima",
    "Araújo", "Fernandes", "Carvalho", "Gomes", "Martins", "Rocha", "Ribeiro", "Barbosa"];
  var INITIALS = "ABCDEFGHIJLMNOPRSTV".split("");
  var CITIES = ["São Paulo, SP", "Rio de Janeiro, RJ", "Belo Horizonte, MG", "Curitiba, PR", "Porto Alegre, RS",
    "Salvador, BA", "Recife, PE", "Fortaleza, CE", "Brasília, DF", "Goiânia, GO", "Campinas, SP", "Florianópolis, SC",
    "Manaus, AM", "Belém, PA", "Vitória, ES", "Natal, RN"];

  function createMock(seed) {
    var state = seed >>> 0;
    var names = 0;
    function random() {
      state = (state + 0x6d2b79f5) >>> 0;
      var t = state;
      t = Math.imul(t ^ (t >>> 15), t | 1);
      t ^= t + Math.imul(t ^ (t >>> 7), t | 61);
      return ((t ^ (t >>> 14)) >>> 0) / 4294967296;
    }
    function int(min, max) { return min + Math.floor(random() * (max - min + 1)); }
    function pick(list) { return list[Math.floor(random() * list.length)]; }
    var mock = {
      seed: function (value) { state = value >>> 0; names = 0; return mock; },
      random: random,
      int: int,
      float: function (min, max, decimals) {
        var factor = Math.pow(10, decimals == null ? 2 : decimals);
        return Math.round((min + random() * (max - min)) * factor) / factor;
      },
      pick: pick,
      chance: function (p) { return random() < p; },
      // There are 360 first/last pairs. A page that draws until the name is
      // new (do { … } while (used.has(name))) froze the tab past them, so
      // later draws widen the space: a second surname after 200 (6,480), a
      // middle initial after 4,000.
      name: function () {
        names++;
        var middle = names > 4000 ? pick(INITIALS) + ". " : "";
        return pick(FIRST) + " " + middle + (names > 200 ? pick(LAST) + " " : "") + pick(LAST);
      },
      city: function () { return pick(CITIES); },
      // series(n, {start, trend, noise, min, decimals}) — a walk: each value
      // moves by trend (fraction per step) plus up to ±noise of itself.
      series: function (n, opts) {
        opts = opts || {};
        var value = opts.start == null ? 100 : opts.start;
        var factor = Math.pow(10, opts.decimals || 0);
        var out = [];
        for (var i = 0; i < n; i++) {
          out.push(Math.max(opts.min == null ? 0 : opts.min, Math.round(value * factor) / factor));
          value = value * (1 + (opts.trend || 0)) * (1 + (random() * 2 - 1) * (opts.noise == null ? 0.08 : opts.noise));
        }
        return out;
      },
      // dates(n, {end?, step?: "day" | "week" | "month"}) — ISO dates
      // (YYYY-MM-DD), oldest first, ending at end (default: today).
      dates: function (n, opts) {
        opts = opts || {};
        var end = opts.end ? new Date(opts.end) : new Date();
        var out = [];
        for (var i = n - 1; i >= 0; i--) {
          var d = new Date(end.getTime());
          if (opts.step === "month") d.setMonth(d.getMonth() - i);
          else d.setDate(d.getDate() - i * (opts.step === "week" ? 7 : 1));
          out.push(d.toISOString().slice(0, 10));
        }
        return out;
      },
      // rows(n, spec) — n objects; each spec value is a function(i), a list
      // to pick from, or a constant.
      rows: function (n, spec) {
        var out = [];
        for (var i = 0; i < n; i++) {
          var row = {};
          for (var key in spec) {
            var value = spec[key];
            row[key] = typeof value === "function" ? value(i) : Array.isArray(value) ? pick(value) : value;
          }
          out.push(row);
        }
        return out;
      }
    };
    return mock;
  }

  window.skipShell = { fmt: fmt };
  window.skipChart = { bar: bar, line: line, donut: donut };
  window.skipUI = { table: table, kpis: kpis, badge: badge, tabs: tabs, toast: toast };
  window.skipStore = store;
  window.skipMock = createMock(20261022);
})();

</script>
<style>
/* ===== VARIÁVEIS ===== */
:root {
  --accent: #c6ff3d;
  --accent-text: #c6ff3d;
  --accent-contrast: #050505;
  --cyan: #00e5ff;
  --bg-0: #050505;
  --bg-1: #0a0a0c;
  --surface-1: #111114;
  --surface-2: #16161a;
  --border-subtle: #26262c;
  --text-main: #f5f5f7;
  --text-muted: #9a9aa5;
  --danger: #ff5c5c;
  --amber: #ffb020;
  --space-1: 0.5rem;
  --space-2: 1rem;
  --space-3: 1.5rem;
  --space-4: 2.5rem;
  --space-5: 4rem;
  --radius-lg: 18px;
  --font-display: 'Space Grotesk', 'Inter', system-ui, sans-serif;
  --font-body: 'Inter', system-ui, -apple-system, sans-serif;
  --header-h: 68px;
}

/* ===== BASE ===== */
*, *::before, *::after { box-sizing: border-box; }
html { scroll-behavior: smooth; scroll-padding-top: 90px; }
body {
  margin: 0;
  font-family: var(--font-body);
  background: var(--bg-0);
  color: var(--text-main);
  line-height: 1.6;
  overflow-x: hidden;
}
h1, h2, h3, h4 { font-family: var(--font-display); letter-spacing: -0.03em; line-height: 1.08; margin: 0; }
p { margin: 0; }
a { color: inherit; }
:focus-visible { outline: 2px solid var(--accent); outline-offset: 3px; border-radius: 4px; }
.sr-only { position: absolute; width: 1px; height: 1px; overflow: hidden; clip: rect(0 0 0 0); white-space: nowrap; }
.container { width: min(1180px, 100% - 2.5rem); margin-inline: auto; }
.section { position: relative; padding: clamp(4rem, 9vw, 7rem) 0; }
.section-head { text-align: center; max-width: 700px; margin: 0 auto var(--space-4); }
.section-head h2 { font-size: clamp(2rem, 4.6vw, 3.4rem); margin-top: var(--space-2); }
.section-head p { color: var(--text-muted); margin-top: var(--space-2); font-size: 1.05rem; }
.eyebrow {
  display: inline-flex; align-items: center; gap: .5rem;
  padding: .35rem .85rem; border-radius: 999px;
  border: 1px solid rgba(198,255,61,.3); background: rgba(198,255,61,.07);
  color: var(--accent); font-size: .78rem; font-weight: 600; letter-spacing: .04em; text-transform: uppercase;
}
.eyebrow::before { content: ""; width: 6px; height: 6px; border-radius: 50%; background: var(--accent); box-shadow: 0 0 10px var(--accent); }
.grad-text { background: linear-gradient(90deg, var(--accent), var(--cyan)); -webkit-background-clip: text; background-clip: text; color: var(--accent); -webkit-text-fill-color: transparent; }
.muted { color: var(--text-muted); }

/* Fundo tecnológico: grid + aurora */
.tech-grid {
  position: fixed; inset: 0; z-index: -2; pointer-events: none;
  background-image:
    linear-gradient(rgba(255,255,255,.035) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,.035) 1px, transparent 1px);
  background-size: 56px 56px;
  mask-image: radial-gradient(ellipse at 50% 0%, #000 30%, transparent 75%);
}
.aurora {
  position: absolute; inset: -20% -10% auto; height: 620px; z-index: -1; pointer-events: none;
  background:
    radial-gradient(40% 55% at 25% 30%, rgba(198,255,61,.16), transparent 70%),
    radial-gradient(35% 50% at 75% 20%, rgba(0,229,255,.13), transparent 70%);
  filter: blur(70px); opacity: .9; animation: drift 14s ease-in-out infinite alternate;
}
@keyframes drift { from { transform: translateX(-30px) scale(1); } to { transform: translateX(40px) scale(1.08); } }

/* Botões (usa shell .btn + ajustes de glow) */
.btn { transition: transform .2s, box-shadow .25s, background .2s; }
.btn:hover { transform: translateY(-1px); box-shadow: 0 0 24px rgba(198,255,61,.35); }
.btn[data-variant="outline"]:hover, .btn[data-variant="secondary"]:hover { box-shadow: 0 0 20px rgba(0,229,255,.25); }
.btn:disabled { opacity: .6; cursor: not-allowed; transform: none; box-shadow: none; }

/* Cards com borda luminosa no hover */
.glow-card {
  position: relative; background: linear-gradient(180deg, var(--surface-2), var(--surface-1));
  border: 1px solid var(--border-subtle); border-radius: var(--radius-lg);
  transition: transform .3s, border-color .3s, box-shadow .3s;
}
.glow-card::before {
  content: ""; position: absolute; inset: -1px; border-radius: inherit; padding: 1px;
  background: linear-gradient(135deg, var(--accent), transparent 40%, var(--cyan));
  -webkit-mask: linear-gradient(#000 0 0) content-box, linear-gradient(#000 0 0);
  -webkit-mask-composite: xor; mask-composite: exclude;
  opacity: 0; transition: opacity .3s; pointer-events: none;
}
.glow-card:hover { transform: translateY(-4px); box-shadow: 0 16px 50px -20px rgba(198,255,61,.35); }
.glow-card:hover::before { opacity: 1; }
.glass { background: rgba(17,17,20,.6); backdrop-filter: blur(14px); -webkit-backdrop-filter: blur(14px); border: 1px solid var(--border-subtle); }

/* Animação de entrada */
.reveal { opacity: 0; transform: translateY(28px); transition: opacity .8s ease, transform .8s cubic-bezier(.2,.7,.2,1); }
.reveal.is-visible { opacity: 1; transform: none; }

/* ===== HEADER ===== */
.progress-bar { position: fixed; top: 0; left: 0; height: 2px; width: 0; background: var(--accent); box-shadow: 0 0 10px var(--accent); z-index: 100; }
.site-header {
  position: fixed; top: 0; left: 0; right: 0; z-index: 90; height: var(--header-h);
  background: rgba(5,5,5,.7); backdrop-filter: blur(16px); -webkit-backdrop-filter: blur(16px);
  border-bottom: 1px solid var(--border-subtle);
}
.header-inner { height: 100%; display: flex; align-items: center; justify-content: space-between; gap: 1rem; }
.logo { display: inline-flex; align-items: center; gap: .6rem; text-decoration: none; }
.logo img { width: 40px; height: 40px; flex-shrink: 0; object-fit: cover; }
.site-footer .logo img { width: 48px; height: 48px; }
.wordmark { font-family: var(--font-display); font-weight: 700; font-size: 1.25rem; letter-spacing: .12em; }
.nav-links { display: flex; gap: 1.6rem; list-style: none; margin: 0; padding: 0; }
.nav-links a { text-decoration: none; color: var(--text-muted); font-size: .92rem; transition: color .2s; }
.nav-links a:hover { color: var(--text-main); }
.header-cta { display: flex; align-items: center; gap: .75rem; }
.menu-toggle {
  display: none; background: none; border: 1px solid var(--border-subtle); border-radius: 10px;
  width: 42px; height: 42px; color: var(--text-main); cursor: pointer; align-items: center; justify-content: center;
}
.mobile-nav {
  position: fixed; top: var(--header-h); left: 0; right: 0; z-index: 89;
  background: rgba(5,5,5,.97); backdrop-filter: blur(16px);
  border-bottom: 1px solid var(--border-subtle);
  transform: translateY(-120%); transition: transform .35s ease; padding: 1.5rem 1.25rem;
}
.mobile-nav.open { transform: none; }
.mobile-nav ul { list-style: none; margin: 0 0 1.25rem; padding: 0; display: grid; gap: .25rem; }
.mobile-nav a { display: block; padding: .8rem .25rem; text-decoration: none; border-bottom: 1px solid var(--border-subtle); color: var(--text-main); }
@media (max-width: 960px) {
  .nav-links, .header-cta .btn { display: none; }
  .menu-toggle { display: inline-flex; }
}

/* ===== HERO ===== */
.hero { min-height: 100vh; display: flex; align-items: center; padding: calc(var(--header-h) + 3rem) 0 4rem; position: relative; overflow: hidden; }
.hero-grid { display: grid; grid-template-columns: 1.05fr .95fr; gap: 3rem; align-items: center; }
.hero h1 { font-size: clamp(2.6rem, 6.4vw, 5rem); letter-spacing: -0.045em; font-weight: 700; margin: 1.25rem 0; }
.hero-sub { font-size: 1.1rem; color: var(--text-muted); max-width: 540px; }
.hero-actions { display: flex; flex-wrap: wrap; gap: .85rem; margin-top: 2rem; }
.hero-note { margin-top: 1.25rem; font-size: .82rem; color: var(--text-muted); }
.flow-visual { position: relative; width: 100%; aspect-ratio: 1 / 1; max-width: 520px; justify-self: center; }
.flow-visual svg { width: 100%; height: 100%; overflow: visible; }
.flow-line { stroke: rgba(198,255,61,.5); stroke-width: 1.5; fill: none; stroke-dasharray: 6 8; animation: dash 3s linear infinite; }
.flow-line.cyan { stroke: rgba(0,229,255,.5); animation-duration: 4.5s; }
@keyframes dash { to { stroke-dashoffset: -140; } }
.flow-node { fill: var(--surface-2); stroke: var(--border-subtle); stroke-width: 1.5; }
.flow-node-core { fill: rgba(198,255,61,.12); stroke: var(--accent); stroke-width: 1.5; filter: drop-shadow(0 0 12px rgba(198,255,61,.5)); }
.flow-pulse { fill: var(--accent); animation: pulse 2.4s ease-in-out infinite; transform-origin: center; }
@keyframes pulse { 0%,100% { opacity: .35; } 50% { opacity: 1; } }
.node-label { fill: var(--text-muted); font-family: var(--font-body); font-size: 12px; }
.node-label.strong { fill: var(--text-main); font-weight: 600; }
.hero-chip {
  position: absolute; padding: .5rem .8rem; border-radius: 12px; font-size: .78rem; white-space: nowrap;
  display: flex; align-items: center; gap: .45rem;
}
.hero-chip .dot { width: 7px; height: 7px; border-radius: 50%; background: var(--accent); box-shadow: 0 0 8px var(--accent); }
@media (max-width: 900px) {
  .hero-grid { grid-template-columns: 1fr; }
  .flow-visual { max-width: 420px; }
}

/* ===== NÚMEROS ===== */
.stats-band { border-block: 1px solid var(--border-subtle); background: rgba(10,10,12,.6); }
.stats-grid { display: grid; grid-template-columns: repeat(4, 1fr); }
.stat { padding: 2.5rem 1rem; text-align: center; border-inline-start: 1px solid var(--border-subtle); }
.stat:first-child { border-inline-start: none; }
.stat-value { font-family: var(--font-display); font-size: clamp(2.2rem, 4vw, 3.2rem); font-weight: 700; letter-spacing: -0.04em; color: var(--text-main); }
.stat-value .accent { color: var(--accent); }
.stat-label { color: var(--text-muted); font-size: .92rem; margin-top: .4rem; }
.stat-caption { font-size: .75rem; color: var(--text-muted); opacity: .75; margin-top: .25rem; }
@media (max-width: 800px) {
  .stats-grid { grid-template-columns: repeat(2, 1fr); }
  .stat:nth-child(3) { border-inline-start: none; }
  .stat:nth-child(n+3) { border-top: 1px solid var(--border-subtle); }
}

/* ===== SERVIÇOS ===== */
.services-grid { display: grid; grid-template-columns: repeat(6, 1fr); gap: 1.25rem; }
.service-card { grid-column: span 2; padding: 2rem; display: flex; flex-direction: column; gap: 1rem; }
.service-card.wide { grid-column: span 3; }
.service-icon {
  width: 52px; height: 52px; border-radius: 14px; display: grid; place-items: center;
  background: rgba(198,255,61,.09); border: 1px solid rgba(198,255,61,.25); color: var(--accent);
}
.service-icon svg { width: 26px; height: 26px; }
.service-card h3 { font-size: 1.45rem; }
.service-card .muted { font-size: .95rem; }
.service-list { list-style: none; padding: 0; margin: .25rem 0 .5rem; display: grid; gap: .5rem; font-size: .9rem; }
.service-list li { display: flex; gap: .6rem; align-items: flex-start; }
.service-list li::before { content: ""; width: 6px; height: 6px; margin-top: .55rem; border-radius: 50%; background: var(--cyan); box-shadow: 0 0 8px var(--cyan); flex-shrink: 0; }
.service-card .btn { margin-top: auto; align-self: flex-start; }
@media (max-width: 960px) {
  .services-grid { grid-template-columns: 1fr 1fr; }
  .service-card, .service-card.wide { grid-column: span 1; }
  .service-card:last-child:nth-child(odd) { grid-column: span 2; }
}
@media (max-width: 620px) {
  .services-grid { grid-template-columns: 1fr; }
  .service-card:last-child:nth-child(odd) { grid-column: span 1; }
}

/* ===== CUSTO DE NÃO AUTOMATIZAR ===== */
.cost-section { background: linear-gradient(180deg, transparent, rgba(255,92,92,.04) 50%, transparent); }
.pain-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.25rem; }
.pain-card { padding: 2rem; display: flex; flex-direction: column; gap: .8rem; }
.pain-number { font-family: var(--font-display); font-size: clamp(3rem, 5.4vw, 4.4rem); font-weight: 700; letter-spacing: -0.05em; line-height: 1; color: var(--danger); text-shadow: 0 0 30px rgba(255,92,92,.35); }
.pain-number.amber { color: var(--amber); text-shadow: 0 0 30px rgba(255,176,32,.3); }
.pain-card p { font-size: .98rem; }
.pain-source { font-size: .74rem; color: var(--text-muted); border-top: 1px dashed var(--border-subtle); padding-top: .7rem; margin-top: auto; }
.pain-note { text-align: center; font-size: .8rem; color: var(--text-muted); margin-top: 1.5rem; }
.cost-cta { margin-top: 3rem; padding: 2.5rem; display: flex; justify-content: space-between; align-items: center; gap: 2rem; flex-wrap: wrap; }
.cost-cta h3 { font-size: clamp(1.5rem, 3vw, 2.1rem); }
@media (max-width: 900px) { .pain-grid { grid-template-columns: 1fr 1fr; } }
@media (max-width: 600px) { .pain-grid { grid-template-columns: 1fr; } }

/* ===== COMO FUNCIONA ===== */
.timeline { position: relative; display: grid; grid-template-columns: repeat(4, 1fr); gap: 1.5rem; }
.timeline::before {
  content: ""; position: absolute; top: 28px; left: 12%; right: 12%; height: 2px;
  background: linear-gradient(90deg, var(--accent), var(--cyan));
  transform-origin: left; transform: scaleX(0); transition: transform 1.6s ease;
  box-shadow: 0 0 12px rgba(198,255,61,.4);
}
.timeline.is-visible::before { transform: scaleX(1); }
.step { text-align: center; padding: 0 .5rem; }
.step-num {
  width: 56px; height: 56px; margin: 0 auto 1.25rem; border-radius: 50%;
  display: grid; place-items: center; font-family: var(--font-display); font-weight: 700; font-size: 1.2rem;
  background: var(--surface-2); border: 1px solid var(--accent); color: var(--accent);
  box-shadow: 0 0 20px rgba(198,255,61,.25); position: relative; z-index: 1;
}
.step h3 { font-size: 1.2rem; margin-bottom: .5rem; }
.step p { color: var(--text-muted); font-size: .92rem; }
.step-time { display: inline-block; margin-top: .75rem; font-size: .75rem; color: var(--cyan); }
@media (max-width: 860px) {
  .timeline { grid-template-columns: 1fr 1fr; row-gap: 2.5rem; }
  .timeline::before { display: none; }
}
@media (max-width: 540px) { .timeline { grid-template-columns: 1fr; } }

/* ===== PLANOS ===== */
.billing-toggle { display: flex; justify-content: center; align-items: center; gap: .9rem; margin-bottom: 2.5rem; flex-wrap: wrap; }
.switch { position: relative; width: 56px; height: 30px; background: var(--surface-2); border: 1px solid var(--border-subtle); border-radius: 999px; cursor: pointer; transition: background .3s; }
.switch::after { content: ""; position: absolute; top: 3px; left: 3px; width: 22px; height: 22px; border-radius: 50%; background: var(--text-main); transition: transform .3s; }
.switch[aria-checked="true"] { background: rgba(198,255,61,.2); border-color: var(--accent); }
.switch[aria-checked="true"]::after { transform: translateX(26px); background: var(--accent); }
.plans-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 1.25rem; align-items: stretch; }
.plan { padding: 2.25rem 2rem; display: flex; flex-direction: column; }
.plan.featured { border-color: rgba(198,255,61,.5); box-shadow: 0 0 60px -15px rgba(198,255,61,.35); }
.plan-tag { position: absolute; top: -13px; left: 50%; transform: translateX(-50%); background: var(--accent); color: var(--accent-contrast); font-size: .75rem; font-weight: 700; padding: .3rem .85rem; border-radius: 999px; white-space: nowrap; }
.plan h3 { font-size: 1.5rem; }
.plan-desc { color: var(--text-muted); font-size: .92rem; margin-top: .4rem; min-height: 2.6em; }
.plan-price { margin: 1.5rem 0 .25rem; display: flex; align-items: baseline; gap: .35rem; }
.plan-price small { color: var(--text-muted); font-size: .85rem; }
.price-value { font-family: var(--font-display); font-size: 2.8rem; font-weight: 700; letter-spacing: -0.04em; transition: opacity .25s, transform .25s; display: inline-block; }
.price-value.swap { opacity: 0; transform: translateY(8px); }
.plan-caption { font-size: .78rem; color: var(--text-muted); min-height: 1.2em; }
.plan-features { list-style: none; padding: 0; margin: 1.5rem 0 2rem; display: grid; gap: .65rem; font-size: .92rem; }
.plan-features li { display: flex; gap: .6rem; }
.plan-features li::before { content: "✓"; color: var(--accent); font-weight: 700; }
.plan .btn { margin-top: auto; }
@media (max-width: 900px) { .plans-grid { grid-template-columns: 1fr; max-width: 480px; margin-inline: auto; } }

/* ===== ROI CALCULADORA ===== */
.calc-wrap { display: grid; grid-template-columns: 1fr 1fr; gap: 1.25rem; }
.calc-form { padding: 2rem; display: grid; gap: 1.1rem; }
.calc-form .field label { font-size: .9rem; font-weight: 500; }
.calc-form .field small { color: var(--text-muted); font-size: .78rem; }
.calc-result { padding: 2rem; display: flex; flex-direction: column; gap: .75rem; background: radial-gradient(circle at 80% 0%, rgba(198,255,61,.13), transparent 60%), var(--surface-1); }
.calc-label { font-size: .75rem; font-weight: 600; letter-spacing: .08em; text-transform: uppercase; color: var(--text-muted); }
.calc-value { font-family: var(--font-display); font-size: clamp(2.4rem, 4.6vw, 3.6rem); font-weight: 700; color: var(--accent); letter-spacing: -0.04em; }
.calc-breakdown { list-style: none; padding: 0; margin: .5rem 0 0; display: grid; gap: .5rem; font-size: .9rem; }
.calc-breakdown li { display: flex; justify-content: space-between; gap: 1rem; border-bottom: 1px dashed var(--border-subtle); padding-bottom: .4rem; }
@media (max-width: 860px) { .calc-wrap { grid-template-columns: 1fr; } }

/* ===== FAQ ===== */
.faq-list { max-width: 820px; margin: 0 auto; display: grid; gap: .75rem; }
.faq-item { border: 1px solid var(--border-subtle); border-radius: 14px; background: var(--surface-1); overflow: hidden; transition: border-color .3s; }
.faq-item.open { border-color: rgba(198,255,61,.4); }
.faq-q {
  width: 100%; background: none; border: 0; color: var(--text-main); text-align: left; cursor: pointer;
  padding: 1.25rem 1.4rem; display: flex; justify-content: space-between; align-items: center; gap: 1rem;
  font-family: var(--font-display); font-size: 1.05rem; font-weight: 600;
}
.faq-icon { width: 28px; height: 28px; flex-shrink: 0; border-radius: 50%; border: 1px solid var(--border-subtle); display: grid; place-items: center; transition: transform .35s, background .3s, border-color .3s; position: relative; }
.faq-icon::before, .faq-icon::after { content: ""; position: absolute; width: 10px; height: 2px; background: var(--accent); border-radius: 2px; transition: transform .35s; }
.faq-icon::after { transform: rotate(90deg); }
.faq-item.open .faq-icon { transform: rotate(180deg); background: rgba(198,255,61,.12); border-color: var(--accent); }
.faq-item.open .faq-icon::after { transform: rotate(0deg); }
.faq-a { display: grid; grid-template-rows: 0fr; transition: grid-template-rows .4s ease; }
.faq-item.open .faq-a { grid-template-rows: 1fr; }
.faq-a > div { overflow: hidden; }
.faq-a p { padding: 0 1.4rem 1.3rem; color: var(--text-muted); font-size: .95rem; }

/* ===== CONTATO ===== */
.contact-wrap { display: grid; grid-template-columns: .8fr 1.2fr; gap: 2.5rem; align-items: start; }
.contact-info h3 { font-size: 1.9rem; margin: 1rem 0 .75rem; }
.contact-info p { color: var(--text-muted); }
.contact-list { list-style: none; padding: 0; margin: 2rem 0 0; display: grid; gap: 1rem; }
.contact-list li { display: flex; gap: .75rem; align-items: center; font-size: .95rem; }
.contact-list svg { width: 20px; height: 20px; color: var(--accent); flex-shrink: 0; }
.contact-form { padding: 2.25rem; display: grid; gap: 1.1rem; }
.form-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 1rem; }
.form-grid .full { grid-column: 1 / -1; }
.field { display: grid; gap: .4rem; }
.field label { font-size: .88rem; font-weight: 500; }
.field .input, .field textarea, .field select {
  background: var(--bg-1); border-color: var(--border-subtle); color: var(--text-main);
}
.field fieldset { display: grid; gap: .6rem; }
.field legend { font-size: .88rem; font-weight: 500; margin-bottom: .2rem; }
.choice-grid { display: grid; grid-template-columns: repeat(2, minmax(0, 1fr)); gap: .65rem; }
.choice-grid label { display: flex; align-items: center; gap: .5rem; padding: .7rem .8rem; border: 1px solid var(--border-subtle); border-radius: 10px; cursor: pointer; }
.choice-grid label:has(input:checked) { border-color: var(--accent); background: rgba(198,255,61,.08); }
.choice-grid input { accent-color: var(--accent); }
.field .input:focus, .field textarea:focus, .field select:focus { border-color: var(--accent); box-shadow: 0 0 0 3px rgba(198,255,61,.15); outline: none; }
.field.invalid .input, .field.invalid textarea, .field.invalid select { border-color: var(--danger); }
.field-error { color: var(--danger); font-size: .78rem; min-height: 1em; }
.field-help { color: var(--text-muted); font-size: .78rem; }
.char-count { font-size: .75rem; color: var(--text-muted); text-align: right; }
.form-success { display: none; text-align: center; padding: 2rem 1rem; gap: .75rem; }
.form-success.show { display: grid; animation: fadeUp .6s ease; }
.check-circle { width: 72px; height: 72px; margin: 0 auto; border-radius: 50%; background: rgba(198,255,61,.12); border: 2px solid var(--accent); display: grid; place-items: center; box-shadow: 0 0 30px rgba(198,255,61,.35); }
.check-circle svg { width: 34px; height: 34px; color: var(--accent); stroke-dasharray: 40; stroke-dashoffset: 40; animation: draw .8s .2s forwards ease; }
@keyframes draw { to { stroke-dashoffset: 0; } }
@keyframes fadeUp { from { opacity: 0; transform: translateY(14px); } to { opacity: 1; transform: none; } }
.demo-notice { font-size: .78rem; color: var(--text-muted); text-align: center; }
@media (max-width: 860px) { .contact-wrap { grid-template-columns: 1fr; } }
@media (max-width: 560px) { .form-grid { grid-template-columns: 1fr; } }
@media (max-width: 560px) { .choice-grid { grid-template-columns: 1fr; } }

/* ===== CTA FINAL ===== */
.final-cta { position: relative; overflow: hidden; text-align: center; padding: clamp(4rem, 9vw, 6rem) 0; }
.final-cta-box { position: relative; border: 1px solid rgba(198,255,61,.3); border-radius: 26px; padding: clamp(2.5rem, 6vw, 4.5rem) 1.5rem; background: radial-gradient(60% 80% at 50% 0%, rgba(198,255,61,.18), transparent 70%), var(--surface-1); box-shadow: 0 0 120px -30px rgba(198,255,61,.5); }
.final-cta h2 { font-size: clamp(2rem, 4.8vw, 3.6rem); max-width: 820px; margin: 1rem auto; }
.final-cta p { color: var(--text-muted); max-width: 560px; margin: 0 auto 2rem; }

/* ===== FOOTER ===== */
.site-footer { border-top: 1px solid var(--border-subtle); padding: 4rem 0 2rem; background: var(--bg-1); }
.footer-grid { display: grid; grid-template-columns: 1.5fr 1fr 1fr 1fr; gap: 2.5rem; }
.footer-grid h4 { font-size: .95rem; margin-bottom: 1rem; }
.footer-grid ul { list-style: none; padding: 0; margin: 0; display: grid; gap: .6rem; }
.footer-grid a { text-decoration: none; color: var(--text-muted); font-size: .92rem; transition: color .2s; }
.footer-grid a:hover { color: var(--accent); }
.footer-desc { color: var(--text-muted); font-size: .92rem; max-width: 320px; margin: 1rem 0; }
.socials { display: flex; gap: .6rem; margin-top: 1rem; }
.social { position: relative; width: 40px; height: 40px; border-radius: 12px; border: 1px solid var(--border-subtle); display: grid; place-items: center; color: var(--text-muted); transition: all .25s; }
.social:hover, .social:focus-visible { color: var(--accent); border-color: var(--accent); box-shadow: 0 0 16px rgba(198,255,61,.25); }
.social svg { width: 18px; height: 18px; }
.social::after { content: attr(data-tip); position: absolute; bottom: calc(100% + 8px); left: 50%; transform: translateX(-50%) translateY(4px); background: var(--surface-2); border: 1px solid var(--border-subtle); color: var(--text-main); font-size: .72rem; padding: .3rem .6rem; border-radius: 8px; white-space: nowrap; opacity: 0; pointer-events: none; transition: all .2s; }
.social:hover::after, .social:focus-visible::after { opacity: 1; transform: translateX(-50%) translateY(0); }
.footer-bottom { margin-top: 3rem; padding-top: 1.5rem; border-top: 1px solid var(--border-subtle); display: flex; justify-content: space-between; flex-wrap: wrap; gap: 1rem; font-size: .82rem; color: var(--text-muted); }
.demo-banner { display: inline-block; padding: .3rem .7rem; border-radius: 999px; border: 1px solid rgba(0,229,255,.3); color: var(--cyan); font-size: .75rem; }
@media (max-width: 860px) { .footer-grid { grid-template-columns: 1fr 1fr; } }
@media (max-width: 520px) { .footer-grid { grid-template-columns: 1fr; } }

/* Voltar ao topo */
.back-to-top {
  position: fixed; right: 1.25rem; bottom: 1.25rem; z-index: 85; width: 46px; height: 46px; border-radius: 14px;
  border: 1px solid var(--accent); background: rgba(10,10,12,.85); color: var(--accent); cursor: pointer;
  display: grid; place-items: center; opacity: 0; transform: translateY(12px); pointer-events: none; transition: all .3s;
  box-shadow: 0 0 20px rgba(198,255,61,.25);
}
.back-to-top.show { opacity: 1; transform: none; pointer-events: auto; }
.back-to-top svg { width: 20px; height: 20px; }

/* Modal de serviços (dialog nativo) */
dialog.service-dialog { max-width: 620px; width: calc(100% - 2rem); }
.service-dialog .dialog-body { padding: 2rem; display: grid; gap: 1.25rem; }
.dialog-block h4 { font-size: .85rem; text-transform: uppercase; letter-spacing: .07em; color: var(--accent); margin-bottom: .4rem; font-family: var(--font-body); }
.dialog-block p { color: var(--text-muted); font-size: .95rem; }
.dialog-meta { display: grid; grid-template-columns: 1fr 1fr; gap: .75rem; }
.dialog-meta div { background: var(--bg-1); border: 1px solid var(--border-subtle); border-radius: 12px; padding: .9rem; }
.dialog-meta span { display: block; font-size: .75rem; color: var(--text-muted); }
.dialog-meta strong { font-size: .95rem; }
.service-dialog .dialog-foot { display: flex; justify-content: flex-end; gap: .6rem; padding: 0 2rem 1.75rem; }

/* Reduz movimento */
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after { animation: none !important; transition: none !important; }
  .reveal { opacity: 1; transform: none; }
}
</style>
</head>
<body>

<div class="tech-grid" aria-hidden="true"></div>
<div class="progress-bar" id="progressBar" aria-hidden="true"></div>

<!-- SEÇÃO: HEADER -->
<header class="site-header" id="top">
  <div class="container header-inner">
    <a href="#top" class="logo" aria-label="Westie — início">
      <img src="Imagemgerada_1793488455741.png" alt="Westie">
      <span class="wordmark">WESTIE</span>
    </a>

    <nav aria-label="Navegação principal">
      <ul class="nav-links">
        <li><a href="#solucoes">Soluções</a></li>
        <li><a href="#custo">O Custo de Não Automatizar</a></li>
        <li><a href="#como-funciona">Como Funciona</a></li>
        <li><a href="#planos">Planos</a></li>
        <li><a href="#contato">Contato</a></li>
      </ul>
    </nav>

    <div class="header-cta">
      <a href="#contato" class="btn">Falar com especialista</a>
      <button class="menu-toggle" id="menuToggle" aria-label="Abrir menu" aria-expanded="false" aria-controls="mobileNav">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><path d="M4 7h16M4 12h16M4 17h16"/></svg>
      </button>
    </div>
  </div>
</header>

<div class="mobile-nav" id="mobileNav">
  <ul>
    <li><a href="#solucoes">Soluções</a></li>
    <li><a href="#custo">O Custo de Não Automatizar</a></li>
    <li><a href="#como-funciona">Como Funciona</a></li>
    <li><a href="#planos">Planos</a></li>
    <li><a href="#contato">Contato</a></li>
  </ul>
  <a href="#contato" class="btn w-full">Falar com especialista</a>
</div>

<main>

<!-- SEÇÃO: HERO -->
<section class="hero" aria-labelledby="hero-title">
  <div class="aurora" aria-hidden="true"></div>
  <div class="container hero-grid">
    <div class="reveal">
      <span class="eyebrow">Automação com IA para negócios</span>
      <!-- EDITE: headline principal -->
      <h1 id="hero-title">Sua empresa não precisa de mais gente. <span class="grad-text">Precisa de mais automação.</span></h1>
      <!-- EDITE: subheadline -->
      <p class="hero-sub">Elimine tarefas repetitivas, responda seus clientes em segundos e não perca nenhuma oportunidade de venda, dia e noite, sem aumentar a equipe.</p>
      <div class="hero-actions">
        <a href="#solucoes" class="btn" data-size="lg">Ver o que automatizamos</a>
        <a href="#calculadora" class="btn" data-variant="outline" data-size="lg">Calcular minha perda</a>
      </div>
      <p class="hero-note">Diagnóstico inicial sem custo • Implantação em até 30 dias</p>
    </div>

    <div class="flow-visual reveal" aria-hidden="true">
      <!-- Visual abstrato de fluxo de automação: nós conectados com linhas animadas -->
      <svg viewBox="0 0 400 400">
        <path class="flow-line" d="M200 200 L90 90"/>
        <path class="flow-line cyan" d="M200 200 L310 90"/>
        <path class="flow-line" d="M200 200 L90 310"/>
        <path class="flow-line cyan" d="M200 200 L310 310"/>
        <path class="flow-line" d="M200 200 L200 40"/>
        <path class="flow-line cyan" d="M200 200 L200 360"/>
        <circle class="flow-node" cx="90" cy="90" r="22"/>
        <circle class="flow-node" cx="310" cy="90" r="22"/>
        <circle class="flow-node" cx="90" cy="310" r="22"/>
        <circle class="flow-node" cx="310" cy="310" r="22"/>
        <circle class="flow-node" cx="200" cy="40" r="18"/>
        <circle class="flow-node" cx="200" cy="360" r="18"/>
        <circle class="flow-node-core" cx="200" cy="200" r="46"/>
        <circle class="flow-pulse" cx="200" cy="200" r="6"/>
        <circle class="flow-pulse" cx="90" cy="90" r="4" style="animation-delay:.6s"/>
        <circle class="flow-pulse" cx="310" cy="310" r="4" style="animation-delay:1.2s"/>
        <text class="node-label strong" x="200" y="205" text-anchor="middle">IA</text>
        <text class="node-label" x="90" y="130" text-anchor="middle">WhatsApp</text>
        <text class="node-label" x="310" y="130" text-anchor="middle">Leads</text>
        <text class="node-label" x="90" y="255" text-anchor="middle">Lembretes</text>
        <text class="node-label" x="310" y="255" text-anchor="middle">Cobranças</text>
      </svg>
      <div class="hero-chip glass" style="top:6%; right:-4%;"><span class="dot"></span>Lead respondido em 4s</div>
      <div class="hero-chip glass" style="bottom:8%; left:-2%;"><span class="dot"></span>Agendamento confirmado</div>
    </div>
  </div>
</section>

<!-- SEÇÃO: FAIXA DE NÚMEROS -->
<section class="stats-band" aria-label="Indicadores de desempenho">
  <div class="container stats-grid">
    <div class="stat reveal">
      <div class="stat-value"><span class="accent" data-count="180">0</span>+</div>
      <div class="stat-label">processos automatizados</div>
      <div class="stat-caption">em operações reais de PMEs</div>
    </div>
    <div class="stat reveal">
      <div class="stat-value"><span data-count="24">0</span>/7</div>
      <div class="stat-label">operação sem pausa</div>
      <div class="stat-caption">atendimento e follow-up contínuos</div>
    </div>
    <div class="stat reveal">
      <div class="stat-value">-<span class="accent" data-count="73">0</span>%</div>
      <div class="stat-label">de tempo em tarefas manuais</div>
      <div class="stat-caption">média nos projetos entregues</div>
    </div>
    <div class="stat reveal">
      <div class="stat-value"><span class="accent" data-count="3">0</span>x</div>
      <div class="stat-label">mais leads respondidos</div>
      <div class="stat-caption">comparado ao atendimento manual</div>
    </div>
  </div>
</section>

<!-- SEÇÃO: O QUE AUTOMATIZAMOS -->
<section class="section" id="solucoes" aria-labelledby="sol-title">
  <div class="container">
    <div class="section-head reveal">
      <span class="eyebrow">Soluções</span>
      <!-- EDITE: título e subtítulo da seção -->
      <h2 id="sol-title">O que automatizamos</h2>
      <p>Cinco frentes que cobrem a jornada completa do cliente, da primeira mensagem ao pagamento.</p>
    </div>

    <div class="services-grid" id="servicesGrid">
      <!-- Os cards são renderizados a partir do array SERVICOS (// ===== MODAIS =====) -->
    </div>
  </div>
</section>

<!-- SEÇÃO: O CUSTO DE NÃO AUTOMATIZAR -->
<section class="section cost-section" id="custo" aria-labelledby="custo-title">
  <div class="container">
    <div class="section-head reveal">
      <span class="eyebrow">Diagnóstico de perdas</span>
      <!-- EDITE: título e subtítulo -->
      <h2 id="custo-title">Não automatizar custa mais caro do que automatizar.</h2>
      <p>Cada minuto de resposta lenta, cada lembrete esquecido e cada avaliação perdida é receita que sai pelo ralo.</p>
    </div>

    <div class="pain-grid">
      <article class="glow-card pain-card reveal">
        <div class="pain-number">78%</div>
        <p>dos clientes compram da empresa que responde primeiro.</p>
        <div class="pain-source">Fonte: Lead Connect / Harvard Business Review (estudo de tempo de resposta).</div>
      </article>
      <article class="glow-card pain-card reveal">
        <div class="pain-number">21x</div>
        <p>Uma resposta em até 5 minutos torna o lead até 21x mais propenso a converter; esperar 30 minutos reduz drasticamente essa chance.</p>
        <div class="pain-source">Fonte: Lead Response Management Study (InsideSales / MIT).</div>
      </article>
      <article class="glow-card pain-card reveal">
        <div class="pain-number amber">R$ 200–800</div>
        <p>Cada lead não atendido representa, em média, essa faixa de receita perdida para PMEs brasileiras.</p>
        <div class="pain-source">Estimativa de mercado (faixa indicativa, não um dado auditado).</div>
      </article>
      <article class="glow-card pain-card reveal">
        <div class="pain-number">20–30%</div>
        <p>de faltas em consultas e compromissos sem lembretes automatizados; lembretes reduzem esse número em até 40%.</p>
        <div class="pain-source">Fonte: estudos de no-show em serviços de saúde e serviços agendados.</div>
      </article>
      <article class="glow-card pain-card reveal">
        <div class="pain-number">93%</div>
        <p>dos consumidores leem avaliações online antes de comprar, e 91% confiam nelas tanto quanto em indicações pessoais.</p>
        <div class="pain-source">Fonte: BrightLocal.</div>
      </article>
      <article class="glow-card pain-card reveal">
        <div class="pain-number amber">-30%</div>
        <p>de atrasos de pagamento quando há automação de cobrança; empresas que perdem o timing aumentam a inadimplência.</p>
        <div class="pain-source">Estimativa de mercado (ordem de grandeza, não um dado auditado).</div>
      </article>
    </div>
    <p class="pain-note">Dados de estudos públicos de mercado. Resultados variam conforme o negócio.</p>

    <div class="glow-card cost-cta reveal">
      <div>
        <h3>Some tudo: quanto a sua empresa perde por mês?</h3>
        <p class="muted">Use a calculadora abaixo para estimar a sua perda mensal com base nos seus números.</p>
      </div>
      <a href="#contato" class="btn" data-size="lg">Falar com especialista</a>
    </div>
  </div>
</section>

<!-- SEÇÃO: COMO FUNCIONA -->
<section class="section" id="como-funciona" aria-labelledby="como-title">
  <div class="container">
    <div class="section-head reveal">
      <span class="eyebrow">Metodologia</span>
      <!-- EDITE: título das etapas -->
      <h2 id="como-title">Como funciona</h2>
      <p>Um processo em quatro etapas, com entregas visíveis a cada semana.</p>
    </div>
    <div class="timeline" id="timeline">
      <div class="step reveal">
        <div class="step-num">1</div>
        <h3>Diagnóstico dos processos</h3>
        <p>Mapeamos onde o tempo e a receita escorrem: atendimento, vendas, agenda e cobranças.</p>
        <span class="step-time">Semana 1</span>
      </div>
      <div class="step reveal">
        <div class="step-num">2</div>
        <h3>Desenho da automação</h3>
        <p>Definimos fluxos, regras de qualificação, mensagens e pontos de transferência para humanos.</p>
        <span class="step-time">Semana 2</span>
      </div>
      <div class="step reveal">
        <div class="step-num">3</div>
        <h3>Implantação e integração</h3>
        <p>Conectamos WhatsApp, CRM, agenda, e-mail e meios de pagamento ao seu sistema atual.</p>
        <span class="step-time">Semanas 3 e 4</span>
      </div>
      <div class="step reveal">
        <div class="step-num">4</div>
        <h3>Monitoramento e otimização</h3>
        <p>Painéis de desempenho, testes de mensagens e ajustes contínuos com base nos resultados.</p>
        <span class="step-time">Contínuo</span>
      </div>
    </div>
  </div>
</section>

<!-- SEÇÃO: PLANOS -->
<section class="section" id="planos" aria-labelledby="planos-title">
  <div class="container">
    <div class="section-head reveal">
      <span class="eyebrow">Planos</span>
      <!-- EDITE: título -->
      <h2 id="planos-title">Escolha o plano ideal</h2>
      <p>Valores de referência. Os preços são a partir de e podem variar conforme volume e integrações.</p>
    </div>

    <div class="billing-toggle">
      <span id="lblMensal" class="muted">Mensal</span>
      <button class="switch" id="billingSwitch" role="switch" aria-checked="false" aria-label="Alternar entre cobrança mensal e anual"></button>
      <span id="lblAnual">Anual <span class="badge" data-variant="secondary">-20%</span></span>
    </div>

    <div class="plans-grid" id="plansGrid">
      <!-- Renderizado a partir de PLANOS (// ===== PLANOS =====) -->
    </div>
  </div>
</section>

<!-- SEÇÃO: CALCULADORA DE PERDA -->
<section class="section" id="calculadora" aria-labelledby="calc-title">
  <div class="container">
    <div class="section-head reveal">
      <span class="eyebrow">Calculadora</span>
      <h2 id="calc-title">Calcular minha perda</h2>
      <p>Ajuste os números da sua operação. O resultado é uma estimativa ilustrativa.</p>
    </div>
    <div class="calc-wrap">
      <div class="glow-card calc-form reveal">
        <div class="field">
          <label for="leadsMes">Leads recebidos por mês</label>
          <input class="input" id="leadsMes" type="number" min="0" value="120" aria-describedby="h-leads">
          <small id="h-leads" class="field-help">Contatos novos vindos de site, anúncios e redes.</small>
        </div>
        <div class="field">
          <label for="taxaNaoAtendida">Leads sem resposta em até 5 min (%)</label>
          <input class="input" id="taxaNaoAtendida" type="number" min="0" max="100" value="45" aria-describedby="h-taxa">
          <small id="h-taxa" class="field-help">Estimativa de quantos não recebem resposta rápida.</small>
        </div>
        <div class="field">
          <label for="ticket">Ticket médio (R$)</label>
          <input class="input" id="ticket" type="number" min="0" value="650" aria-describedby="h-ticket">
          <small id="h-ticket" class="field-help">Valor médio de uma venda fechada.</small>
        </div>
        <div class="field">
          <label for="faltas">Compromissos por mês e taxa de falta (%)</label>
          <input class="input" id="faltas" type="number" min="0" max="100" value="22" aria-describedby="h-faltas">
          <small id="h-faltas" class="field-help">Percentual de faltas sem lembretes automatizados.</small>
        </div>
        <div class="row gap-2">
          <button class="btn" data-variant="outline" id="btnResetCalc" type="button">Restaurar exemplo</button>
          <button class="btn" data-variant="ghost" id="btnCopyCalc" type="button">Copiar resumo</button>
        </div>
      </div>

      <div class="calc-result reveal">
        <span class="calc-label">Perda mensal estimada</span>
        <div class="calc-value" id="calcTotal" aria-live="polite">R$ 0</div>
        <p class="muted" id="calcCaption">Valor aproximado com base nos dados informados.</p>
        <ul class="calc-breakdown">
          <li><span>Leads sem resposta rápida</span><strong id="bdLeads">R$ 0</strong></li>
          <li><span>Faltas em compromissos</span><strong id="bdFaltas">R$ 0</strong></li>
          <li><span>Oportunidades perdidas (estimativa)</span><strong id="bdOportunidades">R$ 0</strong></li>
        </ul>
        <p class="muted" style="font-size:.78rem; margin-top:.5rem;">Estimativa ilustrativa. Resultados variam conforme o negócio.</p>
      </div>
    </div>
  </div>
</section>

<!-- SEÇÃO: FAQ -->
<section class="section" id="faq" aria-labelledby="faq-title">
  <div class="container">
    <div class="section-head reveal">
      <span class="eyebrow">Dúvidas</span>
      <!-- EDITE: perguntas em FAQ_ITENS (// ===== FAQ =====) -->
      <h2 id="faq-title">Perguntas frequentes</h2>
      <p>Respostas rápidas para as dúvidas mais comuns antes da contratação.</p>
    </div>
    <div class="faq-list" id="faqList"></div>
  </div>
</section>

<!-- SEÇÃO: CONTATO -->
<section class="section" id="contato" aria-labelledby="contato-title">
  <div class="container contact-wrap">
    <div class="contact-info reveal">
      <span class="eyebrow">Contato</span>
      <h3 id="contato-title">Fale com um especialista</h3>
      <p>Conte um pouco sobre a sua operação e receba um diagnóstico inicial sem custo.</p>
      <ul class="contact-list">
        <li>
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><path d="M4 4h16v16H4z"/><path d="M4 6l8 6 8-6"/></svg>
          contato@westie.com.br
        </li>
        <li>
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/></svg>
          Resposta em até 1 dia útil
        </li>
        <li>
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 2"/></svg>
          Diagnóstico gratuito de 45 minutos
        </li>
      </ul>
    </div>

    <form class="glow-card contact-form reveal" id="contactForm" action="https://tiagobueno.app.n8n.cloud/webhook/westie-form" method="POST" novalidate>
      <input type="hidden" name="_subject" id="formSubject" value="">
      <input type="hidden" name="_replyto" id="formReplyTo" value="">
      <input type="hidden" name="_autoresponse" id="formAutoresponse" value="">
      <div id="formBody">
        <div class="form-grid">
          <div class="field" data-field="nome">
            <label for="fNome">Nome</label>
            <input class="input" id="fNome" name="nome" type="text" autocomplete="name" placeholder="Ex.: Ana Paula Ribeiro" required aria-describedby="e-nome">
            <span class="field-error" id="e-nome"></span>
          </div>
          <div class="field" data-field="email">
            <label for="fEmail">E-mail</label>
            <input class="input" id="fEmail" name="email" type="email" autocomplete="email" placeholder="voce@empresa.com.br" required aria-describedby="e-email">
            <span class="field-error" id="e-email"></span>
          </div>
          <div class="field" data-field="whatsapp">
            <label for="fWhats">WhatsApp</label>
            <input class="input" id="fWhats" name="whatsapp" type="tel" autocomplete="tel" placeholder="(11) 91234-5678" required aria-describedby="e-whats h-whats">
            <small id="h-whats" class="field-help">Com DDD. Usamos para o retorno do especialista.</small>
            <span class="field-error" id="e-whats"></span>
          </div>
          <div class="field" data-field="empresa">
            <label for="fEmpresa">Empresa</label>
            <input class="input" id="fEmpresa" name="empresa" type="text" autocomplete="organization" placeholder="Ex.: Clínica Vida Plena" required aria-describedby="e-empresa">
            <span class="field-error" id="e-empresa"></span>
          </div>
          <div class="field full" data-field="servicos">
            <fieldset>
              <legend>O que você quer automatizar?</legend>
              <div class="choice-grid">
                <label><input type="checkbox" name="servico_1" value="Leads" data-service-option> Leads</label>
                <label><input type="checkbox" name="servico_2" value="Chatbot com WhatsApp" data-service-option> Chatbot com WhatsApp</label>
                <label><input type="checkbox" name="servico_3" value="Lembretes" data-service-option> Lembretes</label>
                <label><input type="checkbox" name="servico_4" value="Avaliações" data-service-option> Avaliações</label>
                <label><input type="checkbox" name="servico_5" value="Transações" data-service-option> Transações</label>
              </div>
            </fieldset>
            <span class="field-error" id="e-servicos"></span>
          </div>
          <div class="field full" data-field="mensagem">
            <label for="fMsg">Mensagem</label>
            <textarea class="input" id="fMsg" name="mensagem" rows="4" maxlength="500" placeholder="Ex.: Recebo muitos leads por Instagram e demoro horas para responder." aria-describedby="e-msg c-msg"></textarea>
            <div class="row between">
              <span class="field-error" id="e-msg"></span>
              <span class="char-count" id="c-msg">0/500</span>
            </div>
          </div>
        </div>
        <div class="row between" style="margin-top:1.25rem;">
          <span class="demo-notice">Suas respostas serão enviadas com segurança.</span>
          <button class="btn" type="submit" id="submitBtn" data-size="lg">Enviar mensagem</button>
        </div>
      </div>
      <div class="form-success" id="formSuccess" role="status" aria-live="polite">
        <div class="check-circle">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12l5 5L20 7"/></svg>
        </div>
        <h3>Recebemos sua mensagem!</h3>
        <p class="muted">Enviamos uma confirmação para o seu e-mail. Um especialista entrará em contato em até 1 dia útil.</p>
        <button class="btn" data-variant="outline" type="button" id="resetForm">Enviar outra mensagem</button>
      </div>
    </form>
  </div>
</section>

<!-- SEÇÃO: CTA FINAL -->
<section class="final-cta" aria-labelledby="cta-title">
  <div class="container">
    <div class="final-cta-box reveal">
      <span class="eyebrow">Próximo passo</span>
      <h2 id="cta-title">Pronto para parar de perder dinheiro com tarefas manuais?</h2>
      <p>Um diagnóstico gratuito mostra onde está a maior perda da sua operação e o que automatizar primeiro.</p>
      <a href="#contato" class="btn" data-size="lg">Agendar diagnóstico gratuito</a>
    </div>
  </div>
</section>

</main>

<!-- SEÇÃO: FOOTER -->
<footer class="site-footer">
  <div class="container">
    <div class="footer-grid">
      <div>
        <a href="#top" class="logo" aria-label="Westie — voltar ao topo">
          <img src="Imagemgerada_1793488455741.png" alt="Westie">
          <span class="wordmark">WESTIE</span>
        </a>
        <p class="footer-desc">Automações com IA para pequenos e médios negócios brasileiros. Atendimento, vendas, agenda e cobranças funcionando sem pausa.</p>
        <div class="socials">
          <a class="social" href="#" data-tip="Instagram" aria-label="Instagram da Westie">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><rect x="3" y="3" width="18" height="18" rx="5"/><circle cx="12" cy="12" r="4"/><circle cx="17.5" cy="6.5" r="1" fill="currentColor"/></svg>
          </a>
          <a class="social" href="#" data-tip="LinkedIn" aria-label="LinkedIn da Westie">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><rect x="3" y="3" width="18" height="18" rx="3"/><path d="M8 11v5M8 8v.01M12 16v-5m0 2a2 2 0 0 1 4 0v3"/></svg>
          </a>
          <a class="social" href="#" data-tip="YouTube" aria-label="YouTube da Westie">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><rect x="2" y="5" width="20" height="14" rx="4"/><path d="M10 9l5 3-5 3z"/></svg>
          </a>
          <a class="social" href="#" data-tip="WhatsApp" aria-label="WhatsApp da Westie">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><path d="M21 12a9 9 0 0 1-13.4 7.8L3 21l1.3-4.4A9 9 0 1 1 21 12z"/></svg>
          </a>
        </div>
      </div>
      <div>
        <h4>Soluções</h4>
        <ul>
          <li><a href="#solucoes">Leads</a></li>
          <li><a href="#solucoes">Chatbot com WhatsApp</a></li>
          <li><a href="#solucoes">Lembretes</a></li>
          <li><a href="#solucoes">Avaliações</a></li>
          <li><a href="#solucoes">Transações</a></li>
        </ul>
      </div>
      <div>
        <h4>Empresa</h4>
        <ul>
          <li><a href="#custo">O Custo de Não Automatizar</a></li>
          <li><a href="#como-funciona">Como Funciona</a></li>
          <li><a href="#planos">Planos</a></li>
          <li><a href="#faq">Dúvidas</a></li>
        </ul>
      </div>
      <div>
        <h4>Contato</h4>
        <ul>
          <li><a href="mailto:contato@westie.com.br">contato@westie.com.br</a></li>
          <li><a href="#contato">Falar com especialista</a></li>
          <li><a href="#calculadora">Calcular minha perda</a></li>
        </ul>
      </div>
    </div>
    <div class="footer-bottom">
      <span>© 2025 Westie Automações Ltda. Todos os direitos reservados.</span>
      <span class="demo-banner">Site de demonstração — nenhum dado real é coletado</span>
    </div>
  </div>
</footer>

<button class="back-to-top" id="backToTop" aria-label="Voltar ao topo">
  <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><path d="M12 19V5M5 12l7-7 7 7"/></svg>
</button>

<!-- Modal de detalhes dos serviços -->
<dialog class="dialog service-dialog" id="serviceDialog" aria-labelledby="svcDialogTitle">
  <div>
    <header>
      <h2 id="svcDialogTitle">Serviço</h2>
      <p id="svcDialogSub" class="muted"></p>
    </header>
    <div class="dialog-body" id="svcDialogBody"></div>
    <div class="dialog-foot">
      <button class="btn" data-variant="outline" type="button" data-dialog-close>Fechar</button>
      <a href="#contato" class="btn" data-dialog-close id="svcDialogCta">Falar sobre isso</a>
    </div>
  </div>
</dialog>

<script>
/* ===== DADOS: SERVIÇOS ===== */
// ===== MODAIS =====
const SERVICOS = [
  {
    id: 'leads', titulo: 'Leads', wide: false,
    icone: '<path d="M4 6h16M7 12h10M10 18h4"/>',
    resumo: 'Captura e qualificação automática de leads de múltiplos canais, com distribuição inteligente e follow-up automático.',
    itens: ['Captura de site, formulários, anúncios e redes sociais', 'Qualificação por regras e pontuação automática', 'Distribuição para o vendedor certo e follow-up contínuo'],
    como: 'Os formulários, anúncios e mensagens entram em uma fila única. Cada lead recebe pontuação, é atribuído ao vendedor disponível e entra em uma sequência de contatos até responder.',
    resultado: 'Resposta em segundos e mais leads qualificados chegando ao time comercial.',
    prazo: '10 a 15 dias'
  },
  {
    id: 'chatbot', titulo: 'Chatbot com WhatsApp', wide: false,
    icone: '<path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/>',
    resumo: 'Atendimento automatizado 24/7 no WhatsApp: respostas instantâneas, qualificação, agendamento e transferência para humano.',
    itens: ['Respostas instantâneas com base na sua base de conhecimento', 'Qualificação e agendamento na própria conversa', 'Transferência para humano quando necessário'],
    como: 'Um assistente de IA responde perguntas frequentes, coleta dados do cliente e agenda horários na sua agenda. Assuntos complexos são transferidos para um atendente com todo o histórico.',
    resultado: 'Atendimento sem fila, mesmo fora do horário comercial.',
    prazo: '15 a 25 dias'
  },
  {
    id: 'lembretes', titulo: 'Lembretes', wide: false,
    icone: '<circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 2"/>',
    resumo: 'Lembretes automáticos de consultas, reuniões, pagamentos e prazos por WhatsApp, e-mail e SMS.',
    itens: ['Envio em múltiplos canais no momento ideal', 'Confirmação e reagendamento com um toque', 'Relatório de faltas e confirmações'],
    como: 'Sua agenda dispara lembretes em janelas configuradas. O cliente confirma, reagenda ou cancela pela própria mensagem, e a agenda é atualizada automaticamente.',
    resultado: 'Menos faltas e agenda sempre atualizada.',
    prazo: '7 a 12 dias'
  },
  {
    id: 'avaliacoes', titulo: 'Avaliações', wide: false,
    icone: '<path d="M12 3l2.9 5.9 6.5.9-4.7 4.6 1.1 6.5L12 17.8 6.2 20.9l1.1-6.5-4.7-4.6 6.5-.9z"/>',
    resumo: 'Coleta automática de avaliações no Google e redes sociais após cada atendimento, com gestão de reputação.',
    itens: ['Solicitação no momento ideal após o atendimento', 'Direcionamento para Google e redes sociais', 'Alertas de avaliações negativas para tratamento'],
    como: 'Ao concluir um atendimento, o sistema aguarda o intervalo definido e envia um pedido de avaliação. Notas baixas viram alerta interno antes de chegarem ao público.',
    resultado: 'Mais avaliações recentes e reputação monitorada.',
    prazo: '5 a 10 dias'
  },
  {
    id: 'transacoes', titulo: 'Transações', wide: true,
    icone: '<rect x="2" y="5" width="20" height="14" rx="3"/><path d="M2 10h20"/>',
    resumo: 'Conciliação e acompanhamento automático de pagamentos, cobranças recorrentes, emissão de recibos e alertas de falha.',
    itens: ['Conciliação automática de pagamentos recebidos', 'Cobranças recorrentes e lembretes de vencimento', 'Emissão de recibos e alertas de falha em transações'],
    como: 'Pagamentos são conciliados com as vendas automaticamente. Cobranças são disparadas antes e depois do vencimento, com recibos enviados ao cliente e alertas de falha para a equipe financeira.',
    resultado: 'Menos inadimplência por esquecimento e financeiro sem planilhas manuais.',
    prazo: '12 a 20 dias'
  }
];

function renderServicos() {
  const grid = document.getElementById('servicesGrid');
  grid.innerHTML = SERVICOS.map(s => `
    <article class="glow-card service-card reveal ${s.wide ? 'wide' : ''}">
      <div class="service-icon" aria-hidden="true">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.8" stroke-linecap="round" stroke-linejoin="round">${s.icone}</svg>
      </div>
      <h3>${s.titulo}</h3>
      <p class="muted">${s.resumo}</p>
      <ul class="service-list">${s.itens.map(i => `<li>${i}</li>`).join('')}</ul>
      <button class="btn" data-variant="outline" data-size="sm" type="button" data-service="${s.id}" aria-label="Saber mais sobre ${s.titulo}">Saber mais</button>
    </article>
  `).join('');
}

/* ===== PLANOS ===== */
const PLANOS = [
  {
    nome: 'Starter', desc: 'Para negócios que estão começando a automatizar.',
    mensal: 1490, anual: null, cta: 'Começar com Starter', destaque: false,
    recursos: ['Até 2 fluxos automatizados', 'Chatbot com WhatsApp (1 número)', 'Lembretes por WhatsApp e e-mail', 'Painel de desempenho básico']
  },
  {
    nome: 'Growth', desc: 'Para times que querem escalar atendimento e vendas.',
    mensal: 2990, anual: null, cta: 'Escolher Growth', destaque: true,
    recursos: ['Fluxos ilimitados', 'Captura multicanal de leads', 'Chatbot com IA e transferência humana', 'Avaliações e cobranças automatizadas', 'Integração com CRM e agenda']
  },
  {
    nome: 'Enterprise', desc: 'Para operações com volume e exigências específicas.',
    mensal: null, anual: null, cta: 'Falar com especialista', destaque: false,
    recursos: ['Tudo do Growth', 'Integrações sob medida', 'SLA dedicado e gerente de conta', 'Segurança e governança avançadas']
  }
];

let billingAnual = false;
const DESCONTO_ANUAL = 0.2;

function formatPreco(valor) {
  return 'R$ ' + valor.toLocaleString('pt-BR', { minimumFractionDigits: 0, maximumFractionDigits: 0 });
}

function renderPlanos() {
  const grid = document.getElementById('plansGrid');
  grid.innerHTML = PLANOS.map((p, i) => `
    <article class="glow-card plan reveal ${p.destaque ? 'featured' : ''}">
      ${p.destaque ? '<span class="plan-tag">Mais escolhido</span>' : ''}
      <h3>${p.nome}</h3>
      <p class="plan-desc">${p.desc}</p>
      <div class="plan-price">
        ${p.mensal === null
          ? '<span class="price-value" data-plan="' + i + '">Sob consulta</span>'
          : '<small>a partir de</small><span class="price-value" data-plan="' + i + '">' + formatPreco(p.mensal) + '</span><small>/mês</small>'}
      </div>
      <p class="plan-caption" data-caption="${i}">${p.mensal === null ? 'Condições personalizadas' : (billingAnual ? 'Cobrado anualmente' : 'Cobrado mensalmente')}</p>
      <ul class="plan-features">${p.recursos.map(r => `<li>${r}</li>`).join('')}</ul>
      <button class="btn" ${p.destaque ? '' : 'data-variant="outline"'} type="button" data-plan-cta="${p.nome}">${p.cta}</button>
    </article>
  `).join('');
}

function atualizarPrecos() {
  PLANOS.forEach((p, i) => {
    if (p.mensal === null) return;
    const el = document.querySelector(`[data-plan="${i}"]`);
    const cap = document.querySelector(`[data-caption="${i}"]`);
    const valor = billingAnual ? Math.round(p.mensal * (1 - DESCONTO_ANUAL)) : p.mensal;
    el.classList.add('swap');
    cap.textContent = billingAnual ? 'Cobrado anualmente' : 'Cobrado mensalmente';
    setTimeout(() => {
      el.textContent = formatPreco(valor);
      el.classList.remove('swap');
    }, 250);
  });
}

function setupBillingToggle() {
  const sw = document.getElementById('billingSwitch');
  const lblM = document.getElementById('lblMensal');
  const lblA = document.getElementById('lblAnual');
  sw.addEventListener('click', () => {
    billingAnual = !billingAnual;
    sw.setAttribute('aria-checked', String(billingAnual));
    lblM.classList.toggle('muted', billingAnual);
    atualizarPrecos();
  });
  sw.addEventListener('keydown', e => {
    if (e.key === ' ' || e.key === 'Enter') { e.preventDefault(); sw.click(); }
  });
  lblM.addEventListener('click', () => { if (billingAnual) sw.click(); });
  lblA.addEventListener('click', () => { if (!billingAnual) sw.click(); });
}

/* ===== FAQ ===== */
// EDITE: perguntas e respostas
const FAQ_ITENS = [
  { q: 'Preciso saber programar?', a: 'Não. Nós desenhamos, implantamos e mantemos as automações. Você acompanha os resultados em um painel simples e recebe treinamento para a equipe.' },
  { q: 'Funciona com meu sistema atual?', a: 'Na maioria dos casos, sim. Conectamos WhatsApp, CRM, agenda, e-mail e meios de pagamento mais usados no Brasil. Antes de qualquer contrato, validamos a integração no diagnóstico.' },
  { q: 'Quanto tempo leva a implantação?', a: 'Depende da complexidade. Um fluxo simples pode ficar pronto em 7 a 12 dias. Operações com várias integrações costumam levar de 3 a 4 semanas, com entregas visíveis a cada semana.' },
  { q: 'E se o chatbot não souber responder?', a: 'Ele reconhece quando não tem segurança na resposta e transfere a conversa para um atendente humano, com todo o histórico, para que o cliente não precise repetir nada.' },
  { q: 'Meus dados ficam seguros?', a: 'Sim. Os dados são criptografados em trânsito e em repouso, o acesso é controlado por perfil e seguimos a LGPD. Você pode solicitar a exclusão de dados a qualquer momento.' },
  { q: 'Posso cancelar quando quiser?', a: 'Sim. Os planos mensais podem ser cancelados a qualquer momento, sem multa. No plano anual, as condições de cancelamento constam no contrato e são explicadas antes da assinatura.' }
];

function renderFaq() {
  const list = document.getElementById('faqList');
  list.innerHTML = FAQ_ITENS.map((item, i) => `
    <div class="faq-item reveal" data-idx="${i}">
      <button class="faq-q" type="button" aria-expanded="false" aria-controls="faq-a-${i}" id="faq-q-${i}">
        <span>${item.q}</span>
        <span class="faq-icon" aria-hidden="true"></span>
      </button>
      <div class="faq-a" id="faq-a-${i}" role="region" aria-labelledby="faq-q-${i}">
        <div><p>${item.a}</p></div>
      </div>
    </div>
  `).join('');

  list.querySelectorAll('.faq-q').forEach(btn => {
    btn.addEventListener('click', () => {
      const item = btn.closest('.faq-item');
      const abrir = !item.classList.contains('open');
      list.querySelectorAll('.faq-item').forEach(it => {
        it.classList.remove('open');
        it.querySelector('.faq-q').setAttribute('aria-expanded', 'false');
      });
      if (abrir) {
        item.classList.add('open');
        btn.setAttribute('aria-expanded', 'true');
      }
    });
  });
}

/* ===== CALCULADORA DE PERDA ===== */
// Usa dados informados pelo usuário. Valores exibidos como estimativa ilustrativa.
function setupCalculadora() {
  const ids = ['leadsMes', 'taxaNaoAtendida', 'ticket', 'faltas'];
  const exemplo = { leadsMes: 120, taxaNaoAtendida: 45, ticket: 650, faltas: 22 };
  const fmt = n => 'R$ ' + Math.round(n).toLocaleString('pt-BR');

  function calcular() {
    const leads = Math.max(0, +document.getElementById('leadsMes').value || 0);
    const taxa = Math.min(100, Math.max(0, +document.getElementById('taxaNaoAtendida').value || 0)) / 100;
    const ticket = Math.max(0, +document.getElementById('ticket').value || 0);
    const faltas = Math.min(100, Math.max(0, +document.getElementById('faltas').value || 0)) / 100;

    const leadsPerdidos = leads * taxa;
    const perdaLeads = leadsPerdidos * ticket * 0.1;
    const compromissos = leads * 0.6;
    const perdaFaltas = compromissos * faltas * ticket * 0.5;
    const oportunidades = leadsPerdidos * 0.15 * ticket;
    const total = perdaLeads + perdaFaltas + oportunidades;

    document.getElementById('calcTotal').textContent = fmt(total);
    document.getElementById('bdLeads').textContent = fmt(perdaLeads);
    document.getElementById('bdFaltas').textContent = fmt(perdaFaltas);
    document.getElementById('bdOportunidades').textContent = fmt(oportunidades);
    document.getElementById('calcCaption').textContent =
      `Equivale a cerca de ${fmt(total * 12)} por ano. Estimativa com base nos dados informados.`;
    return { total, perdaLeads, perdaFaltas, oportunidades };
  }

  ids.forEach(id => document.getElementById(id).addEventListener('input', calcular));

  document.getElementById('btnResetCalc').addEventListener('click', () => {
    ids.forEach(id => document.getElementById(id).value = exemplo[id]);
    calcular();
    window.skipUI.toast('Exemplo restaurado.');
  });

  document.getElementById('btnCopyCalc').addEventListener('click', () => {
    const r = calcular();
    const txt = `Perda mensal estimada: ${fmt(r.total)} (leads sem resposta: ${fmt(r.perdaLeads)}, faltas: ${fmt(r.perdaFaltas)}, oportunidades: ${fmt(r.oportunidades)}). Estimativa ilustrativa.`;
    navigator.clipboard?.writeText(txt).catch(() => {});
    window.skipUI.toast('Resumo copiado para a área de transferência.', { type: 'success' });
  });

  calcular();
}

/* ===== MODAIS (serviços) ===== */
function setupModais() {
  const dlg = document.getElementById('serviceDialog');
  let scrollY = 0;

  function abrir(id) {
    const s = SERVICOS.find(x => x.id === id);
    if (!s) return;
    document.getElementById('svcDialogTitle').textContent = s.titulo;
    document.getElementById('svcDialogSub').textContent = s.resumo;
    document.getElementById('svcDialogBody').innerHTML = `
      <div class="dialog-block"><h4>Como funciona</h4><p>${s.como}</p></div>
      <div class="dialog-block"><h4>Resultado esperado</h4><p>${s.resultado}</p></div>
      <div class="dialog-meta">
        <div><span>Tempo de implantação</span><strong>${s.prazo}</strong></div>
        <div><span>Inclui</span><strong>${s.itens.length} entregas principais</strong></div>
      </div>`;
    scrollY = window.scrollY;
    document.body.style.position = 'fixed';
    document.body.style.top = `-${scrollY}px`;
    document.body.style.width = '100%';
    dlg.showModal();
  }

  dlg.addEventListener('close', () => {
    document.body.style.position = '';
    document.body.style.top = '';
    document.body.style.width = '';
    window.scrollTo(0, scrollY);
  });

  dlg.addEventListener('click', e => { if (e.target === dlg) dlg.close(); });

  document.getElementById('servicesGrid').addEventListener('click', e => {
    const btn = e.target.closest('[data-service]');
    if (btn) abrir(btn.dataset.service);
  });
}

/* ===== FORMULÁRIO ===== */
function setupFormulario() {
  const form = document.getElementById('contactForm');
  const body = document.getElementById('formBody');
  const success = document.getElementById('formSuccess');
  const msg = document.getElementById('fMsg');
  const counter = document.getElementById('c-msg');

  function prepararEmail(value) {
    return value.trim();
  }

  function prepararNome(value) {
    return value.trim();
  }

  const opcoesServico = () => Array.from(form.querySelectorAll('input[data-service-option]'));

  const regras = {
    nome: v => v.trim().length >= 3 || 'Informe seu nome completo (mín. 3 caracteres).',
    email: v => /^[^\s@]+@[^\s@]+\.[^\s@]{2,}$/.test(v.trim()) || 'Informe um e-mail válido.',
    whatsapp: v => v.replace(/\D/g, '').length >= 10 || 'Informe um WhatsApp com DDD.',
    empresa: v => v.trim().length >= 2 || 'Informe o nome da empresa.',
    servicos: () => opcoesServico().some(input => input.checked) || 'Escolha pelo menos um serviço.',
    mensagem: v => v.trim().length <= 500 || 'Máximo de 500 caracteres.'
  };

  function validarCampo(name) {
    const input = name === 'servicos' ? opcoesServico()[0] : form.elements[name];
    const field = form.querySelector(`[data-field="${name}"]`);
    const erro = document.getElementById('e-' + (name === 'servicos' ? 'servicos' : name === 'mensagem' ? 'msg' : name === 'whatsapp' ? 'whats' : name));
    const res = regras[name](name === 'servicos' ? '' : input.value);
    const ok = res === true;
    field.classList.toggle('invalid', !ok);
    if (name !== 'servicos') input.setAttribute('aria-invalid', String(!ok));
    erro.textContent = ok ? '' : res;
    return ok;
  }

  Object.keys(regras).forEach(name => {
    const inputs = name === 'servicos'
      ? opcoesServico()
      : [form.elements[name]];
    inputs.forEach(input => {
      input.addEventListener('blur', () => validarCampo(name));
      input.addEventListener('change', () => validarCampo(name));
      input.addEventListener('input', () => {
        if (form.querySelector(`[data-field="${name}"]`).classList.contains('invalid')) validarCampo(name);
      });
    });
  });

  msg.addEventListener('input', () => {
    counter.textContent = `${msg.value.length}/500`;
  });

  form.addEventListener('submit', e => {
    e.preventDefault();
    const ok = Object.keys(regras).map(validarCampo).every(Boolean);
    if (!ok) {
      window.skipUI.toast('Revise os campos destacados.', { type: 'error' });
      return;
    }
    const btn = document.getElementById('submitBtn');
    btn.disabled = true;
    btn.textContent = 'Enviando…';
    const email = prepararEmail(form.elements.email.value);
    const nome = prepararNome(form.elements.nome.value);
    const servicos = opcoesServico().filter(input => input.checked).map(input => input.value);
    const autoresposta = `Olá, ${nome}!

Obrigado por entrar em contato com a Westie.

Recebemos sua mensagem sobre ${servicos.join(', ')} e já estamos analisando o que você precisa. Um especialista vai te responder em até 24 horas úteis.

Enquanto isso, se quiser adiantar a conversa, é só chamar no WhatsApp:

📱 (11) 94723-2559

É o canal mais rápido — em geral respondemos em poucos minutos no horário comercial.

O que acontece a seguir:
1. Analisamos o cenário que você descreveu
2. Montamos um diagnóstico gratuito da automação
3. Apresentamos a proposta com prazo e investimento

Se a sua necessidade for urgente, chame direto no WhatsApp que a gente prioriza.

Um abraço,
Equipe Westie
Automações que trabalham por você.`;
    const respostas = {
      email,
      nome,
      interesse: servicos.join(', '),
      corpo_email: `E-mail: ${email}`,
      corpo_nome: `Nome: ${nome}`,
      corpo_interesse: `Interesse: ${servicos.join(', ')}`,
      whatsapp: form.elements.whatsapp.value.trim(),
      empresa: form.elements.empresa.value.trim(),
      servicos: servicos.join(', '),
      servico: {
        'Leads': 'leads',
        'Chatbot com WhatsApp': 'chatbot-whatsapp',
        'Lembretes': 'lembretes',
        'Avaliações': 'avaliacoes',
        'Transações': 'transacoes'
      }[servicos[0]] || 'outro',
      mensagem: msg.value.trim()
    };
    opcoesServico().forEach(input => {
      respostas[input.name] = input.checked ? input.value : '';
    });
    fetch(form.action, {
      method: 'POST',
      body: JSON.stringify(respostas),
      headers: {
        Accept: 'application/json',
        'Content-Type': 'application/json'
      }
    })
      .then(response => {
        if (!response.ok) throw new Error('Falha ao enviar o formulário.');
        return response.json();
      })
      .then(() => {
        body.style.display = 'none';
        success.classList.add('show');
        window.skipUI.toast('Mensagem enviada com sucesso.', { type: 'success' });
      })
      .catch(error => {
        btn.disabled = false;
        btn.textContent = 'Enviar mensagem';
        window.skipUI.toast(error.message, { type: 'error' });
      });
  });

  document.getElementById('resetForm').addEventListener('click', () => {
    form.reset();
    counter.textContent = '0/500';
    form.querySelectorAll('.field').forEach(f => f.classList.remove('invalid'));
    form.querySelectorAll('.field-error').forEach(el => el.textContent = '');
    const btn = document.getElementById('submitBtn');
    btn.disabled = false;
    btn.textContent = 'Enviar mensagem';
    success.classList.remove('show');
    body.style.display = '';
  });
}

/* ===== MENU MOBILE ===== */
function setupMenu() {
  const toggle = document.getElementById('menuToggle');
  const nav = document.getElementById('mobileNav');
  function set(open) {
    nav.classList.toggle('open', open);
    toggle.setAttribute('aria-expanded', String(open));
    toggle.setAttribute('aria-label', open ? 'Fechar menu' : 'Abrir menu');
  }
  toggle.addEventListener('click', () => set(!nav.classList.contains('open')));
  nav.querySelectorAll('a').forEach(a => a.addEventListener('click', () => set(false)));
  document.addEventListener('keydown', e => { if (e.key === 'Escape') set(false); });
}

/* ===== SCROLL: progresso, topo, header ===== */
function setupScroll() {
  const bar = document.getElementById('progressBar');
  const btn = document.getElementById('backToTop');
  const header = document.querySelector('.site-header');
  function onScroll() {
    const max = document.documentElement.scrollHeight - window.innerHeight;
    bar.style.width = (max > 0 ? (window.scrollY / max) * 100 : 0) + '%';
    btn.classList.toggle('show', window.scrollY > 600);
    header.style.borderBottomColor = window.scrollY > 10 ? 'rgba(198,255,61,.12)' : '';
  }
  window.addEventListener('scroll', onScroll, { passive: true });
  btn.addEventListener('click', () => window.scrollTo({ top: 0, behavior: 'smooth' }));
  onScroll();
}

/* ===== ANIMAÇÕES: entrada e contadores ===== */
function animarContador(el) {
  const alvo = +el.dataset.count;
  const dur = 1600;
  const inicio = performance.now();
  function frame(t) {
    const p = Math.min(1, (t - inicio) / dur);
    const eased = 1 - Math.pow(1 - p, 3);
    el.textContent = Math.round(alvo * eased);
    if (p < 1) requestAnimationFrame(frame);
  }
  requestAnimationFrame(frame);
}

function setupAnimacoes() {
  const reduz = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
  const io = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (!entry.isIntersecting) return;
      const el = entry.target;
      el.classList.add('is-visible');
      if (el.id === 'timeline') el.classList.add('is-visible');
      el.querySelectorAll?.('[data-count]').forEach(c => {
        if (!c.dataset.done) {
          c.dataset.done = '1';
          reduz ? (c.textContent = c.dataset.count) : animarContador(c);
        }
      });
      if (el.matches('[data-count]') && !el.dataset.done) {
        el.dataset.done = '1';
        animarContador(el);
      }
      io.unobserve(el);
    });
  }, { threshold: 0.15 });

  document.querySelectorAll('.reveal, .stat, .timeline').forEach(el => io.observe(el));

  const tl = document.getElementById('timeline');
  const ioTl = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) { tl.classList.add('is-visible'); ioTl.disconnect(); } });
  }, { threshold: 0.4 });
  ioTl.observe(tl);
}

/* ===== CARDS COM PLANOS E FAQ: observação após render ===== */
function observarNovos() {
  const io = new IntersectionObserver((entries, obs) => {
    entries.forEach(e => {
      if (e.isIntersecting) { e.target.classList.add('is-visible'); obs.unobserve(e.target); }
    });
  }, { threshold: 0.15 });
  document.querySelectorAll('.service-card.reveal, .plan.reveal, .faq-item.reveal').forEach(el => io.observe(el));
}

/* ===== CTAs: planos e foco ===== */
function setupPlanCtas() {
  document.getElementById('plansGrid').addEventListener('click', e => {
    const b = e.target.closest('[data-plan-cta]');
    if (!b) return;
    if (b.dataset.planCta === 'Enterprise' || b.dataset.planCta === 'Falar com especialista') {
      window.skipUI.toast('Um especialista entrará em contato para montar a proposta.');
    } else {
      window.skipUI.toast(`Plano ${b.dataset.planCta} selecionado (demonstração).`, { type: 'success' });
    }
    document.getElementById('contato').scrollIntoView({ behavior: 'smooth' });
  });
}

/* ===== INICIALIZAÇÃO ===== */
document.addEventListener('DOMContentLoaded', () => {
  renderServicos();
  renderPlanos();
  renderFaq();
  setupBillingToggle();
  setupCalculadora();
  setupModais();
  setupFormulario();
  setupMenu();
  setupScroll();
  setupAnimacoes();
  observarNovos();
  setupPlanCtas();
});
</script>
</body>
</html>
