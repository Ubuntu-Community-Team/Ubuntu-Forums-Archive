---
title: "Put icon in the system tray and run bash command when clicked"
date: 2010-07-29
forum: General Help
---

### Post by chrisharrington on 2010-07-29
Hi,

I am trying to find a way to put an icon in the system tray and run a bash command every time I click on the icon.

Purpose: I want to set up a system tray icon that will hide/unhide the desktop when clicked, much as would the standard desktop panel plugin for the various panel apps like lxpanel, gnome panel, etc.

Why don't I just use a panel app?

I am using a very reduced install of Ubuntu Lucid oriented towards first time PC users on very old hardware, using Openbox as the window manager and [Tint2]("http://code.google.com/p/tint2/") with [lxlauncher]("http://wiki.lxde.org/en/LXLauncher") instead of a panel, the latter both compiled from latest source for some slight customization. Tint2 is a taskbar that also features a built in clock applet and system tray which I have chosen after examining basically all other alternatives and chosen for its light footprint and customization. It gives me everything I need except a single click hide/show-desktop feature or a halt/reboot/logout menu. lxlauncher is a very lightweight alternative to the Ubuntu Netbook Remix netbook-launcher (and/or netbook-launcher-efl) package that conforms to the freedesk specifications and occupies all free deskspace other than tint2, under all other windows. I used the freedesk specs to set up a "shutdown" menu category and created shutdown.desktop reboot.desktop and logout.desktop files in the category to add that feature, using dbus commands for the first two and 'openbox --exit' for the latter.

I set the openbox config to open all app windows maximized with no decoration, so each app takes up the whole screen other than tint2 and can only be closed by right clicking on its icon in tint2 or by its file->Quit menu.

This gives me a kind of OLPC for grown ups with no computer experience. In other words, for people who don't know what a desktop or window is. This is similar to the Ubuntu Netbook Remix except that in UNR they superimpose the window decorations over the gnome panel so you can still close the window.

However, the one problem here is that to see lxlauncher when one has several apps running, one has to click on each app in tint2 to minimize it. I would like to add a system tray icon to make this possible with one click without adding too much more overhead to the existing setup.

Here is a screen cap of the desktop:

[IMG]http://awanowa.jp/projects/awaos/awaos.jpg[/IMG]

BTW, I will use wmctrl to test the desktop visibility state and toggle it using this bash command:
test 'wmctrl -m | grep ON' && wmctrl -k on || wmctrl -k off

So any ideas about how to get an icon in the system tray and run the above command when clicked will be appreciated :)

P.S. I've looked at 'zenity --notification --listen' but running a command when the icon is clicked in this case is a [pending feature]("http://live.gnome.org/Zenity") for the app and not yet implemented. My last resort will be to learn C and try that.

---

### Post by chrisharrington on 2010-08-03
I've decided to take the memory hit and use lxpanel instead of tint2. lxpanel can be configured to look similar to my tint2 settings (with the exception of the nice task tray highlighting).

However, that still doesn't answer the question. It would be good to know of a solution for future reference so I won't mark this as solved for now.

---

### Post by thil77 on 2010-08-12
have added some tooltip in FAQ

[http://code.google.com/p/tint2/wiki/FAQ?ts=1281639174&updated=FAQ#Adding_a_%27show_desktop%27_button](http://code.google.com/p/tint2/wiki/FAQ?ts=1281639174&updated=FAQ#Adding_a_%27show_desktop%27_button)

---

