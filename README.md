# Laptop

Script to set up a macOS laptop for development.

It can be run multiple times on the same machine safely. It installs, upgrades, or skips packages based on what is already installed. If individual formulae or casks fail, the script logs a warning and continues with the rest of the setup.

## Install

Download, review, then execute the script:

```sh
curl --remote-name https://raw.githubusercontent.com/samcdavid/laptop/master/mac
less mac
sh mac 2>&1 | tee ~/laptop.log
```

## What it sets up

**Homebrew** formulae:

| Category | Packages |
|---|---|
| Unix | git, git-lfs, openssl@3, rcm, tmux, tmuxinator, tpm, watchman, zsh, fish |
| GitHub | gh |
| Image processing | imagemagick, vips |
| Languages / package managers | asdf, yarn |
| Databases | postgresql@17, redis |
| Cloud / infrastructure | awscli, circleci, nomad |
| Dev tools | chroma, cmake, colordiff, direnv, ffmpeg@6, fswatch, fzf, jq, libxslt, llvm@11, miller, mkcert, neovim, pipx, ripgrep, tree, unixodbc, websocat, wget, wxwidgets, yt-dlp, zq |
| Fun | cowsay, figlet, fortune, lolcat |

**Homebrew** casks:

1password, Altair GraphQL Client, Chromedriver, Claude, Docker Desktop, Font Hack, Font JetBrains Mono, Font JetBrains Mono Nerd Font, Font Menlo for Powerline, Font SF Mono for Powerline, gcloud CLI, Ghostty, GPG Suite, Insomnia, Linear, Loom, MacDown, Muzzle, ngrok, Notion, ProtonVPN, Rectangle, Session Manager Plugin, Tuple, Visual Studio Code

**Dotfiles ([samcdavid/dotfiles](https://github.com/samcdavid/dotfiles)):**

- Clones dotfiles repo and runs `rcup` to create symlinks
- Includes fish config, neovim (LazyVim), tmux, ghostty, git, psqlrc, tmuxinator sessions

**Git:**

- Configures git-lfs hooks
- Generates a GPG key for commit signing
- Authenticates with GitHub and uploads the GPG key

**Shell:**

- Sets [fish](https://fishshell.com/) as the default shell
- Installs [Oh My Fish](https://github.com/oh-my-fish/oh-my-fish) and all packages from the OMF bundle

**Tmux:**

- Installs TPM plugins automatically

**Version management ([asdf](https://asdf-vm.com/)):**

- Plugins: ruby, nodejs, erlang, elixir, python, golang, terraform
- Installs all language versions from `~/.tool-versions`

## Customize

The script will source `~/.laptop.local` if it exists. Put any additional setup there.

## Manual steps

After running the script:

- Setup 1Password

## Credits

Originally based on [thoughtbot's laptop](https://github.com/thoughtbot/laptop) script. See the [LICENSE](LICENSE) file for details.
