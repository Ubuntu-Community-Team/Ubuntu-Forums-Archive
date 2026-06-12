---
title: "Just installed Win7 now Grub won't show to all OS choice"
date: 2011-01-21
forum: General Help
---

### Post by Sanjuro82 on 2011-01-21
I been running Ubuntu 10.10.  I just recently partitioned my hard drive (using Gparted).  I shurnk the Ubuntu partition down to 400 gigs (Ext4).  And then partitioned the newly created unallocated (200 or so gigs) space as NFTS.  After getting the partitioning done, I exited Gparted and started the Win7 install.  

I installed Win7 on the newly created NTFS partition.  Everything installed correctly.  But when I reboot or start the CPU up, I don't get the screen that allows me to select which OS I want to boot.  Windows just boots right up.  Anyone know how to get that screen to show up so I can dual boot?

Thanks!

---

### Post by wilee-nilee on 2011-01-21
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

When you install windows it puts the MS bootlaoder in the MBR, the script will confirm what is where.

---

### Post by bryanl on 2011-01-21
This particular problem seems very popular right now ;-)

Always install Ubuntu last!

If you have Windows and Ubuntu both on the drive but installed Windows last so it is booting the drive, you'll need to reinstall GRUB2. That can be done from the live CD. see [Drive upgrade: Ubuntu and Windows 7 dual boot main drive](http://tcl.leipper.org/2011/01/drive-upgrade-ubuntu-and-windows-7-dual-boot-main-drive/) for an example.

---

