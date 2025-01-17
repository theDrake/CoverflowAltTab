# CoverflowAltTab

<a href="https://extensions.gnome.org/extension/97/coverflow-alt-tab/"><img src="https://img.shields.io/badge/Download-extensions.gnome.org-4a86cf.svg?logo=gnome&style=plastic" /></a>
<a href="https://hosted.weblate.org/engage/coverflow-alt-tab/"><img src="https://img.shields.io/weblate/progress/coverflow-alt-tab?style=plastic&logo=weblate&color=2ECCAA&label=Use%20Weblate%20for%20translation">
</a>

CoverflowAltTab is an Alt-Tab replacement available as an extension for [Gnome-Shell](https://www.gnome.org/). It lets you Alt-Tab through your windows in a cover-flow manner.

![Screenshot](img/screenshot.png)

## Installation

Easiest way to install the extension is via [extensions.gnome.org](https://extensions.gnome.org/extension/97/coverflow-alt-tab/), the official Gnome extension platform. Head over there and install CoverflowAltTab with one click by toggling the switch on the site.

If you want to install it manually (e.g. to test the latest, probably unstable code):

1. Download the zip file by clicking the zip button on the upper part of this page and extract it (or you can just clone the repository).

2. Install the extension locally by running the following command in Terminal:

    - `make all`

## Usage

### Manual

This extension uses the following key bindings (you can change or disable them in your system settings):

-   "Switch applications" (usually **Alt+Tab**): Cycle through windows grouped by application
-   "Switch windows" (usually undefined): Cycle through windows 
-   "Switch windows of an application" (usually **Alt+\`**): Cycle through all windows from the current application from all workspaces

Many users prefer a flat list of windows over a list grouped by application and so prefer the **Alt+Tab** key combination for "Switch windows". 
Such a user could change the keybindings as in the table:

| Action              | Default Shortcut | Recommended Shortcut |
|---------------------|------------------|----------------------|
| Switch applications | **Alt+Tab**      | **Super+Tab**        |
| Switch windows      | None             | **Alt+Tab**          |


All of the shortcuts with **Shift** key pressed cycles backward.

-   Hit **Esc** to cancel.
-   Hit **d** to hide all windows and show the desktop.

You can also use the **arrow keys**, **mouse wheel**, or **trackpad** to cycle through the windows.

### DBus

The extension exports a DBus interface. This can be used, for example, with the Custom Hot Corners - Extended extension to launch the switcher by moving to a corner.

The interface has four methods: 

1. The `launch` method which takes a string that should be either `windows` or `applications`

```
gdbus call --session --dest org.gnome.Shell.Extensions.Coverflowalttab --object-path /org/gnome/Shell/Extensions/Coverflowalttab --method org.gnome.Shell.Extensions.Coverflowalttab.launch "windows"
```

2. The `next` method which takes no arguments.
3. The `previous` method which also takes no arguments.
4. The `select` method breaks out of the switcher.


## Customization

To change the keybindings, use your system keyboard settings! See above for the used keybindings and change them to your desire.

To access preferences you can:

  - Open the Extensions tool. You should find it in your system menu
  - Click the preferences button on [extensions.gnome.org](https://extensions.gnome.org/local/)
  - run `gnome-extensions prefs CoverflowAltTab@palatis.blogspot.com` inside a terminal

This will show you a preference dialog where you can change the settings to your needs.

## Troubleshooting

### I have to manually enable the extension every time I start my computer.

Many GNU/Linux distributions, namely Debian and its derivatives, install some extensions by default. Among those it's very common to find the [AlternateTab](https://extensions.gnome.org/extension/15/alternatetab/) extension; unfortunately, both AlternateTab and CoverflowAltTab are alt-tab replacements, and so they conflict: AlternateTab is usually the winning one, and so CoverflowAltTab appears as enabled but does not work as expected.

All you need to do to be able to enjoy the CoverflowAltTab eyecandy is to disable AlternateTab (or any other alt-tab replacement extension)! To do that, you might use the Extensions tool or visit https://extensions.gnome.org/local/. CoverflowAltTab might need to be disabled and re-enabled after you disable the offending extension(s), but this time it'll continue working even after a reboot.

## License

CoverflowAltTab is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

See the [contributors list](CONTRIBUTORS.md) and [a copy of the license](COPYING).
