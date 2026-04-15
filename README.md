# Forge Skills Plugin Bundle

Plugin-style packaging for the Forge App Builder skill, with shared MCP configuration for Atlassian Forge.

## Included

- `skills/forge-app-builder` - Forge app builder skill
- `.mcp.json` - Shared MCP server config (`https://mcp.atlassian.com/v1/forge/mcp`)
- `plugin.json` - GitHub Copilot CLI plugin manifest
- `.cursor-plugin/plugin.json` - Cursor plugin manifest
- `.claude-plugin/plugin.json` - Claude plugin manifest
- `.codex-plugin/plugin.json` - Codex plugin manifest
- `gemini-extension.json` - Gemini extension manifest

## Install

### Cursor

The Cursor manifest explicitly sets `"mcpServers": "./.mcp.json"`, so skill + Forge MCP are configured together.

Use Cursor plugin install from source with this repository.

Then restart Cursor (or run "Developer: Reload Window") if needed.

### Claude

Use Claude plugin install from source with this repository (or clone as a skill fallback under `~/.claude/skills`).

Claude Code auto-discovers `.mcp.json` at plugin root, and this plugin also declares `"mcpServers": "./.mcp.json"` explicitly in `.claude-plugin/plugin.json`.

### Gemini CLI

Install from source URL:

```bash
gemini extensions install <repo-url>
```

`gemini-extension.json` will register the Forge MCP server.

### Codex

The Codex manifest uses `"mcpServers": "./.mcp.json"` and `"skills": "./skills/"`.

Install through a Codex marketplace entry (repo or personal) that points `source.path` at this plugin directory, then restart Codex.

### GitHub Copilot CLI

This repository follows the Copilot CLI plugin layout: root `plugin.json` plus optional `.mcp.json` and `skills/`. See [Creating a plugin for GitHub Copilot CLI](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/plugins-creating).

Install locally from a checkout of this repo (path is the plugin root):

```bash
copilot plugin install .
```

Re-install after local changes (Copilot caches plugin components). Then verify with `copilot plugin list` or `/plugin list` in an interactive session.

## Notes

- Marketplace listing is optional for source installs; each marketplace has separate review/approval rules.
- MCP server registration does not bypass provider authentication. If Forge MCP requires auth, users will still complete the auth flow.

## Skill Documentation

See `skills/forge-app-builder/README.md` and `skills/forge-app-builder/SKILL.md` for workflow details.
