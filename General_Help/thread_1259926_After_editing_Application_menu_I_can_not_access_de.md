---
title: "After editing Application menu I can not access desktop."
date: 2009-09-06
forum: General Help
---

### Post by pyjimbo on 2009-09-06
After renaming the default menus to what I want, added some of my own, and remove all excess items in all menus (the ones with no checkmarks), my computers only show a background wallpaper after login. [I blamed Ubuntuone for this, poor little guy (so that is not actually solved).]("http://ubuntuforums.org/showthread.php?t=1259022") [Here is another thread I had.]("http://ubuntuforums.org/showthread.php?t=1259625")

I just reproduced this on a third machine (Dell P4) after a clean install. I know it is this. What am I doing to break this? Is it a bug?

I have this problem on a late 2006 Macbook, Sony Vaio P4, and Dell P4.

**How do I restore/fix my application menu?** :confused:

---

### Post by NoaHall on 2009-09-07
Ah, so you have no panels? Try running "gnome-panel"

---

### Post by pyjimbo on 2009-09-07
> **NoaHall said:**
> Ah, so you have no panels? Try running "gnome-panel"

I logged into Failsafe Terminal session from the login screen, then ran gnome-panel. It worked and got me to see the GUI in the default look and feel. I was able to get this from the terminal after running gnome-panel.

```
(gnome-panel:3950): GConf-WARNING **: Directory '/apps/panel/toplevels/bottom_panel_screen1/screen' was not being monitored by GConfClient 0x8aa3f28

(gnome-panel:3950): GConf-WARNING **: Directory '/apps/panel/toplevels/top_panel_screen1/screen' was not being monitored by GConfClient 0x8aa3f28
**(gnome-panel:3950): DEBUG: Adding applet 0.
**(gnome-panel:3950): DEBUG: Initialized Panel Applet Signaler.
**(gnome-panel:3950): DEBUG: Adding applet 1.
**(gnome-panel:3950): DEBUG: Adding applet 2.
**(gnome-panel:3950): DEBUG: Adding applet 3.
**(gnome-panel:3950): DEBUG: Adding applet 4.
**(gnome-panel:3950): DEBUG: Adding applet 5.

(gnome-panel:3950): Gdk-WARNING **: /build/buildd/gtk+2.0-2.16.1/gdk/x11/gdkdrawable-x11.c:878 drawable is not pixmap or window

(gnome-panel:3950): libglade-WARNING **: Unxpected element <requires-version> inside <glade-interface>.
**(gnome-panel:3950): DEBUG: Adding applet 6.
**(gnome-panel:3950): DEBUG: Adding applet 7.
**Message: Could no connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

**(gnome-panel:3950): WARNING **: Could not connect to session manager: Could not get owner of name 'org.gnome.SessionManager': no such name

```

I transcribed it by hand with text editor, I could not copy and paste out of xterm.

---

### Post by TDK800 on 2009-09-30
I am having the exact same problem on 9.04 after editing menus last night it happened on 9.10 also few weeks ago and re-installed 9.04. 

This is a critical problem!


UPDATE:
rm -rf /home/Yourusername/.local 
fixes this (My thanks to board member oOarthurOo)

It is this bug, that has been closed for some reason:
[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/378422](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/378422)

-------
Member  Brandon Williams explains problem in more detail: 

> OK ... here's what's going on ...

If you delete an item from one of the menus using alacarte, an <appname>.desktop file is created in ~/.local/share/applications/ with a line that says 'Hidden=true'. For some reason, if a desktop file for an application in your local apps directory has this flag, the app won't be started when you log in, probably because it will be ignored when gnome searches for the application, and thus gnome doesn't know what command to run. If you delete Panel from the menu, the resulting 'Hidden=true' flag in gnome-panel.desktop will prevent gnome-panel from being found and started at login. Likewise for nautilus, and gnome-wm. If you delete any of these core components, each of which is specified in gconf as require components for the gnome desktop, you will lose functionality as a result.

When this problem occurs, simply delete the bad .desktop file. For example, if the panel doesn't start, then 'rm -f ~/.local/share/applications/gnome-panel.desktop'. If you're uncertain which deletion is causing trouble for you, then 'grep Hidden=true ~/.local/share/applications/*.desktop' to get a list of all the .desktop files that are candidates.

To avoid this in the future, simply avoid deleting items that represent important desktop elements from the menu. If you really just can't help yourself and that item that only shows up in the menu editor is too much to bear :-) ... try adding the associated application to your 'Startup Applications'. I don't know if that will work, but it's worth a try if it's important to you.

FWIW, I agree that this is a real bug. Deleting an item from the menu should not lead to gnome's refusal to start the app at login..."

---

