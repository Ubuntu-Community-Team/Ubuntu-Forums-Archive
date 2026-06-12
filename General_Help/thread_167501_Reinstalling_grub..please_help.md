---
title: "Reinstalling grub..please help"
date: 2006-04-28
forum: General Help
---

### Post by cabber on 2006-04-28
I had Fedora installed (first) on sda1 and Dapper installed (second) on sdb1.  I removed the fedora drive from the system and obviously lost my GRUB so I cannot boot into Ubuntu.  I've read a few post on reinstalling the grub and was curious if someone could walk me through a very user friendly process to do this.  This machine only has two drives on it.  Ubuntu Linux and a Back up drive.  

Some of my confusion is this.  Since I pulled the Fedora drive out, which was the "sda" drive, does the Ubuntu drive (that was sdb) become the sda drive?  And the back up, which was "sdc" become "sdb"?  I'm not sure how to reinstall the grub and where to install it.  When I installed Ubuntu, I just let the installer format the drive and do a "default" install.  

Please advise on what to do.  Thank You very much.
Cabber

---

### Post by KnottyMan on 2006-04-28
Yes, the drive letters will renumber.  Sata drive are like SCSI in this respect.

There are numerous threads on how to reinstall grub.  Try a search.  I usually just boot off the CD, mount the volume, chroot to it, then grub--install /dev/sda
exit chroot, umount, reboot.  While chroot'd though, look at fstab and change the sdb to sda. Then you should be set.

---

### Post by cabber on 2006-04-28
[QUOTE=KnottyMan]Yes, the drive letters will renumber.  Sata drive are like SCSI in this respect.

There are numerous threads on how to reinstall grub.  Try a search.  I usually just boot off the CD, mount the volume, chroot to it, then grub--install /dev/sda
exit chroot, umount, reboot.  While chroot'd though, look at fstab and change the sdb to sda. Then you should be set.[/QUOTE]


I guess I am a little shacky on mounting the volume.  When I get to the partitioning part, it lists the drives I have installed, what keys do I press to mount them vs formating them and reinstalling.   This is with the DVD install disk

Can this be done via the "rescue" mode?  As I mentioned I have done a search and read through several post, but I am still a bit confused with the process.

---

### Post by cabber on 2006-04-28
When I sue my install disk to reinstall the grub and get to the disk partitioning area.  It list both drives.  

/dev/sda:
#1 primary 35.5 GB B K ext3   /media/sda1
#5 logical    1.5 GB    F swap  swap

/dev/sdb
#1 primary 137.9 GB K  ext3    /media/sdb1

So were do I go from here?  Thanks.

cabber

---

