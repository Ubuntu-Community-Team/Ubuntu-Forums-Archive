---
title: "How Do I resize Partition ?"
date: 2010-05-07
forum: General Help
---

### Post by whitetimer on 2010-05-07
Hi All

I have a dual boot system, windows 7 & Xubuntu Lucid and i have gparted installed.  I need to resize my Windows 7 Partition by adding another 18gb by reducing my Xubuntu /home partiton by 18gb ...

How do i do this please ?

Many Thanks

):P

---

### Post by John Bean on 2010-05-07
You can't resize a mounted partition. The way around this is to boot from a LiveCD and use gparted from there.

---

### Post by whitetimer on 2010-05-07
> **John Bean said:**
> You can't resize a mounted partition. The way around this is to boot from a LiveCD and use gparted from there.

oh ok ... Thanks for that ...

---

### Post by John Bean on 2010-05-07
Incidentally, if you think you may need to do this again it may be worth downloading a small LiveCD like [Parted Magic]("http://partedmagic.com/") which not only loads very quickly but has a host of useful tools including (of course) gparted. It's much faster than using a Ubuntu LiveCD and even has its own bootable USB creator to allow you to put it on a thumb drive.

---

### Post by whitetimer on 2010-05-07
> **John Bean said:**
> Incidentally, if you think you may need to do this again it may be worth downloading a small LiveCD like [Parted Magic]("http://partedmagic.com/") which not only loads very quickly but has a host of useful tools including (of course) gparted. It's much faster than using a Ubuntu LiveCD and even has its own bootable USB creator to allow you to put it on a thumb drive.


I'm going to try that now .... CHEERS :KS

---

### Post by ajgreeny on 2010-05-07
DO NOT use gparted to enlarge your windows 7 partition!!

Shrink the linux partition that way, with gparted, but then boot into win7 and use the disk management utility there to enlarge that partition.

---

### Post by efflandt on 2010-05-07
You may want to shrink your Linux partition with gparted and then expand your Win7 partition from Windows itself.  Although, I do not currently have Win7, that would be safest.

I did play around with a Win7 laptop I bought for someone, and when temporarily installing Ubuntu 9.10 on it, I shrank the Win7 partition from its own administration tools, and then installed Linux on the freed up space.  I was sure that I put grub on the Linux partition (and marked that as the boot partition), but after I removed the Linux partition and marked the Win7 partition as the boot partition, Win7 could not find something like boot.ldr.  So I had to boot the Win7 CD (or DVD?) a couple of times to fix that.  Then I expanded the partition from Win7 itself to fill the unallocated disk space.

---

