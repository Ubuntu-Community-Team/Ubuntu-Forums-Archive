---
title: "Nautilus hangs with USB stick"
date: 2009-07-18
forum: General Help
---

### Post by Blue_Mercury on 2009-07-18
Today I tried pluging my USB flash drive (16GB Duracell) into my desktop running Ubuntu 8.10

When I do the file browser pops up like normal and displays the content, but then hangs and does not recover.

At the same time, Nautilus hangs and all the icons on the desktop disappear and the system monitor says Nautilus is running at around 60% CPU (of 2.6gHz) until I force close the file browser window.

After it is forced closed the icons on the desktop reappear.  If open the drive again it does the same thing. The drive can be unmounted successfully.

I don't understand what has changed, it was working yesterday just fine and I tested the USB stick on my laptop running Ubuntu 9.04 and it worked fine.

---

### Post by fragos on 2009-07-18
Perhaps your USB flash drive has a lot of files. Nautilus may have been preparing to display when you forced a termination. Even a folder on hard disk can take a little while before Nautilus will display the files. /usr/bin is an example of a folder with so many files there is a delay before displaying. Remember your USB flash drive access is much slower than a hard disk.

---

### Post by Blue_Mercury on 2009-07-18
It is a large USB stick, however when it was working 2 days ago it had the same information on it as it does now, so what has changed?

I allowed it to sit for 10 minutes to see if it could resolve the problem or was attempting to load, but it didn't do anything,

The file browser remained non responsive for the whole time (but only the window attempting to view the stick) and the desktop remained blank until I forced the window to quit.  Nautilus remained using a large portion of the processor for the entire time.

I tested a much smaller USB stick (156mb) with only 2 files on it, and it worked.

Now I really don't understand what is going on, because this USB stick worked 2 days ago with the exact same information on it as now, but doesn't work now, and only in this computer.  It works on other computers fine, and other USB sticks work on this one fine.

---

### Post by fragos on 2009-07-19
I checked [https://bugs.launchpad.net/](https://bugs.launchpad.net/) and didn't find any relating bugs reported. In your home folder there is a hidden folder ".nautilus" which seems to contain information about files and media that have been accessed. Just guessing but perhaps there's something in there that causes your problem. You could try deleting that folder and contents. A new one should be created by nautilus.

---

