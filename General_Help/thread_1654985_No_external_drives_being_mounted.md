---
title: "No external drives being mounted"
date: 2010-12-29
forum: General Help
---

### Post by lroedal on 2010-12-29
Hi! I recently wiped my second computer from Windows, replacing it with Linux Mint XFCE. I have already used Ubuntu for a while on my other computer, but I wanted something less demanding as this computer will also be used for gaming through Wine. 

After the fresh install everything worked perfectly, but now no external drives get mounted. Not usb-sticks, not the dvd-r and not any external drives. The external drive and usb-stick both are "active" with power, and show up under Gparted. They just are invisible to the filesystem, even though the system is set to automount every external source that is connected to the PC.

Any idea on what I could do? The lack of usb-sticks and such is quite annoying, as everything else works flawlessly now. :/ Thanks in advance!

---

### Post by Mark Phelps on 2010-12-29
Since these are the "Ubuntu" forums, you would do better going to the link below and asking your Linux Mint questions there:

[http://forums.linuxmint.com/]("http://forums.linuxmint.com/")

---

### Post by lroedal on 2010-12-29
Found the problem, I used some command-lines to tweak the system for SC2, and those were obviously meant for Gnome... So the reason for the "missing" drives was that they needed Nautilus. And since I don't have the slightest idea how to fix it back to Thunar, I just installed Nautilus... Problem "solved".. :p

---

