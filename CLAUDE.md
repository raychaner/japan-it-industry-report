# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a comprehensive research report on the Japanese IT industry, covering market size, employment trends, foreign worker opportunities, and future outlook. The project is a **documentation-only repository** using Docsify to render Markdown files as a static website hosted on GitHub Pages.

**Live site**: https://raychaner.github.io/japan-it-industry-report/

## Repository Structure

```
.
├── docs/                    # Single source of truth for all content
│   ├── index.html          # Docsify configuration (Vue theme, plugins)
│   ├── README.md           # Website homepage with navigation
│   ├── .nojekyll           # Required for GitHub Pages (do not delete)
│   ├── 00_项目大纲.md      # Project outline
│   ├── 01-08_*.md          # Eight main chapters
│   └── 使用说明.md         # Usage instructions
├── README.md               # Repository overview (summary only)
├── DEPLOY.md               # GitHub Pages deployment guide
└── .gitignore
```

**Critical**: `docs/` is the single source of truth. All content lives there. Root `README.md` is just a summary.

## Local Development

### Start local server (3 methods)

**Method 1 - Docsify CLI (recommended)**:
```bash
npm i docsify-cli -g
docsify serve docs
# Opens at http://localhost:3000
```

**Method 2 - Python**:
```bash
cd docs
python -m http.server 3000
```

**Method 3 - VS Code Live Server**:
Right-click `docs/index.html` → "Open with Live Server"

**Important**: Must use HTTP server. Opening `index.html` directly in browser will break search and Mermaid diagrams.

## Content Editing

### Markdown files
- All content is in `docs/*.md` files
- Uses GitHub-flavored Markdown
- Includes 40+ Mermaid diagrams (flowcharts, mindmaps, timelines)
- Heavy use of tables, blockquotes, and emoji

### Docsify configuration
Located in [docs/index.html](docs/index.html):
- Theme: Vue.css with custom Chinese font optimization
- Plugins: search, pagination, copy-code, word count, dark theme, Mermaid
- Theme color: `#42a5f5` (blue)
- Sidebar: Auto-generated from headings (subMaxLevel: 3)

### Key files
- [docs/index.html](docs/index.html) - All Docsify config and styling
- [docs/README.md](docs/README.md) - Homepage with full navigation and data tables
- [docs/.nojekyll](docs/.nojekyll) - Empty file, required for GitHub Pages to work

## Deployment

### GitHub Pages setup
1. Repository must be **public**
2. Settings → Pages → Source: `main` branch, Folder: `/docs`
3. Site deploys automatically on push to main
4. Takes 1-3 minutes to update

### Deployment workflow
```bash
git add .
git commit -m "Update content"
git push
# Wait 1-2 minutes for automatic deployment
```

See [DEPLOY.md](DEPLOY.md) for detailed instructions.

## Content Guidelines

### Language and audience
- Written in **Simplified Chinese**
- Target audience: Foreign IT professionals interested in Japan, Japanese IT workers, investors, researchers
- Formal but accessible tone

### Document structure
Each chapter follows this pattern:
- Numbered sections (e.g., 1.1, 1.2)
- Data tables with statistics
- Mermaid diagrams for visualization
- Blockquotes for important notes
- Chapter summaries

### Data sources
- Japanese Ministry of Economy, Trade and Industry (METI)
- Information-technology Promotion Agency (IPA)
- Market research: Mordor Intelligence, IDC, Gartner, IMARC Group
- Data is from 2024, with projections to 2030

## Technical Notes

### Mermaid diagrams
- Rendered client-side via Mermaid.js v10
- Centered with custom CSS
- Must be in code blocks with `mermaid` language tag
- Requires HTTP server to render

### Chinese font optimization
Custom font stack in [docs/index.html](docs/index.html):
```css
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI",
             "Noto Sans SC", "Microsoft YaHei", sans-serif;
```

### CDN dependencies
All assets loaded from CDN (jsdelivr):
- Docsify core and plugins
- Mermaid.js
- Dark theme plugin
- No local dependencies or build process

## Git Workflow

- Main branch: `main`
- Current branch: `Claude-code-edit`
- Repository is clean (no uncommitted changes)
- Recent commits focus on documentation improvements and GitHub Pages setup

## Common Tasks

### Adding a new chapter
1. Create `docs/XX_章节名.md`
2. Update navigation in [docs/README.md](docs/README.md)
3. Follow existing chapter structure and numbering

### Modifying theme
Edit CSS variables in [docs/index.html](docs/index.html):
```css
:root {
  --theme-color: #42a5f5;
  --theme-color-dark: #1976d2;
}
```

### Testing locally
Always test with HTTP server before pushing. Check:
- Mermaid diagrams render correctly
- Search functionality works
- Navigation links are correct
- Tables display properly
- Dark theme toggle works
