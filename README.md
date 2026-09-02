<div align="center">

### Rust & systems developer — I build tools that get out of the way

[![Rust](https://img.shields.io/badge/Rust-CE422B?logo=rust&logoColor=white)](#)
[![Tokio](https://img.shields.io/badge/Tokio-000000?logo=rust&logoColor=white)](#)
[![SQLite](https://img.shields.io/badge/SQLite-003B57?logo=sqlite&logoColor=white)](#)
[![Bash](https://img.shields.io/badge/Bash-4EAA25?logo=gnubash&logoColor=white)](#)
[![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?logo=powershell&logoColor=white)](#)
[![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)](#)
[![Linux](https://img.shields.io/badge/Linux-FCC624?logo=linux&logoColor=black)](#)

</div>

---

My work starts the same way almost every time: a workflow that technically works but **drags** —
five processes glued together with shell scripts, a pipeline that freezes the terminal every time it
runs, a tool that needs six packages installed before it does anything useful.

I rebuild those as **single, self-contained binaries** that are fast enough that you stop thinking
about them. Concurrency where it actually removes waiting, embedded storage instead of external
services, and zero runtime dependencies wherever it's achievable.

### What I work with

| | |
|---|---|
| **Languages** | Rust, Bash, Python, Lua, SQL, PowerShell |
| **Async & concurrency** | `tokio`, bounded task fan-out, channel-based architectures, safe async ↔ blocking-thread boundaries |
| **Terminal UIs** | `ratatui`, `crossterm`, responsive layouts, theming, keyboard-first UX |
| **Data & storage** | SQLite (embedded), schema migrations, backup strategies, data-retention policies |
| **Networking** | `reqwest` + rustls, concurrent HTTP fan-out, feed/XML/HTML parsing |
| **Cross-platform** | Linux, macOS, Windows — platform-agnostic code, per-OS install tooling |
| **Practice** | Unit + integration tests, `clippy`-clean code, documented architecture decisions |

### Featured project — [dnews](https://github.com/ret3030/dnews)

A terminal RSS reader with full Reader View, in **one native Rust binary**.

- **Started as a shell stack** — bash + newsboat + fzf + rdrview + pandoc + a Lua filter + a Python
  colorizer, wired together with subprocess calls and inline SQL.
- **Rewrote it from scratch in Rust.** Feed fetching, storage, article extraction, and rendering now
  happen inside one process, with no runtime dependencies at all.
- **Made reloading actually concurrent** — up to 16 feeds fetched in parallel behind a semaphore,
  results funnelled through a single writer thread that owns the SQLite connection, so the UI never
  blocks on network or database work.
- **Built a real reading experience in a terminal** — Mozilla Readability extraction, a responsive
  split layout that collapses gracefully on narrow terminals, live search, bookmarks, automatic
  pruning, and rolling database backups.
- **Ships on all three major platforms** from a single platform-agnostic codebase — rustls instead of
  system TLS, bundled SQLite instead of a system library, with native installers for both bash and
  PowerShell.

### How I work

- **Rewrites over patches** when the architecture is the problem — but only after the seams are
  demonstrably the bottleneck.
- **No blocking work on the hot path.** If it touches the network or the disk, it goes to a task and
  reports back over a channel.
- **Decisions get documented**, including the ones that look wrong at a glance — the next person to
  read the code (usually me) deserves to know why.
- **Details are the product.** Text selection that still works, colors that stay stable between runs,
  a layout that survives a 60-column terminal.

<div align="center">

☕ [Buy me a coffee](https://buymeacoffee.com/ret3030)

</div>
