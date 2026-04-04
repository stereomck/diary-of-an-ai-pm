# Diary of an AI PM — Site README
**D/AI** · diaryofanaipm.com · Maintained by Claude

---

## Site structure

```
diary-of-an-ai-pm/
├── index.html          # Homepage — teaser landing page (Phase 2 prep)
├── about.html          # About page
├── feed.xml            # RSS feed — empty until Phase 2 launch
├── CNAME               # Custom domain: diaryofanaipm.com
│
├── css/
│   └── style.css       # All brand CSS — edit here for design changes
│
└── posts/              # Empty until Phase 2 launch
    └── (entries go here)
```

**How GitHub Pages works:** push any file to this repo and GitHub serves it as a live website at diaryofanaipm.com. No build step. No server. Just files.

---

## Phase rules — READ THIS FIRST

**Phase 1 (current):** Private drafts only. The site is a teaser landing page + newsletter signup. NO published entries. NO job search content. NO employer references.

**Phase 2 (when active):** Soft launch. Focus on "the AI PM role itself." Never reference job search or current employer by name. Begin publishing accumulated private drafts.

**Phase 3 (after landing):** Full launch. Tell the whole story with receipts. Publish everything.

**The site is currently in Phase 1.** Do not publish any entries until Phase 2 is explicitly activated.

---

## Brand reference

| Token        | Value      | Use                         |
|--------------|------------|-----------------------------|
| `--ink`      | `#1C1917`  | Primary text, dark elements |
| `--gilt`     | `#C8A96E`  | Gold accent, links, tags    |
| `--gilt-dim` | `#A08555`  | Borders, secondary gold     |
| `--page`     | `#F5F0E8`  | Background (warm paper)     |
| `--red-pen`  | `#E8372A`  | Code, editorial marks       |
| `--noise`    | `#8A7F74`  | Secondary text, meta        |
| Serif        | Libre Baskerville | Titles, post body      |
| Sans         | DM Sans    | Nav, secondary text         |
| Mono         | DM Mono    | Code, labels, meta          |

**Visual identity:** Light background (warm paper), dark text, gold accents. The aesthetic is "private journal made public" — elegant, literary, slightly worn. The red-pen color is used for code and editorial annotations, like markup on a manuscript.

---

## Adding a new entry (Phase 2+)

### Step 1 — Generate the entry file

```
D/AI new entry

Title: [title]
Date: [YYYY-MM-DD]
Tags: [tag1, tag2]
Excerpt: [one sentence]
Content: [paste the script or write "generate from draft notes"]

Generate the complete posts/[slug].html file for the Diary of an AI PM site.
Include the full post body as proper HTML. Return only the file contents.
```

### Step 2 — Update index.html

```
D/AI update index

Add this entry to diary-of-an-ai-pm/index.html entry list (newest at top):
- File: posts/[slug].html
- Date: [Month DD, YYYY]
- Tags: [tag1, tag2]
- Title: [title]
- Excerpt: [excerpt]

Also update the entry count in .post-list-count.
Return the updated post-list section of index.html only.
```

### Step 3 — Update feed.xml

```
D/AI update feed

Add this entry to diary-of-an-ai-pm/feed.xml (newest at top inside <channel>):
- Title: [title]
- URL: https://diaryofanaipm.com/posts/[slug].html
- Date: [Day, DD Mon YYYY 00:00:00 +0000]
- Description: [excerpt]

Return the updated feed.xml file.
```

### Step 4 — Push to GitHub

```bash
git add posts/[slug].html index.html feed.xml
git commit -m "entry: [title]"
git push
```

Site is live at diaryofanaipm.com within 30 seconds.

---

## Maintenance prompts

### Change a design element

```
D/AI design update

In diary-of-an-ai-pm/css/style.css, [describe the change].
Example: "add a red-pen strikethrough animation for edited text"
Example: "increase the body serif font size on mobile"
Example: "add a handwritten-style border to blockquotes"

Return the updated CSS block only, with a comment marking what changed.
```

### Remove the phase banner (Phase 2 launch)

```
D/AI launch phase 2

Remove the .phase-banner section from index.html.
Update the post-list-count from "0 entries" to the current count.
Update this README to mark Phase 2 as active.
```

### Add a new page

```
D/AI new page

Create [page-name].html for the Diary of an AI PM site.
Purpose: [what this page is for]
Nav label: [text shown in header nav]
Content: [describe or provide content]

Match the exact structure of about.html — same header, footer, CSS link.
Add the nav link to all pages. Return each file's updated <nav> block
and the complete new page.
```

