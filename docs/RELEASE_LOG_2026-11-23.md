# AI Optimizer Release & Ecosystem Operations Log

**Date:** November 23, 2026  
**Repository:** [shivam-app-developers/ai-optimizer](https://github.com/shivam-app-developers/ai-optimizer)  
**Namespace:** `io.github.shivam-app-developers/ai-optimizer`  
**Current Version:** `0.1.1`

---

## 1. Package Health & Registry Audit

- **Monorepo Layout**:
  - Root `ai-optimizer`: Monorepo container (`private: true`), not published directly to npm.
  - `@ai-optimizer/core`: Main MCP server executable (`ai-optimizer`).
  - `@ai-optimizer/init`: Automated setup CLI (`npx @ai-optimizer/init`).
  - `@ai-optimizer/sdk`: Community framework pack developer kit.
  - `@ai-optimizer/context-mode-import`: Configuration translator for `.contextmode`.
  - `apps/landing`: Next.js 15 landing website.

- **npm Download Statistics (as of Nov 23, 2026)**:
  - `@ai-optimizer/core`: **1,207** all-time downloads, **192** last 30 days, **44** last 7 days (~4–7 downloads/day consistently across 162 active days).
  - `@ai-optimizer/init`: ~23 downloads/month.
  - `@ai-optimizer/sdk`: ~19 downloads/month.
  - `@ai-optimizer/context-mode-import`: ~21 downloads/month.

- **Community Baseline**:
  - 0 GitHub stars / 0 forks.
  - Open issues were automated Dependabot dependency bumps; no external community reviews or discussions yet.

---

## 2. Server Verification & Test Health

- **Protocol Negotiation**:
  - Validated local stdio server startup (`node packages/core/bin/ai-optimizer.js`).
  - Successfully negotiated JSON-RPC 2.0 handshake using protocol version `2024-11-05`.
  - Confirmed all 11 registered MCP tools:
    `optimized_read_file`, `optimized_list_files`, `optimized_grep`, `optimized_diagnostics`, `read_symbol`, `strip_bash_noise`, `get_optimizer_config`, `set_optimizer_config`, `budget_status`, `budget_reset`, `optimizer_status`.
- **Live Tool Invocations**:
  - Verified `optimized_list_files` filters noise files while preserving source code.
  - Verified `optimizer_status` correctly reports detected frameworks and cumulative token savings.
- **Automated Test Suite**:
  - Vitest: **171 passed** across 21 test files (`core`: 114, `init`: 21, `context-mode-import`: 30, `sdk`: 6).
  - Next.js: Successfully built 6 static prerendered production routes in `apps/landing`.

---

## 3. Improvements & Version Bump to 0.1.1

- **Community Feedback Prompts**:
  - Updated `packages/init/src/cli.ts` to output GitHub star & issue links upon completing the setup wizard:
    - ⭐ Star us on GitHub: https://github.com/shivam-app-developers/ai-optimizer
    - 💬 Report issues or suggest packs: https://github.com/shivam-app-developers/ai-optimizer/issues
    - 💡 Review savings: Run `optimizer_status`
- **Documentation**:
  - Added "Feedback, Reviews & Community" section to root `README.md`.
- **Telemetry Flexibility**:
  - Updated `packages/core/src/telemetry/client.ts` to check `process.env.AI_OPTIMIZER_TELEMETRY_ENDPOINT` before defaulting to `telemetry.ai-optimizer.dev`.
- **Registry Discoverability**:
  - Added MCP keywords (`mcp`, `model-context-protocol`, `mcp-server`, `context-optimizer`) and git repository link to root `package.json`.
  - Updated `smithery.yaml` command to `npx -y @ai-optimizer/core` for zero-install execution.
- **Version Bump**:
  - Bumped to `0.1.1` across all `package.json` files and `SERVER_VERSION` in `packages/core/src/server.ts`.
  - Formatted all files with Prettier (`npm run format`).

---

## 4. MCP Registry & Directory Operations

### A. Smithery.ai Status

- Documented that Smithery's hosted proxy, CLI, and developer accounts were permanently deactivated on **October 31, 2026** following its acquisition by Arcade.dev.
- Kept `smithery.yaml` updated in the repo for catalog compatibility.

### B. Glama.ai Listing & Claiming

- Server profile is **Live, Claimed, and Verified** at:
  [glama.ai/mcp/servers/shivam-app-developers/ai-optimizer](https://glama.ai/mcp/servers/shivam-app-developers/ai-optimizer)
  - **Title**: `AI Token Optimizer by shivam-app-developers | Glama`
  - **Maintainer**: Claimed by `shivam-app-developers`
  - **Indexed Features**: Automatically indexed all 4 primary tools (`optimized_read_file`, `optimized_list_files`, `optimized_grep`, `optimizer_status`), quickstart guides, and `.claude/settings.json` configuration.
  - **Category**: Placed into Model Context Protocol developer tools alongside related token optimizers.
  - **Community Reviews**: Developers can now star, review, and install the server directly from the Glama hub.

### C. Official MCP Registry (`registry.modelcontextprotocol.io`)

- Updated `server.json` schema to version `0.1.1`.
- Resolved CLI distinction:
  - npm `mcp-publisher` is an unrelated third-party package.
  - Real official tool is the Go binary released on [modelcontextprotocol/registry](https://github.com/modelcontextprotocol/registry).
- Downloaded and ran official `mcp-publisher.exe` (v1.8.15):
  - Validated `server.json` against `https://registry.modelcontextprotocol.io/v0/validate` (Passed).
  - Authenticated with GitHub OIDC (`shivam-app-developers`).
  - Published version `0.1.1` to the official registry.
- **Live Verification**:
  - Verified registry API at `https://registry.modelcontextprotocol.io/v0/servers?search=ai-optimizer`.
  - Confirmed entry:
    - Name: `io.github.shivam-app-developers/ai-optimizer`
    - Version: `0.1.1`
    - Status: `active`
    - `isLatest`: `true`
    - Published at: `2026-11-23T09:29:22Z`

---

## 5. Ongoing Reference Commands

### To Re-Publish or Update server.json in Official Registry:

```powershell
.\mcp-publisher.exe validate
.\mcp-publisher.exe publish
```

### To Build and Test Locally:

```bash
npm run build
npm test
```

### To Publish Updated Packages to npm:

```bash
npm login
npm publish -w @ai-optimizer/core --access public
npm publish -w @ai-optimizer/init --access public
npm publish -w @ai-optimizer/sdk --access public
npm publish -w @ai-optimizer/context-mode-import --access public
```
