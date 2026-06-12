---
title: "Difference between installing ubuntu in 2 ways"
date: 2011-07-29
forum: General Help
---

### Post by community on 2011-07-29
I need to know about the basic difference between installing ubuntu alongside windows and installing directly on to a disk space.Is there any restrictions that I have to face if I install it alongside windows???

---

### Post by Lok222 on 2011-07-29
> **community said:**
> I need to know about the basic difference between installing ubuntu alongside windows and installing directly on to a disk space.Is there any restrictions that I have to face if I install it alongside windows???

i'll say in my experience, i loaded ubuntu on it's own drive to test, then loaded it as a dual boot with win 7 and the dual boot one is SOOOOOO Slow on the ubuntu side. not sure why but it's to where i dont even use it i just swap hard drives

---

### Post by Mark Phelps on 2011-07-29
> **community said:**
> I need to know about the basic difference between installing ubuntu alongside windows and installing directly on to a disk space.

The difference is the following:
1) Alongside -- if this is the Wubi install, Ubuntu is installed from inside MS Windows to a large file -- that it then treats as a partition.  The MS Windows OS selection menu is then modified to add an Ubuntu selection, and something known as GRUB4DOS is installed to support booting Ubuntu.  Since Ubuntu is running from inside an MS Windows filesystem (but NOT actually from inside MS Windows, it is a little slower, but not so much as to be noticeable.  Also, no new partitioning was done, the existing Windows MBR was NOT modified, and Ubuntu can be cleanly uninstalled later -- just like any other MS Windows app.
2) Separate partition -- Ubuntu is installed from the CD (or ISO image) to its own partition.  This requires creating space on the drive for the partition, and if the PC comes preloaded with 4 primary partitions, this can be a LOT of work. Allowing the Ubuntu installer to shrink Win7 OS partitions, instead of using the Win7 Disk Management utility, risks corrupting Win7 and rendering it unbootable.  And, it modifies the MBR to point to GRUB now, instead of Win7.  But, it's a little faster and is the preferred way to go. 
> Is there any restrictions that I have to face if I install it alongside windows???
Primary restriction of using Wubi is that it's generally a BAD idea to upgrade Ubuntu versions with it -- as some attempts at that have crashed Ubuntu.  If you're going to keep using Ubuntu long enough to need to upgrade it, then you should install to its own partitions.

---

### Post by tilii on 2011-07-29
Just to say that I have a Wubi install and have upgraded with no apparent issues from Intrepid to Natty bit I do understand that separate partitions are considered the better way to go.

Perhaps I've just been lucky. Other peoples experiences may differ.

---

### Post by Frogs Hair on 2011-07-29
I'm glad it is working for you . A Wubi installation is a virtual disk and works inside of the Windows partition . In many cases performance degrades over time . Wubi uses the windows boot loader , so if that fails for some reason , no Windows or Ubuntu .

 The Wubi developer/s wrote that it is for temporary  use as a means to try Ubuntu . I started with Wubi and find  that the dual boot is faster. I had nmon system monitor installed on the Wubi installation and the file system shows up as not a real file system .

You also can't hibernate with Wubi because of limited swap space and of course you have the 30 Gb maximum size limit for the partition .

---

