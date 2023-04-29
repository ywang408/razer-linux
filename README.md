# Razer-Blade-16 Linux Settings

## HiDPI

Fix QT-based apps:

In `/etc/environment`:

```
QT_AUTO_SCREEN_SCALE_FACTOR=1
```

## Nvidia Prime

To switch between using integrated, hybrid, dedicated gpus, install envy control:

```shel
yay -S envycontrol
```

To use Gui to swtich:

- Install gnome-browser-connector:

    ```
    yay -S gnome-browser-connector
    ```

- Install gnome extension from [here](https://extensions.gnome.org/extension/5009/gpu-profile-selector/).

## Rime Input(中文输入法)

Reference: [link](https://www.cnblogs.com/keatonlao/p/12983158.html)

```
pacman -S ibus-rime
```

```
cat /etc/environment
GTK_IM_MODULE=ibus
QT_IM_MODULE=ibus
XMODIFIERS=@im=ibus
```

Rime-ice(雾凇拼音) dictionary:

See this [repo](https://github.com/iDvel/rime-ice).

## Gnome settings

- Add minimize and maximize button: **gnome tweaks**

- Show files in Desktop: See this [extension](https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/).

## ZSH configs

1. Installation
    ```
    sudo pacman -S zsh
    chsh -s $(which zsh)
    ```

2. oh-my-zsh
    ```
    yay -S oh-my-zsh-git
    cp /usr/share/oh-my-zsh/zshrc ~/.zshrc
    ```

3. Starship
   ```shell
   starship preset pure-preset -o ~/.config/starship.toml
   ```

   Add to `~/.zshrc`:

   ```
   eval "$(starship init zsh)"
   export STARSHIP_CONFIG=~/.config/starship.toml
   ```

4. plugins:

   - zsh-autosuggestions:
     ```
     git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
     ```

   - fast-syntax-highlighting
     ```
     git clone https://github.com/zdharma-continuum/fast-syntax-highlighting.git \
       ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/plugins/fast-syntax-highlighting
     ```


## Others

- Open folder while opening vscode

    Check `/usr/share/applications/code.desktop `. The same for opening `kitty` by default.

- Prevent wake up problem after suspend

    ```shell
    sudo systemctl enable nvidia-suspend.service
    sudo systemctl enable nvidia-hibernate.service
    sudo systemctl enable nvidia-resume.service
    ```

