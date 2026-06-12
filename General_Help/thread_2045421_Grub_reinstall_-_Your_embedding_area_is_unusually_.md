---
title: "Grub reinstall - Your embedding area is unusually small. core.img won't fit in it.."
date: 2012-08-21
forum: General Help
---

### Post by lordmonkeyu on 2012-08-21
Hello everyone, 

I have a small problem with booting to Ubuntu after my resizing and moving the partitions recently. 
So I have 2 systems : 
[LIST]
[*]Windows 7 64 bit
[*]Ubuntu 12.04 64 bit
[/LIST]

This is my boot script paste [http://paste.ubuntu.com/1158836/]("http://paste.ubuntu.com/1158836/")
and my partition table here (when bootable flag is on sda3 then windows boots, when on sda6 then bios won't detect linux - midding operating system) 
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x68beefda

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              19    27262991    13631486+  27  Hidden NTFS WinRE
/dev/sda2        27262992    27467791      102400    7  HPFS/NTFS/exFAT
/dev/sda3        27467792   232267775   102399992    7  HPFS/NTFS/exFAT
/dev/sda4       232267793   976771071   372251639+   f  W95 Ext'd (LBA)
/dev/sda5       232267795   918867967   343300086+   7  HPFS/NTFS/exFAT
/dev/sda6   *   918870016   968044543    24587264   83  Linux
/dev/sda7       968046592   976771071     4362240   82  Linux swap / Solaris

```

After changing some stuff with partitions my system now boots only to Windows without showing grub menu. I have tried repairing this stuff with boot-repair but didn't help (either I got a blinking beacon - no boot, or information that there is no bootable device). 

So I have tried one last option to install grub onto a USB pendrive an boot my system from here and... boom it worked :)

So now I have possibility to boot to both Windows and Ubuntu but from ... USB.

Since already being logged to Ubuntu I have tried to reinstall grub. Logical thing, right ? But when I try to 
```
sudo grub-instal /dev/sda
```

I get this 
> ~$ sudo grub-install /dev/sda
/usr/sbin/grub-setup: warn: Your embedding area is unusually small.  core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: will not proceed with blocklists.


So here is my question to you: how can I fix it now ?

---

### Post by lordmonkeyu on 2012-08-21
Ok, guys I got this ;) 

The problem was that grub didn't have enough space to install itself in the beginning of the disk, namely I had first partition starting on 19th sector whereas grub needs at least 62 sectors in beginning of the disk to install itself (as far as msdos MBRs are concerned). 

So what I have done is I have moved the first partition 1MB right with GParted (didn't have option to move it a number of sectors - f anybody knows how to do this please message me) and then install grub on /dev/sda. 

Link to some related stuff 
[http://forums.fedoraforum.org/showthread.php?t=274701]("http://forums.fedoraforum.org/showthread.php?t=274701")

Voila :)

---

