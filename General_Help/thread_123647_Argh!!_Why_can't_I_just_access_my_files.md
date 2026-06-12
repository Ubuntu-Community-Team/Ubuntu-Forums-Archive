---
title: "Argh!! Why can't I just access my files?"
date: 2006-01-30
forum: General Help
---

### Post by maxsideburn on 2006-01-30
I've always been a big linux supporter.....except that everything "belongs" to a certain user. I like having full access to my #&*@ing computer.

Now I've had this problem before with Ubuntu, but always managed to fix it. My NTFS partitions are automatically mounted on my users' desktops, but they "don't have permission" to access them. (Man I wish I could just give them PERMISSION TO DO ANYTHING).

Well here's my FSTAB

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1 /media/hda1 ntfs ro,noauto,umask=222 0 0
/dev/hdb1 /media/hdb1 ntfs ro,noauto,umask=222 0 0
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0


I don't see what's wrong. I've tried like 10 different FSTAB suggestions on these forums. I don't see what else to do.

---

### Post by mcduck on 2006-01-30
change the lines for hda1 and hdb1 to these:

/dev/hda1       /media/hda1 ntfs    nls=utf8,umask=0222 0  0
/dev/hdb1       /media/hdb1  ntfs    nls=utf8,umask=0222 0  0

If that doesn't work, run 'sudo fdisk -l' and post the output here.

---

### Post by The Mekon on 2006-01-30
My FSTB is as follows:

/dev/hda1       /media/windows_boot  ntfs    nls=utf8,umask=0222 0       0
/dev/hda2       /media/windows_share  vfat    iocharset=utf8,umask=000   0       0
/dev/hda3       /media/windows_data  ntfs    nls=utf8,umask=0222 0       0


Perhaps you could try it out as it works for me. It has been several months since I set it up and can not remember how I got there:)

---

### Post by aysiu on 2006-01-30
[QUOTE=mcduck]change the lines for hda1 and hdb1 to these:

/dev/hda1       /media/hda1 ntfs    nls=utf8,umask=0222 0  0
/dev/hdb1       /media/hdb1  ntfs    nls=utf8,umask=0222 0  0[/QUOTE] I second the motion.

---

### Post by maxsideburn on 2006-01-30
/dev/hda1               1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        3170     4980150   83  Linux
/dev/hda3            3171        3413     1951897+   5  Extended
/dev/hda5            3171        3413     1951866   82  Linux swap / Solaris

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       19457   156288321    7  HPFS/NTFS


That's what I get. I tried the first suggestion, still nothing. My regular users don't have permission to access any of the NTFS partitions.

also when I tried running sudo fdisk -l under another user it asked for my password, but then said it wasn't the right one. So I had to go back into my root account to do it.

---

### Post by mcduck on 2006-01-31
after you did those changes, did you reboot (or 'sudo mount -a') to remount all drives?

If you did, then I have no idea what's wrong with your system. Partitions are correct, and that umask should give everybody read acces to those partitions.

edit: sudo won't work for other users than the first created, as the rest aren't in the sudoer's group.

---

### Post by aysiu on 2006-01-31
I would encourage a reboot.

```
sudo mount -a
``` tends to work only if the partitions were unmounted before the fstab changes were made. A reboot makes it nice and clean.

---

### Post by mcduck on 2006-01-31
[QUOTE=aysiu]I would encourage a reboot.

```
sudo mount -a
``` tends to work only if the partitions were unmounted before the fstab changes were made. A reboot makes it nice and clean.[/QUOTE]
Hey, thanks. I didn't know that, I've understood that it would remount everything in fstab.

You live and learn :D

---

### Post by aysiu on 2006-01-31
[QUOTE=mcduck]Hey, thanks. I didn't know that, I've understood that it would remount everything in fstab.

You live and learn :D[/QUOTE] That's what I understood, too, but I haven't found that to always be the case. I'm not saying this with 100% certainty (it's all anecdotal based on my limited experience), but I'm pretty sure a reboot will cleanly remount.

---

