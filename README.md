# rishipalyadav.github.io

Personal site built with [Hugo](https://gohugo.io/) + [Blowfish theme](https://blowfish.page/), deployed via GitHub Actions to GitHub Pages.

**Live site:** https://rishipalyadav.github.io

---

## First-time setup (macOS)

### 1. Install dependencies

```bash
# Install Homebrew if you don't have it
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Install Hugo (extended version — required for Blowfish)
brew install hugo

# Verify
hugo version
# Should show: hugo v0.xxx+extended ...
```

### 2. Clone your repo and add Blowfish as a submodule

```bash
# Clone your repo (replace with your actual repo URL)
git clone https://github.com/rishipalyadav/rishipalyadav.github.io.git
cd rishipalyadav.github.io

# Add Blowfish as a git submodule
git submodule add -b main https://github.com/nunocoracao/blowfish.git themes/blowfish

# Copy the config files from Blowfish into your config folder
# (skip this if you're using the config files from this repo)
cp -r themes/blowfish/config/* config/

# Commit the submodule
git add .
git commit -m "add blowfish theme as submodule"
git push
```

### 3. Preview locally

```bash
hugo server
# Open http://localhost:1313 in your browser
# Live-reloads on every file save
```

### 4. Add your headshot

Drop your photo into `assets/img/avatar.jpg`. Blowfish will pick it up automatically from `languages.en.toml` where `image = "img/avatar.jpg"` is set.

Recommended: square image, minimum 400×400px.

---

## Enable GitHub Pages in your repo settings

1. Go to your repo on GitHub → **Settings** → **Pages**
2. Under **Source**, select **GitHub Actions**
3. Push to `main` — the workflow in `.github/workflows/gh-pages.yml` will build and deploy automatically

---

## Adding content

### New blog post
```bash
hugo new posts/my-post-title.md
# Edit content/posts/my-post-title.md
# Set draft: false when ready to publish
```

### New research entry
```bash
hugo new research/paper-title.md
```

### Cross-posting from Medium

For Medium articles, you have two options:

**Option A — Mirror post** (better for SEO): Copy the article into a new `.md` file under `content/posts/`. Add this to the front matter:
```yaml
canonicalUrl: "https://notyourciso.medium.com/your-article-url"
```

**Option B — Link card**: Keep just a short description + link to Medium. Keeps things simple and drives Medium traffic.

---

## Customisation quick reference

| What to change | File |
|---|---|
| Site title, author name, bio | `config/_default/languages.en.toml` |
| Color scheme, dark mode | `config/_default/params.toml` |
| Navigation links | `config/_default/menus.en.toml` |
| Homepage layout | `config/_default/params.toml` → `[homepage]` |
| Base URL | `config/_default/hugo.toml` |

### Color scheme options (set in params.toml)
`slate` · `noir` · `terminal` · `github` · `blowfish` · `forest` · `ocean` · `fire`

---

## Project structure

```
rishipalyadav.github.io/
├── .github/
│   └── workflows/
│       └── gh-pages.yml        # auto-deploy on push to main
├── assets/
│   └── img/
│       └── avatar.jpg          # YOUR PHOTO goes here
├── config/
│   └── _default/
│       ├── hugo.toml           # base URL, language
│       ├── languages.en.toml   # author info, bio, social links
│       ├── menus.en.toml       # navigation
│       └── params.toml         # theme settings, homepage layout
├── content/
│   ├── _index.md               # homepage intro text (below author card)
│   ├── about.md                # About page
│   ├── posts/                  # blog posts
│   │   ├── _index.md
│   │   └── *.md
│   └── research/               # research papers
│       ├── _index.md
│       └── *.md
├── themes/
│   └── blowfish/               # git submodule — do not edit directly
└── README.md
```

---

## Updating Blowfish

```bash
git submodule update --remote --merge
git add themes/blowfish
git commit -m "update blowfish theme"
git push
```
