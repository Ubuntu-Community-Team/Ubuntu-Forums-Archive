---
title: "Ghosting"
date: 2006-06-16
forum: General Help
---

### Post by maniacmusician on 2006-06-16
Is there any way I can ghost a copy of the Xubuntu OS that I'm running? I was planning on using this old computer to take it for a test run,  and I got caught up, installed a lot of things, etc, and dont want to have to do that all over again. I'm planning on eventually buying another computer and installing Xubuntu on it, but for now, I want to set it up on an xp machine and configure a dual boot. But yeah,,,how would I go about ghosting it as I have it now? 

I've never even done it to a PC, but its pretty convenient when you don't want your settings erased...

any help would be appreciated

---

### Post by aysiu on 2006-06-16
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by maniacmusician on 2006-06-16
ah...i shouldve realized this, but just to make sure, if they don't have the same hardware, it won't work right? or will xubuntu detect the new hardware (its a completely different chipset, hard drive, everything)? 

unless someone knows for sure, its pretty risky and could probably screw up a lot...

---

### Post by aysiu on 2006-06-16
I think you might run into some road bumps if they're different hardware, but it may be as simple as running ```
sudo dpkg-reconfigure xserver-xorg
``` to get it working again.

---

### Post by maniacmusician on 2006-06-16
right...but when i put it on the xp machine, and if it screws up, is there a chance it will ruin all partitions on the hard drive (because it will probably have to resize the windows partition to make space for itself right?)

---

### Post by aysiu on 2006-06-16
No, the space you make for the partition image happens *before* you restore the image.

So, yes, you might ruin the Windows partition by shrinking it (highly unlikely, especially if you've defragmented it first), but that's in the resizing process, not the image restoration process.

---

