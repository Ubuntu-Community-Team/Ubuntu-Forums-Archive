---
title: "Full install"
date: 2010-09-06
forum: General Help
---

### Post by rodericke on 2010-09-06
I installed Wubi the other night and messed around with it for a while and absolutely love it. I uninstalled it, burned a live CD and USB, tried to install but got no 'side by side' option. And, to top it all off it I am scared of the manual partitioning. The truth is, I loved it so much that what I really want to do is a complete, Ubuntu 10.04 LTS only install. But, I am completely unnerved by this idea. I have lost my backup Vista disks so I wouldn't be able to reinstall Windows if necessary and this is my primary work computer.

---

### Post by bcbc on 2010-09-06
If you have vista you must use the vista disk utility to shrink your windows volume. I've heard running chkdsk is a good idea as apparently the ubuntu installer won't recognise the partition properly as ntfs if it's not clean.

Also, consider some disk imaging software as a backup - if this is your primary work computer, you have to consider what you'll do if you mess it up. At the least, you should be able to backup your entire install to DVDs before messing with a dual boot. And have a windows repair cd handy as well. Not saying you'll need it, but it pays to be cautious.

---

### Post by rodericke on 2010-09-06
I've tried chkdsk and it says that the disk is clean. As far as the installation goes, disk space is partitioned as follows: 1.6GB w/854mb used. The other is 248.6GB w/unknown usage.

---

### Post by bcbc on 2010-09-06
have you tried shrinking the 248gb partition in vista?

---

### Post by rodericke on 2010-09-06
According to my PC, the available space is 168GB. That is after shrinking. The whole manual partition thing scares the hell out of me.

---

### Post by rodericke on 2010-09-06
I'm not sure how to set up the partitions. Am I too much of a noob for Ubuntu or what?

---

### Post by ironic.demise on 2010-09-06
> **rodericke said:**
> I'm not sure how to set up the partitions. Am I too much of a noob for Ubuntu or what?

Partitioning isn't that scary, I know what you mean though.
My advice would be to backup all your data first, as bcbc said use imaging software.

do a quick google at (I think it's NERO) GHOST.

It will copy your entire hard-drive and if everything fails then it will put it back EXACTLY how it was (byte for byte, the whole disk, 0s and 1s)

There may be alternatives but GHOST seems like a professional option.

Then try and use Vistas utilities, GParted or anything else that claims to handle partitions and as said, if all else fails use an Imaging software to go back in time... it's practically the same as if you DID have your Vista discs.

---

### Post by bcbc on 2010-09-06
That's odd. So you've created a new 168Gb partition in windows, and the Ubuntu installer doesn't see it?

Instead of installing, select "Try without installing". Once booted run "sudo fdisk -l" (that's a small L) from a Terminal prompt (Applications, Accessories, Terminal) and post the output.

You can also run gparted (System, Administration, GParted) and upload a screenprint (Applications, Accessories, Take Screenshot)

---

### Post by rodericke on 2010-09-06
Thank you guys so much for your help. I think I am going to get some imaging software and go that route.

---

### Post by ironic.demise on 2010-09-09
> **rodericke said:**
> Thank you guys so much for your help. I think I am going to get some imaging software and go that route.

good luck than, tell us how it goes, imaging software is *relatively* failsafe ;)

---

### Post by mastablasta on 2010-09-09
make sure to defrag the drivefirst to avoid any data loss. using the enclosed (in Vista) partitioning software hsoul dbe good enough to make one partition. after that Ubuntu should give you the option on autopartitioning on that empty space.

---

