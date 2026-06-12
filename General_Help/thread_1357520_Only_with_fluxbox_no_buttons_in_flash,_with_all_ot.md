---
title: "Only with fluxbox no buttons in flash, with all other window managers works"
date: 2009-12-17
forum: General Help
---

### Post by lasantarosa on 2009-12-17
Hello,

I have a weird problem:

When I start fluxbox as the window manager I can not push any buttons in flash animations. Like for example the play button on youtube. The rest of flash works normally.
I have the latest libflashplayer.so for 64-bit from Adobe Labs installed under .mozilla/plugins

If I click a button, it goes down, when I release the mouse it goes up again but nothing happens. Sometimes after pushing several times it works but it is not reproducable.

When I start for example kde or awesome window manager the buttons work perfectly!

I also tried to erase the .mozilla and .fluxbox dirs in my home and reinstall fluxbox completely but it does not help. The same happens also with other users, also root.

Does anybody have a clue?

Thanks!

---

### Post by lasantarosa on 2009-12-17
Discussed already here: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407)

For me without using nspluginwrapper this worked:

GDK_NATIVE_WINDOWS=TRUE firefox

---

