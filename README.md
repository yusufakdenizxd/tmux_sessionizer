# tmux-sessionizer

A smart directory navigator and tmux session manager that helps you quickly navigate between your project directories and automatically creates/switches to tmux sessions.

## Features

- 🚀 Navigate to your most important directories with fuzzy search
- 🔄 Instantly create or switch to tmux sessions for your projects
- 🗂️ Organize directories in customizable categories with different search depths
- ⌨️ Configure keyboard shortcuts for quick access to specific directory groups

## Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/yusufakdenizxd/tmux_sessionizer
   ```

2. Make the script executable:

   ```bash
   chmod +x /path/to/tmux-sessionizer.sh
   ```

## Dependencies

- [tmux](https://github.com/tmux/tmux)
- [fzf](https://github.com/junegunn/fzf)

## Usage

Simply run the script:

```bash
./tmux-sessionizer
```

Or add to tmux config

```
bind-key t run-shell "/path/to/tmux-sessionizer.sh"
```

## Configuration

Edit the script and modify the `CATEGORIES` array to customize your directory groups:

```bash
CATEGORIES=(
  "Default:ctrl-n|1|$HOME/work $HOME/dev $HOME/github"
  "Config:ctrl-c|1|$HOME/dev/dot-config"
  "Leetcode:ctrl-l|1|$HOME/leetcode"
  "Playground:ctrl-p|2|$HOME/playground/javascript $HOME/playground/python $HOME/playground/go"
)
```

Each entry follows this format:

```
"CategoryName:keyboard-shortcut|search-depth|space-separated-list-of-directories"
```

### Additional Configuration Options

- `ALL_DIRS_BINDING`: Keyboard shortcut and name for showing all directories
- `FZF_POSITION`: Position and size of the FZF window
- `FZF_PROMPT`: Custom prompt for the FZF interface
- `FZF_LAYOUT`: FZF layout style
- `SHOW_HEADER`: Whether to show keyboard shortcut help in the header

## How It Works

1. The script presents an FZF interface with directories from your configured categories
2. When you select a directory, the script:
   - Creates a new tmux session named after the directory if it doesn't exist
   - Attaches to an existing session if it already exists
   - Sets the working directory to your selected directory

## License

MIT

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request