### Update all nav links

```
D/AI nav update

Add/change/remove this nav item across all Diary of an AI PM pages:
[describe the change]

Files to update: index.html, about.html, [list any post files].
Return each file's updated <nav> block only.
```

### Generate RSS feed from scratch

```
D/AI regenerate feed

Generate a complete feed.xml for Diary of an AI PM from this entry list:
[paste entry titles, URLs, dates, and excerpts]

Use the same format as the existing feed.xml.
```

---

## Entry file template

When asking Claude to generate a new entry, it will use this structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>[ENTRY TITLE] — Diary of an AI PM</title>
  <meta name="description" content="[EXCERPT]">
  <meta name="author" content="Michael Kent">
  <meta property="og:title" content="[ENTRY TITLE]">
  <meta property="og:description" content="[EXCERPT]">
  <meta property="og:type" content="article">
  <meta property="og:url" content="https://diaryofanaipm.com/posts/[SLUG].html">
  <meta property="article:published_time" content="[YYYY-MM-DD]">
  <link rel="canonical" href="https://diaryofanaipm.com/posts/[SLUG].html">
  <link rel="alternate" type="application/rss+xml" title="Diary of an AI PM" href="/feed.xml">
  <link rel="stylesheet" href="../css/style.css">
</head>
<body>
  [HEADER — identical to other pages]
  <main class="page-wrapper">
    <article>
      <header class="post-header">
        <div class="post-item-tags">
          <span class="post-tag">[TAG]</span>
        </div>
        <h1 class="post-title">[TITLE]</h1>
        <div class="post-meta">
          <span class="post-meta-item">Michael Kent</span>
          <span class="post-meta-sep"></span>
          <span class="post-meta-item">[DATE]</span>
          <span class="post-meta-sep"></span>
          <span class="post-meta-item">[N] min read</span>
        </div>
      </header>
      <div class="post-body">
        [CONTENT]
      </div>
      <footer class="post-footer">
        <a href="/" class="post-back">← All entries</a>
        <div class="post-channel-links">
          <a href="https://contextwindow.dev">Context Window →</a>
          <a href="https://postsynaptic.dev">PostSynaptic →</a>
        </div>
      </footer>
    </article>
  </main>
  [FOOTER — identical to other pages]
</body>
</html>
```

---

## Git workflow

```bash
# First time setup
git clone https://github.com/stereomck/diary-of-an-ai-pm.git
cd diary-of-an-ai-pm

# Every time you add/update content
git add .
git commit -m "entry: [title]"   # for new entries
git commit -m "fix: [change]"    # for corrections
git commit -m "design: [change]" # for CSS/layout changes
git push

# Check build status
# Go to: github.com/stereomck/diary-of-an-ai-pm/actions
```

---

## Shortcodes used in prompts

| Shortcode | Meaning                         |
|-----------|---------------------------------|
| `D/AI`    | Diary of an AI PM task          |
| `CW:[]`   | Context Window site task        |
| `PS://`   | PostSynaptic site task          |

---

## Safety rules — non-negotiable

1. **NEVER** name the current employer in any published content
2. **NEVER** publish job search content until Phase 2 is explicitly active
3. **NEVER** use "journey" as a noun for Michael's career
4. **NEVER** open with "I'm excited to share..."
5. **NEVER** perform vulnerability — document the process, don't dramatize it
6. Assume Michael's current boss could read any published content
7. Check employment contract before referencing the consulting firm

---

## Checklist — going live (Phase 1: teaser only)

- [ ] Create GitHub repo named `diary-of-an-ai-pm` (public)
- [ ] Push all files from this folder
- [ ] Settings → Pages → Deploy from branch → main / root
- [ ] Buy domain: diaryofanaipm.com (Namecheap or Cloudflare Registrar)
- [ ] Add CNAME record: `www` → `stereomck.github.io`
- [ ] Add A records: four GitHub IPs (185.199.108-111.153)
- [ ] Settings → Pages → Custom domain → diaryofanaipm.com
- [ ] Wait up to 24 hours for DNS propagation
- [ ] Tick "Enforce HTTPS" once it becomes available
- [ ] Set up Substack at substack.com/@diaryofanaipm
- [ ] Update placeholder YouTube URL in nav once channel exists

## Checklist — Phase 2 launch

- [ ] Remove phase-banner from index.html
- [ ] Publish accumulated private drafts as posts/*.html
- [ ] Update index.html post list and feed.xml
- [ ] Update this README to mark Phase 2 as active
- [ ] Announce on LinkedIn and cross-link from CW + PS
