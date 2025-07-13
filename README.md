# Basic Setup Claude Hooks

Production-ready Claude Code hooks for Next.js projects. This is a test repository built on [claude-code-hooks-mastery](https://github.com/disler/claude-code-hooks-mastery).

## Features

- **Security**: Blocks dangerous commands (`rm -rf`, `.env` access, `npm run build`)
- **Code Quality**: Automatic ESLint and Prettier checks on file edits
- **Audio Notifications**: TTS alerts for task completion and user input requests
- **Comprehensive Logging**: All hook events logged to `logs/` directory
- **Zero Configuration**: Works immediately after setup

## Quick Setup

```bash
# Navigate to your project
cd /path/to/your/project

# Install hooks
~/basic-setup-claude-hooks/setup.sh

# Start Claude Code
claude-code
```

This creates a `.claude` symlink and `logs/` directory in your project.

## Requirements

- [Astral UV](https://docs.astral.sh/uv/) - Python package manager
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) - Anthropic's CLI

## Configuration

Optional environment variables in your `.env`:

```bash
# Personalized notifications
ENGINEER_NAME="Your Name"

# Dynamic completion messages
OPENAI_API_KEY=your_openai_key
ANTHROPIC_API_KEY=your_anthropic_key

# Code quality automation
HOOK_LINT_ENABLED=true
HOOK_PRETTIER_ENABLED=true
```

## Logging

Hook events are logged in `logs/`:
- `pre_tool_use.json` - Tool execution attempts
- `post_tool_use.json` - Tool execution results  
- `notification.json` - User notifications
- `stop.json` - Task completions
- `chat.json` - Conversation transcript

## File Structure

```
.claude/
├── settings.json              # Claude Code configuration
└── hooks/
    ├── pre_tool_use.py        # Security & logging
    ├── post_tool_use.py       # Results & logging
    ├── notification.py        # User alerts
    ├── stop.py                # Completion handling
    ├── subagent_stop.py       # Subagent completion
    └── utils/
        ├── tts/
        │   └── pyttsx3_tts.py # Local text-to-speech
        └── llm/
            ├── oai.py         # OpenAI completion messages
            └── anth.py        # Anthropic completion messages
```

## Troubleshooting

**Broken symlink:**
```bash
rm .claude && ~/basic-setup-claude-hooks/setup.sh
```

**Missing logs:**
```bash
mkdir -p logs
```

**Dependencies:**
```bash
uv --version && claude-code --version
```

---

Built for production use with Docker workflows and Next.js projects.