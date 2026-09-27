# my-mcp-server

A small MCP server exposing my notes to Claude Desktop

Side project, maintained when I have time.

## Installation

```bash
pip install -r requirements.txt
```

## What it does

- Five tools: add / get / update / delete / list notes
- Includes a Claude Desktop config snippet with absolute paths
- Notes path set by MCP_NOTES_FILE or --notes-file
- A missing note raises instead of returning the string 'not found'
- Every tool carries a real docstring, so clients get descriptions
- Atomic saves (temp file + os.replace) behind a write lock

## Examples

```bash
# claude_desktop_config.json  (use ABSOLUTE paths: Claude does not
# run from the repo directory, so a bare "server.py" is not found)
# {
#   "mcpServers": {
#     "notes-box": {
#       "command": "python",
#       "args": ["/abs/path/to/my-mcp-server/server.py"],
#       "env": {"MCP_NOTES_FILE": "/abs/path/to/notes.json"}
#     }
#   }
# }
python server.py --help
```

## Project structure

```text
├── .github/
│   └── workflows/
│       └── ci.yml
├── docs/
│   ├── configuration.md
│   ├── development.md
│   ├── faq.md
│   └── usage.md
├── tests/
│   └── test_notes.py
├── .gitignore
├── CODE_OF_CONDUCT.md
├── CONTRIBUTING.md
├── SECURITY.md
├── requirements.txt
└── server.py
```

## Development

```bash
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
python -m pytest -q
```
