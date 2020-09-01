# Table of Contents

1.  [Why I did I write this guide?](#org602b926)
2.  [How well it look like?](#org23c08a5)
3.  [Installing dependencies](#orgbdd4fd7)
    1.  [Manjaro/Arch](#org466e3ab)
    2.  [Ubuntu/Debain/Pop<sub>OS</sub>/Deepin/&#x2026;&#x2026;](#org97a70f7)
4.  [Enabling Rounded Corners](#org3a6d975)
    1.  [Running picom on startup automatically:](#org97e256a)
5.  [Installing Themes from kde store](#org98d6a3e)
6.  [Installing Konsole Scheme](#org81ac136)
7.  [Installing Icons](#org82b63ee)
8.  [Configuring the panel](#org09d0784)

9.  [Wallpaper](#orgd7a0f94)
10. [Final words](#orgee5b22f)

(Theme by u/DarkReaper231)

<a id="org602b926"></a>

## Why I did I write this guide?

Recently u/DarkReaper231 posted a nice [monochrome theme](https://www.reddit.com/r/unixporn/comments/iizjgi/i3gaps_went_monochrome/) on unixporn. His config
works in i3-gaps only, so I decided to write a short guide to help port it to
KDE plasma.

<a id="org23c08a5"></a>

## How well it look like?

![img](/images/monochrome-plasma/final-rice.png)

<a id="orgbdd4fd7"></a>

## Installing dependencies

<a id="org466e3ab"></a>

### Manjaro/Arch

    $ sudo pacman -Syu yay # This line is Only for Manjaro users (Arch users know what to do btw :P)
    $ yay -Sy picom-ibhagwan-git

<a id="org97a70f7"></a>

### Ubuntu/Debain/Pop<sub>OS</sub>/Deepin/&#x2026;&#x2026;

A guide on how to install picom-ibhagwan is [on his repo](https://github.com/ibhagwan/picom)
If you don&rsquo;t feel like reading there then here is the untested summary of the
instructions

    sudo apt update && sudo apt upgrade

    # this is one line lol
    sudo apt install libxext-dev libxcb1-dev libxcb-damage0-dev libxcb-xfixes0-dev libxcb-shape0-dev libxcb-render-util0-dev libxcb-render0-dev libxcb-randr0-dev libxcb-composite0-dev libxcb-image0-dev libxcb-present-dev libxcb-xinerama0-dev libpixman-1-dev libdbus-1-dev libconfig-dev libgl1-mesa-dev  libpcre2-dev  libevdev-dev uthash-dev libev-dev libx11-xcb-dev

    cd /tmp
    git clone https://github.com/ibhagwan/picom.git && cd picom

    git submodule update --init --recursive
    meson --buildtype=release . build
    ninja -C build

    ninja -C build install #if it fails run it with sudo

<a id="org3a6d975"></a>

## Enabling Rounded Corners

Picom is the &ldquo;composite manager&rdquo; that is going to make windows rounded. It
requires a little bit of setup to make it work.

- First we need to disable the current composite manager which came by default
  with KDE Plasma.

Open your settings > Hardware Section > Display and Login > Compositor >

From there disable Compositor on start up
![img](/images/monochrome-plasma/disable-compositor.png)

- Next Logout and log back for the changes to take effect
- Copy and paste the picom config from [.config/picom.conf](https://raw.githubusercontent.com/westofer/monochrome-theme/master/.config/picom.conf) into
  ~/.config/picom.conf. or use this command if you feel too lazy to do things
  manually

      # will overwrite your current config
      curl https://raw.githubusercontent.com/westofer/monochrome-theme/master/.config/picom.conf -o ~/.config/picom.conf

- Run picom to test the rounded corners :)
  You should see something similar to ![img](/images/monochrome-plasma/rounded-corners.gif)

  Note: if you get an error stating &ldquo;Another Composite Manager is already
  running&rdquo;, try running \`pkill picom\` and repeating the first step ;)

<a id="org97e256a"></a>

### Running picom on startup automatically:

- You probably don&rsquo;t want to type \`picom\` on each startup, so instead we
  are going to create a script that runs on startup. The process is simple and
  and can be done by running this one liner to do most of the process automatically.

      mkdir -p ~/bin/ && echo "picom &" > ~/bin/autostart.sh && chmod +x ~/bin/autostart.sh

Now add this file to autostartup by opening \`settings >> Startup and shutdown >>
Autostart >> Add Script >> Type &ldquo;~/bin/autostart.sh&rdquo;\`

Here is a gif for reference:
![img](/images/monochrome-plasma/autostart.gif)

\***\*Now Login to test it\*\***

Yay! This was the hardest part!

<a id="org98d6a3e"></a>

## Installing Themes from kde store

From the settings >> Global Themes >> Get New Global themes >> Search for
&ldquo;monochrome&rdquo; >> install and apply

<a id="org81ac136"></a>

## Installing Konsole Scheme

    From the konsole >> settings >> manage profiles >>
    New Profile >> Appereance >> Get New >>
    Search for "Monochrome" >> Install >> exit >>
    Select Monochrome Konsole >>
    exit and set the new profile as default.
    (restart konsole for changes to take effect)

Demo:

![img](/images/monochrome-plasma/konsole-colorscheme.gif)

You might also want to change the margin size:

![img](/images/monochrome-plasma/margin-size.png)

You might also want to hide the menu bar

![img](/images/monochrome-plasma/menubar.png)

Another option is to hide the title bat

(remeber that you can drag windows without a title bar while holding ALT)

![img](/images/monochrome-plasma/titlebar.png)

<a id="org82b63ee"></a>

## Installing Icons

This should be easy too

settings >> icons >> add icons >> install icon >> use

![img](/images/monochrome-plasma/installing-icons.gif)

you get the idea

<a id="org09d0784"></a>

## Configuring the panel

First we need to set the panel to be flexable.

![img](/images/monochrome-plasma/panel-flexable.png)

Then click edit panel

![img](/images/monochrome-plasma/panel-edit.png)

On the right we should have &rsquo;more options&rsquo; button, click that then center the panel

![img](/images/monochrome-plasma/panel-center.png)

On the edge of the panel you should be able to resize the panel as in this
picture

![img](/images/monochrome-plasma/panel-resize-handle.png)

The whole process looks like this:

![img](/images/monochrome-plasma/panel-resize.gif)

press ESC to exit and save

<a id="orgd7a0f94"></a>

# Wallpaper

[here is the wallpaper](https://github.com/DarkReaper231/blacknwhite/blob/master/background.jpg)

<a id="orgee5b22f"></a>

# Final words

![img](/images/monochrome-plasma/final-rice.png)

Notice that I didn&rsquo;t include any font configuration, it should be something
simple that you can do :). This applies to using css stylesheets for firefox.

For the Dolphin File Manager I used <F9> and alt+m to hide the side panel and
menu bar respectively. An alternative to dolphin would be nautilus.

The Picture included neofetch, cava and tty-clock (press c to center the clock)

to resize a terminal with nobars >> alt + right click

Hope you enjoy your rice :)
