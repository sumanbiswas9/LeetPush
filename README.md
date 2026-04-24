<p align="center">
  <img src="assets/icon128.png" alt="LeetPush Logo" width="100" height="100" />
</p>

<h1 align="center">LeetPush</h1>

<p align="center">
  <strong>Push your LeetCode solutions directly to GitHub — without ever leaving LeetCode.</strong>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/version-1.0.0-6c5ce7?style=for-the-badge" alt="Version 1.0.0" />
  <img src="https://img.shields.io/badge/manifest-v3-0984e3?style=for-the-badge" alt="Manifest V3" />
  <img src="https://img.shields.io/badge/platform-Chrome-00b894?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Chrome" />
  <img src="https://img.shields.io/badge/license-MIT-fdcb6e?style=for-the-badge" alt="MIT License" />
</p>

<p align="center">
  <em>One click. Your code on GitHub. Zero context-switching.</em>
</p>

---

## 📌 Table of Contents

- [The Problem](#-the-problem)
- [The Solution](#-the-solution)
- [Key Features](#-key-features)
- [How It Works](#-how-it-works)
- [Installation Guide](#-installation-guide)
- [Step-by-Step Usage](#-step-by-step-usage)
- [Supported Languages](#-supported-languages)
- [Project Architecture](#-project-architecture)
- [Privacy & Security](#-privacy--security)
- [Who Is This For?](#-who-is-this-for)
- [Support This Project](#-support-this-project)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🔴 The Problem

Every competitive programmer and job-seeker who practices on **LeetCode** faces the same friction:

1. **Manual copy-pasting** — After solving a problem, you have to manually copy your code, switch to GitHub, navigate to the right folder, create a new file, paste the code, write a commit message, and push.
2. **Broken workflow** — Constantly tab-switching between LeetCode and GitHub kills focus and wastes precious time.
3. **Inconsistent organization** — Without a system, solutions end up scattered across random repos, unnamed files, or lost entirely.
4. **No version tracking** — If you revisit and improve a solution, there's no easy way to track your progress over time.
5. **Missing metadata** — Problem difficulty, language, and problem links are rarely preserved alongside the solution file.

> **The result?** Hundreds of solved problems, but a messy (or empty) GitHub profile that doesn't reflect your effort.

---

## ✅ The Solution

**LeetPush** eliminates the entire manual workflow. It's a Chrome Extension built on **Manifest V3** that:

- **Automatically detects** the problem title, number, difficulty, language, and your code from the active LeetCode tab.
- **Pushes your solution** to any GitHub repository with a **single click** — complete with a professional file header (problem metadata, difficulty, date, LeetCode link).
- **Organizes your code** into a folder structure of your choice, right from the extension popup.
- **Handles duplicates intelligently** — prompts you to overwrite, update, or push as a new version.
- **Supports undo** — accidentally pushed the wrong file? One-click undo deletes it from GitHub.
- **Tracks your history** — every push is logged locally so you can review past submissions.

> **In short:** Solve on LeetCode → Click "Push" → Your code is on GitHub. Done.

---

## 🚀 Key Features

| Feature | Description |
|---|---|
| **One-Click Push** | Push your solution to GitHub directly from the LeetCode problem page. |
| **Auto-Detection** | Automatically extracts problem title, number, difficulty, language, and code from the LeetCode editor. |
| **Smart File Naming** | Generates clean, standardized filenames like `001_two_sum.py`. |
| **Professional Code Headers** | Automatically prepends metadata (problem name, difficulty, LeetCode link, language, date) as comments. |
| **Folder Navigation** | Browse your repo's folder tree, search folders, and create new ones — all from the popup. |
| **Duplicate Handling** | Detects existing files and lets you choose: Overwrite, Push as New Version, or Cancel. |
| **Undo / Delete** | Instantly undo the last push by deleting the file from GitHub. |
| **Push History** | Maintains a local history of all your pushes with timestamps, folders, and direct GitHub links. |
| **Multi-Repo Support** | Connect and switch between multiple GitHub repositories. |
| **Dark / Light Theme** | Sleek UI with both dark and light themes — remembers your preference. |
| **Folder Caching** | Caches the repository folder tree for 5 minutes to avoid redundant API calls. |
| **Custom Commit Messages** | Auto-generates commit messages or lets you write your own. |
| **Offline-Safe Credentials** | GitHub PAT is stored in Chrome's secure `storage.sync` — never sent anywhere except GitHub's API. |
| **25+ Language Support** | Python, Java, C++, JavaScript, TypeScript, Go, Rust, Kotlin, and many more. |

---

## ⚙️ How It Works

```
┌─────────────────────────────────────────────────────────────────┐
│                     LeetCode Problem Page                       │
│                                                                 │
│  ┌─────────────────────────────────────────────────────────┐    │
│  │  Content Script + Inject Script                         │    │
│  │  • Extracts problem title, number, difficulty           │    │
│  │  • Hooks into Monaco editor to capture your code        │    │
│  │  • Detects programming language                         │    │
│  └────────────────────────┬────────────────────────────────┘    │
└───────────────────────────┼─────────────────────────────────────┘
                            │
                            ▼
┌─────────────────────────────────────────────────────────────────┐
│                    Extension Popup (UI)                          │
│                                                                 │
│  • Displays problem info card (title, difficulty, language)     │
│  • Shows code preview                                           │
│  • Folder tree browser with search + create                     │
│  • Commit message input                                         │
│  • One-click "Push to GitHub 🚀" button                         │
│  • Push history tab                                             │
└────────────────────────┬────────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│                   Background Service Worker                      │
│                                                                 │
│  • Proxies all GitHub API calls                                 │
│  • Handles: Test Connection, Get Repo Tree, Check File,         │
│             Push File (create/update), Delete File               │
│  • Manages rate-limit detection and error handling               │
│  • Updates extension icon state based on active tab              │
└────────────────────────┬────────────────────────────────────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │    GitHub REST API    │
              │  api.github.com      │
              └─────────────────────┘
```

---

## 📦 Installation Guide

### Prerequisites

- **Google Chrome** (or any Chromium-based browser — Edge, Brave, Arc, etc.)
- A **GitHub account** with at least one repository
- A **GitHub Personal Access Token (PAT)** with `repo` scope

### Step 1 — Generate a GitHub Personal Access Token

1. Go to [github.com/settings/tokens/new](https://github.com/settings/tokens/new?scopes=repo&description=LeetPush).
2. Set a descriptive name, e.g., `LeetPush`.
3. Under **Select scopes**, check **`repo`** (full control of private repositories).
4. Click **Generate token** and **copy the token immediately** — you won't see it again.

### Step 2 — Download or Clone the Extension

```bash
git clone https://github.com/sumanbiswas9/LeetPush.git
```

Or download the ZIP from the repository and extract it.

### Step 3 — Load the Extension in Chrome

1. Open Chrome and navigate to `chrome://extensions/`.
2. Toggle **"Developer mode"** ON (top-right corner).
3. Click **"Load unpacked"**.
4. Select the **LeetPush** project folder (the one containing `manifest.json`).
5. The LeetPush icon will appear in your Chrome toolbar. Pin it for quick access.

### Step 4 — Configure Your GitHub Repository

1. Click the **LeetPush icon** in the toolbar.
2. If this is your first time, you'll see a **"Setup Required"** screen — click **"⚙️ Open Settings"**.
3. Enter:
   - **Personal Access Token** — the PAT you generated in Step 1.
   - **GitHub Username** — your GitHub username.
   - **Repository Name** — the name of the repo where you want to push solutions (e.g., `leetcode-solutions`).
   - **Branch** — defaults to `main`. Change if your repo uses a different default branch.
4. Click **"🔌 Test Connection"** to verify everything works.
5. Click **"💾 Save Repository"** to save the configuration.

> ✅ You're all set! Navigate to any LeetCode problem to start pushing.

---

## 📖 Step-by-Step Usage

### Pushing a Solution

1. **Solve a LeetCode problem** as you normally would on [leetcode.com](https://leetcode.com).
2. **Click the LeetPush icon** in your Chrome toolbar while on the problem page.
3. The popup displays:
   - **Problem Card** — Title, number, difficulty badge, detected language, and a link to the problem.
   - **Code Preview** — Click "Preview Code" to verify the code that will be pushed.
   - **File Name** — Auto-generated filename (e.g., `001_two_sum.py`).
4. **Select a destination folder** from the folder tree, or create a new one (e.g., `Arrays`, `DSA/Dynamic-Programming`).
5. **Edit the commit message** (optional) — a descriptive commit message is auto-generated.
6. **Click "Push to GitHub 🚀"**.
7. A success toast appears with a **direct link to the file on GitHub**.

### Handling Duplicate Files

If a file with the same name already exists in the selected folder:

- **🔄 Overwrite / Update** — Replaces the existing file (preserves Git history).
- **📝 Push as New Version** — Creates a versioned copy (e.g., `001_two_sum_v2.py`).
- **Cancel** — Aborts the push.

### Undoing a Push

After a successful push, an **"↩️ Undo"** button appears in the toast notification. Click it to delete the file from GitHub instantly.

> ⚠️ Undo is only available for newly pushed files (not for overwrites/updates).

### Viewing Push History

1. Click the **"📋 History"** tab in the popup.
2. View a chronological list of all your pushes, including:
   - Problem title
   - Destination folder
   - Difficulty badge
   - Date & time
   - Direct link to the file on GitHub
3. Click **"🗑 Clear All"** to reset history.

### Switching Repositories

1. Use the **repo dropdown** at the top of the popup to switch between saved repositories.
2. To add a new repo, open **Settings** (⚙️) and add another repository.

### Toggling Theme

Click the **🌙 / ☀️ button** in the popup header to switch between dark and light themes.

---

## 🌐 Supported Languages

LeetPush supports **25+ programming languages** used on LeetCode:

| Language | Extension | Language | Extension |
|---|---|---|---|
| Python / Python3 | `.py` | Go | `.go` |
| Java | `.java` | Ruby | `.rb` |
| C++ | `.cpp` | Swift | `.swift` |
| C | `.c` | Kotlin | `.kt` |
| C# | `.cs` | Rust | `.rs` |
| JavaScript | `.js` | Scala | `.scala` |
| TypeScript | `.ts` | PHP | `.php` |
| Dart | `.dart` | Racket | `.rkt` |
| Erlang | `.erl` | Elixir | `.ex` |
| MySQL / SQL / MS SQL / Oracle | `.sql` | Pandas | `.py` |

Each language gets **properly formatted comment headers** in its native comment syntax (`//`, `#`, `--`, `;`, etc.).

---

## 🏗️ Project Architecture

```
LeetPush/
├── manifest.json          # Chrome Extension manifest (Manifest V3)
├── assets/
│   ├── icon16.png         # Toolbar icon (16×16)
│   ├── icon32.png         # Toolbar icon (32×32)
│   ├── icon48.png         # Extension management icon (48×48)
│   ├── icon128.png        # Chrome Web Store icon (128×128)
│   └── QR.jpeg            # Support/Donation QR code
├── background/
│   └── background.js      # Service worker — GitHub API proxy & icon state
├── content/
│   ├── content.js         # Content script — extracts problem data from LeetCode DOM
│   └── inject.js          # Injected script — hooks into Monaco editor for code extraction
├── popup/
│   ├── popup.html         # Main extension popup UI
│   ├── popup.css          # Popup styles (dark/light themes, animations)
│   └── popup.js           # Popup logic (push flow, history, folder tree, etc.)
├── options/
│   ├── options.html       # Settings/configuration page
│   ├── options.css        # Options page styles
│   └── options.js         # Settings logic (repo management, theme, test connection)
└── README.md              # You are here
```

### Component Responsibilities

| Component | Role |
|---|---|
| **manifest.json** | Declares permissions, content scripts, background worker, and extension metadata. |
| **background.js** | Service worker that proxies all GitHub REST API calls (`GET`, `PUT`, `DELETE`). Manages rate-limit errors, connection testing, repo tree fetching, file existence checks, file pushing, and file deletion. |
| **content.js** | Content script injected into LeetCode problem pages. Extracts the problem title, number, difficulty, language, and coordinates code extraction via the inject script. |
| **inject.js** | Runs in the page's main world to access the Monaco editor instance directly. Extracts code from the editor via the Monaco API, CodeMirror fallback, or React fiber traversal. |
| **popup.js** | The main UI controller. Manages the push workflow, folder tree navigation, duplicate detection, undo, push history, and theme toggling. |
| **options.js** | Settings page controller. Handles GitHub credential management, connection testing, repo CRUD, and theme preferences. |

---

## 🔒 Privacy & Security

LeetPush takes your privacy seriously:

- **🔐 Your GitHub PAT is stored locally** in Chrome's `storage.sync` — it is **never** transmitted to any server other than GitHub's official API (`api.github.com`).
- **🚫 No analytics, no tracking, no telemetry.** LeetPush does not collect or transmit any personal data.
- **💾 All data stays on your machine.** Push history, folder caches, and preferences are stored in Chrome's local storage.
- **🛡️ Production builds are obfuscated** to protect the source code from reverse engineering.
- **🌐 Minimal permissions.** The extension only requests the permissions it needs: `storage`, `activeTab`, `tabs`, `scripting`, and access to `api.github.com` and `leetcode.com`.

---

## 🎯 Who Is This For?

| Audience | How LeetPush Helps |
|---|---|
| **Job Seekers** | Build a well-organized GitHub portfolio of LeetCode solutions to impress recruiters. |
| **Competitive Programmers** | Save time by automating the push workflow — focus on problem-solving, not file management. |
| **CS Students** | Track your DSA practice progress with a clean, version-controlled archive of solutions. |
| **Open Source Enthusiasts** | Contribute to a public "leetcode-solutions" repo that showcases your skills. |
| **Interview Prep Coaches** | Recommend LeetPush to students so they can maintain organized solution repositories effortlessly. |

---

## ❤️ Support This Project

If **LeetPush** saves you time and helps you build a better GitHub profile, consider supporting the project! Every contribution keeps development alive and helps bring new features.

<p align="center">
  <img src="assets/QR.jpeg" alt="Scan this QR code to support LeetPush" width="200" height="200" style="border-radius: 12px;" />
</p>

<p align="center">
  <strong>Scan the QR code above to buy the developer a coffee ☕</strong>
</p>

Your support means the world and motivates continued development of free, open-source tools for the developer community. Thank you! 🙏

---

## 🤝 Contributing

Contributions are welcome! If you'd like to improve LeetPush:

1. **Fork** this repository.
2. **Create a feature branch:** `git checkout -b feature/your-feature-name`
3. **Commit your changes:** `git commit -m "Add: your feature description"`
4. **Push to the branch:** `git push origin feature/your-feature-name`
5. **Open a Pull Request** with a clear description of your changes.

### Development Setup

```bash
# Clone the repository
git clone https://github.com/sumanbiswas9/LeetPush.git
cd LeetPush

# Load as unpacked extension in Chrome
# chrome://extensions/ → Developer mode → Load unpacked → select this folder

# For production build (obfuscated + minified)
chmod +x build.sh
./build.sh
# Output: /dist folder and leetpush-dist.zip
```

### Build Script

The included `build.sh` creates a production-ready distribution:

- **Obfuscates** all JavaScript files with `javascript-obfuscator`
- **Minifies** all CSS files with `clean-css`
- **Packages** everything into a `leetpush-dist.zip` ready for Chrome Web Store submission

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/sumanbiswas9">Suman Biswas</a>
</p>

<p align="center">
  <strong>⭐ Star this repo if LeetPush helped you!</strong>
</p>