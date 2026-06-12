---
title: "WTF? My hard disk wiped in the *blink* of an eye!"
date: 2011-12-11
forum: General Help
---

### Post by c.cobb on 2011-12-11
Long story, short question: How do I remove the "Format..." option from the right-click context menu for Gnome? (Ubuntu 10.04)

I just tried using nautilus-actions but this seems to only be for adding  menus / items, not for removing existing functionality. I thought maybe  add a new "Format.." to override the existing, but it doesn't seem to  apply to mounted device icons.
 Thanks,

Ever have one of these nights? It was late, and I was just wrapping up messing with some new software. I have a little laptop with WinXP on the hard disk, but I usually boot it with Ubuntu running on a Live USB. I had used the hard disk to unpack the software, compile, etc...

I went to unmount the hard disk. Whenever I right-click on any disk icon for the first time in the Ubuntu desktop, there is about a 4-second delay before the context menu pops up -- dunno if this happens for you. If I move the mouse pointer during this delay, the menu will eventually pop up where ever the pointer is later on. 

When the menu popped up, it *immediately* disappeared, I saw a progress bar saying "Formatting..." and, in less than a second, got an error message on the progress bar that the format failed. I tried re-mounting and got a completely empty disk labeled "New Volume". I can only imagine that the menu happened to pop up in such a way that the "Format" option was under the mouse pointer, and *two* clicks were queued up somehow. Too bizarre. 

I sat there with my mouth open for about 20 minutes Googling my data recovery options. Tried running TestDisk. Even the "deep query" ("deep discovery?") option didn't work -- it hung about 35% of the way through. Turns out a bad sector, but that's another story. Apparently, after reformat, the only way to recover is sending the disk to a Forensics / Data Recovery lab.

---

### Post by winh8r on 2011-12-11
sorry, posted then re-read that you had tried nautilus actions-- oops!

---

### Post by c.cobb on 2011-12-11
Well, shoot, didn't find any easy way to do this. Nothing in UbuntuTweak, gconf-editor, or even [editing nautilus UI menus]("http://ubuntuforums.org/showthread.php?t=1786591#4") directly seems to work. Also none of the Gnome Lockdown settings work for this. You can disable printing, but not formatting a disk device. Too strange. 

I did find where the menu is created: the 'nautilus_gdu_get_file_items()' function in file 'src/nautilus-extension/nautilus-gdu.c' which, for Lucid, is in package [gnome-disk-utility (2.30.1-1)]("http://packages.ubuntu.com/source/lucid/gnome-disk-utility").

Guess the only way to ensure this doesn't happen, short of rebuilding nautilus, is to disable displaying the mounted disk icons on the desktop. :-( And there's probably not much use filing a change request against Gnome 2.30 anymore. 
FWIW,

---

### Post by oldtimer7777 on 2011-12-11
I would try a different desktop environment instead of asking to change one. 

> **c.cobb said:**
> Well, shoot, didn't find any easy way to do this. Nothing in UbuntuTweak, gconf-editor, or even [editing nautilus UI menus]("http://ubuntuforums.org/showthread.php?t=1786591#4") directly seems to work. Also none of the Gnome Lockdown settings work for this. You can disable printing, but not formatting a disk device. Too strange. 

I did find where the menu is created: the 'nautilus_gdu_get_file_items()' function in file 'src/nautilus-extension/nautilus-gdu.c' which, for Lucid, is in package [gnome-disk-utility (2.30.1-1)]("http://packages.ubuntu.com/source/lucid/gnome-disk-utility").

Guess the only way to ensure this doesn't happen, short of rebuilding nautilus, is to disable displaying the mounted disk icons on the desktop. :-( And there's probably not much use filing a change request against Gnome 2.30 anymore. 
FWIW,

---

