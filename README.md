# Prompier MCP server

Use your [Prompier](https://prompier.com) prompts, skills and apps in your own AI tool.
Prompier is a prompt manager for individuals and teams. This server connects it to
Claude Code, Cursor, VS Code, Claude Desktop and other tools that support remote MCP
servers over HTTP.

This repository holds the documentation for the hosted server. The server itself is
run by Prompier and is not open source.

- Endpoint: `https://prompier.com/mcp` (Streamable HTTP)
- Auth: a connection key sent as a bearer token
- Access: read-only

## Features

- **Your prompt library in any AI tool.** Find prompts, skills and apps by name, fill in
  the variables and get the finished text without copy and paste.
- **Runs on your own AI subscription, with nothing stored.** Prompier builds the prompt
  and your tool runs it. The server never calls a model, and nothing you type or get
  back is stored. Only a usage count is recorded.
- **Read-only and role-aware.** Keys can't change anything. In a team, everyone gets
  approved text only, never drafts, and your role is checked on every call.

## Set up

1. Sign in at [prompier.com](https://prompier.com). You need an Individual or Team plan.
2. Open **Settings → Connect an AI tool** and turn on AI tool access.
3. Click **Create key**. The key starts with `pmm_` and is shown once, so copy it.
4. Add the server to your tool.

Claude Code:

```bash
claude mcp add --transport http prompier https://prompier.com/mcp \
  --header "Authorization: Bearer <your key>"
```

For Cursor, VS Code and Claude Desktop, the same page shows a ready-made snippet.
Restart your tool after adding the server.

## Use cases

- **Run an approved prompt from your coding tool.** Ask for the team's "release notes"
  prompt by name, fill in the variables and run it, without leaving your editor.
- **Keep a team on one reviewed set of prompts.** Members pull the approved version.
  When a prompt is re-approved, everyone gets the change.
- **Use your personal library everywhere.** Connect Cursor at work and Claude Desktop at
  home with separate keys.

## FAQ

**Do I need a paid plan?**
Yes, an Individual or Team plan. On Free you can't create a key.

**Does Prompier run my prompts or see my results?**
No. Prompier builds the prompt and your tool runs it on your own subscription. Nothing
you type or get back is stored. Only a usage count is recorded.

**Can it run prompts with placeholders?**
Yes. You give a value for each field (text, long text or a choice) and Prompier returns
the finished prompt. Optional fields can be left blank, and optional sections are
dropped when blank.

## Who sees what

- In a team, every role sees approved text only.
- A personal workspace sees ready items at their latest version.
- App users (people a team shared apps with) can't connect.
- Apps that need an approver checkpoint aren't supported over MCP yet.

## Keys and security

- A key belongs to one person and one workspace. You can set an expiry (30 or 90 days,
  1 year or never) and revoke it at any time under Settings → Connect an AI tool.
- Changing your password does not revoke a key. Revoke it if you lose a device.
- Team owners and admins can see and revoke every member's keys.
- A key stops working when its person leaves the workspace.
- Treat a key like a password. Never commit it to a repository.

To report a security problem, email <security contact address>.

## Support

Questions or problems: <support address> or [prompier.com](https://prompier.com).

## License

The documentation in this repository is released under CC BY 4.0.
The Prompier name and logo are trademarks of Prompier.
