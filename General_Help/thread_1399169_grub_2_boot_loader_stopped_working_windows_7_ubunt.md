---
title: "grub 2 boot loader stopped working windows 7 ubuntu 9.10"
date: 2010-02-05
forum: General Help
---

### Post by ambiogas on 2010-02-05
I recently installed ubuntu 9.10 32 bit using live cd onto a recently new Dell machine with windows7.

Everything was fine for a couple of weeks, but last night I got the error:

Grub loading.
the symbol ` fil?
not found
Aborted

Looking into the forums, I see that maybe I need to re-install grub 2. When I started probing using fdisk, I saw that the boot partition was my windows partition. So, I thought I would ask to find out if this looks right before I start making things worse:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca6eeadf

Device Boot Start End Blocks Id System
/dev/sda1 1 5 40131 de Dell Utility
/dev/sda2 * 6 1918 15360000 7 HPFS/NTFS
/dev/sda3 1918 41471 317711636 7 HPFS/NTFS
/dev/sda4 41472 77825 292013505 5 Extended
/dev/sda5 41472 76605 282213823+ 83 Linux
/dev/sda6 76606 77825 9799618+ 82 Linux swap / Solaris
ubuntu@ubuntu:~$

ubuntu@ubuntu:~$ sudo df -Th
Filesystem Type Size Used Avail Use% Mounted on
aufs aufs 1.6G 49M 1.6G 3% /
udev tmpfs 1.6G 280K 1.6G 1% /dev
/dev/sr0 iso9660 690M 690M 0 100% /cdrom
/dev/loop0
squashfs 668M 668M 0 100% /rofs
none tmpfs 1.6G 100K 1.6G 1% /dev/shm
tmpfs tmpfs 1.6G 20K 1.6G 1% /tmp
none tmpfs 1.6G 88K 1.6G 1% /var/run
none tmpfs 1.6G 0 1.6G 0% /var/lock
none tmpfs 1.6G 0 1.6G 0% /lib/init/rw
ubuntu@ubuntu:~$

If the boot partition is wrong, I have no idea how this could have happened...?

Thanks in advance for any advice.
Andy

---

### Post by ambiogas on 2010-02-05
OK, I read the grub 2 update faq more closely and see from another person that my boot partition was indeed ok, so I did the standard grub 2 update, and it seems to have remedied this problem.

But, I have no idea how the boot loader got corrupted....?  Is there any way that I can avoid this in the future?


Thanks,

Andy

---

### Post by VMC on 2010-02-05
It depends what you did just prior to the corruption. We have no way to know.

When you install a new Linux, if you want to keep the grub on the current partition make sure you un-select add grub boot. Usually found at the advance tab. You can then issue 'sudo update-grub' to find the new OS.

---

### Post by ambiogas on 2010-02-05
My kids were on ToonTown before the corruption occurred (no laughing, please).  This is a windows and mac program, so they can't run it on linux.

I'll watch more closely if this happens again, and if I find the offending program, I'll post it.

Thanks for the help, I'm updating this thread to solved.

Andy

---

### Post by meierfra. on 2010-02-05
Check out this link. It list some of the programs which might be causing the problem. It also  contains solutions to the problem.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

---

