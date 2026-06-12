---
title: "Mouse Randomly Locks Up!!!"
date: 2010-09-19
forum: General Help
---

### Post by jeremy96 on 2010-09-19
Once in a while, my mouse pointer will just lock up and then when I try to kill the X server by pressing Ctrl + Alt + Backspace on my keyboard, it quits the desktop and it shows my wallpaper. It does not go back to the login screen. How do I fix this problem?

Thanks, 

Jeremy Passarelli :(:confused:

---

### Post by scorchgeek on 2010-09-19
Pressing Ctrl-Alt-Delete does not kill the X server by default. On many systems, Ctrl-Alt-Backspace will. You can also use Ctrl-Alt-F1 to get to a virtual terminal, then run ```
sudo killall gdm
```

Of course, you really want to fix the mouse locking up in the first place, which is something Linux has never done to me. Maybe your video driver? Or the system is just very busy?

---

### Post by Alexis Phoenix on 2010-09-19
I wonder what kind of mouse you are using?  Several things occur to me:
It is a battery powered wireless mouse and needs new batteries
As scorchgeek says, the system is very busy
It is a fancy mouse and the driver support is incomplete
Xorg is locking up for some reason - you can detect this by seeing if your caps lock light still comes on when you press the caps lock key
You have gpm running and it is causing interference - though I thought all those issues had been fixed.

You could try using gpm as a repeater though I don't know if this has any relevance these days, it did used to be a way to work around these kind of issues.  (With gpm installed) you change the relevant line in xorg.conf to use /dev/gpmdata as the mouse device.

---

### Post by jeremy96 on 2010-09-19
It's only happened with Ubuntu! Other distros I've used have not had this problem!

---

### Post by choochoousmc on 2010-09-19
I have an Acer  5532. Took Win 7 off it and put ubuntu 10.04
Every now and then my mouse won't respond.
I double tap my pad (built in mouse pad) and my usb mouse starts working again.
I installed the synaptics  deactivator, but it doesn't seem to work.
You might try double tapping the synaptic pad.

---

### Post by youbuntu on 2010-09-20
I have THREE, *WIRED* USB mice, and they ALL lock the system up eratically. This is with Lucid 10.04.1 on a MacBook. Please DO NOT tell me it is my mouse, because when I remove it, all is well again. Lucid has a bug, and a rather serious one, which I suggest is fixed, pronto!.

Thx

---

