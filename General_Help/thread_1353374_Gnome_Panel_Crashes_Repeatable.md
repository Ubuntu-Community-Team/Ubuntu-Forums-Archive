---
title: "Gnome Panel Crashes Repeatable"
date: 2009-12-12
forum: General Help
---

### Post by Orfintain on 2009-12-12
I know I can fix the problem by bringing up a terminal and executing "killall gnome-panel" The problem is I have to do this entirely too often and usually I have to kill some process to get it do it at all.

It's a fairly new computer and I recently air-dusted the processors

---

### Post by Orfintain on 2009-12-14
[http://linuxhaters.blogspot.com/](http://linuxhaters.blogspot.com/)

This **** is hilarious

---

### Post by pibach on 2010-01-26
I have the same problem and panel crashes frequently even after resetting conf. I am using Netbook Remix, might be a candidate. Any hints?

---

### Post by Hauke I. on 2010-01-29
Using 9.10 64 bit this happens frequently. Sometimes after killing the processes the panel does not restart.
It's not the NBR.

Panel settings:
- Vertical panel on the left
- Auto hiding (hiding animations off, show & delays at zero)
- One panel only, so all applets on this one (top to bottom):
  * Main menu
  * Window chooser
  * Window list
  * Show Desktop
  * Kill process
  * Desktop switcher
  * Keyboard layout indicator
  * Notification area
  * Clock

---

### Post by Hauke I. on 2010-01-29
I reset my panel configuration. As the standard setup doesn't suit me (I think it is a waste of space and to much distracting stuff on it) I adjusted it. I deleted the top panel, put the essential stuff onto the bottom panel and changed a few settings (/apps/panel/toplevels/bottom_panel_screen0: enable_animations 0, auto_hide_size 0, hide_delay 0, unhide_delay 0). As long as the panel is at the bottom (orientation bottom) it just works (up until now, maybe it will crash like before after some time...).
But: Setting the orientation to left via the panel settings crashes it now instantly. It is partly drawn to the left, the settings dialog that is still open is not drawn anymore (only the window border), other running applications are not affected. This happens reproducable.

---

### Post by Hauke I. on 2010-01-30
I forgot to mention that this happens with different computers. These have a similar setup. One "unusual" part of my setup is the system's language, swedish.

I tried to put the otherwise unchanged panel from the left to the bottom and could not determine any crashes yet on both computers. Before it was every few minutes, so the systems were de facto completly unusable.

---

### Post by A7med on 2010-03-21
I have the same problem here . gnome-panel leaks memory when i run many applications and it keeps leaking till system freezes and killing it won't work . I have to reboot very often and this sucks .

---

