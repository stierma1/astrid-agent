# Astrid MCP server

Astrid's stdio MCP server is a supported way to use Astrid from clients such
as Claude Code or Codex. Run it from an environment where Astrid is installed:

```sh
python -m astrid.mcp_server
```

Configure your MCP client to start that command as a stdio server. It exposes
the product CLI commands generated from Astrid's argparse parsers, an `invoke`
tool for admitting capability runs, and pack skills as MCP prompts. The skills
are also available through the `skills_list` and `skill_get` tools.

Path arguments refer to the disk where the MCP server runs. Arguments whose
CLI parser type is `Path` take file text: the server writes that text to a
temporary file and passes its path to the CLI. Other path strings keep their
normal local path meaning.

Timeline renders always run detached. After `invoke` or a render returns a
task ID, poll it with `tasks_show`; the blocking `tasks_follow` command is not
exposed over MCP.
