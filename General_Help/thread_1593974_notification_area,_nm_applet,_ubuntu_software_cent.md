---
title: "notification area, nm applet, ubuntu software center suddenly all kinds of messed up"
date: 2010-10-11
forum: General Help
---

### Post by Supersonic Doom on 2010-10-11
The notification area in my systray is suddenly empty after upgrading from 10.04 amd64 to 10.10 amd64.
The nm-applet can be made to appear if I use a terminal to run it, without that terminal running nm-applet specifically, I will have no internet with only one exception.

If I edit... the name of the file evades me, but it's the one with auto loopback, and if it doesn't have autoeth0 or autowlan0 in it then the network manager picks them up. If I add the autoeth0 lines to that file, then I can get internet through an ethernet connection. but not otherwise unless I have the aforementioned terminal running.

gksudo gedit /etc/networkmanager/nm-system-settings.conf
opens blank, but if you navigate to it manually, it shows that the file is intact, and set to manage=true.

The battery applet can be made to appear in the notification area as well, but only if I go into the power management menu and change when to display an icon, even if it's just to another setting and back, with no confirmation between.

Neither of these appear on startup as they did not but 2 days ago.

Ubuntu software center doesn't work either. It will open fine, but if you try to install or remove anything, the button will either turn gray when pressed or hang gray after it's pressed, in neither case will it install or remove a package. Synaptic package manager still works however, and I can add or remove packages without trouble in that program.

I'm still pretty new to linux, but I've been researching for a couple days now on how to fix my problem and it seems to me to be bigger than the sum of its parts. Some help from more experienced users than I would be much appreciated.

edit: Also, I've purged, removed, and re-installed all these items to no effect

---

### Post by Supersonic Doom on 2010-10-21
Login switched default to safe mode, severely restricting my ability to use internet applets, disabling startup programs, disabling my notification area, and generally making things difficult.spread the work to check that you're logging into gnome desktop and not gnome desktop (safe mode) as a solution to a lot of these tray problems I've seen pop up? (I've never vouluntarily logged into safe mode, nor switched it over. The default snuck its way in and I only caught it by chance)

---

