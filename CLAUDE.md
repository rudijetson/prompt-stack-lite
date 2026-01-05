# pstack CLI

Package manager for Prompt Stack - install stacks, manage secrets, run workflows.

## Commands

```bash
pstack search <query>     # Search registry
pstack search --all       # List all available packages
pstack install <pkg>      # Install a stack/runtime/tool
pstack remove <pkg>       # Uninstall a package
pstack list [kind]        # List installed (stacks, runtimes, tools, agents)
pstack run <stack>        # Run a stack
pstack secrets            # Manage secrets
pstack update [pkg]       # Update packages
pstack doctor             # Check system health
```

## Architecture

```
src/index.js → commands/*.js
      ↓
@prompt-stack/env         # PATHS, platform detection
@prompt-stack/core        # db, installer, resolver
@prompt-stack/registry-client  # fetch from GitHub
      ↓
~/.prompt-stack/
├── stacks/               # Installed MCP stacks
├── runtimes/             # Node, Python, Deno
├── tools/                # ffmpeg, ripgrep, etc.
├── agents/               # Claude, Codex, Gemini CLIs
└── prompt-stack.db       # Shared with Studio
```

## Registry

- Index: `https://raw.githubusercontent.com/prompt-stack/registry/main/index.json`
- Binaries: `https://github.com/prompt-stack/registry/releases/download/v1.0.0/`
- Local dev fallback: `/Users/hoff/dev/prompt-stack/registry/index.json`

## Development

```bash
cd /Users/hoff/dev/prompt-stack/cli
npm link                  # Add pstack to PATH
pstack search --all       # Test
```
