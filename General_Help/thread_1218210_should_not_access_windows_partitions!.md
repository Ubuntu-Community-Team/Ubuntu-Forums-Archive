---
title: "should not access windows partitions!"
date: 2009-07-20
forum: General Help
---

### Post by chinmaya_n on 2009-07-20
Hi 

I would like to have a linux system such that it should not access the windows partitions but it should do its linux partitions.( for some security reason, i need this) From linux we should not see the windows partitions. Can we do this??

Thanx

---

### Post by mixmaster on 2009-07-20
Remove all references to windows file systems from /etc/fstab and reboot.

You will still be able to mount them again manually but they won't automount.

---

### Post by chinmaya_n on 2009-07-20
I could not find any lines representing windows partitions in /etc/fstab !

---

### Post by balaknair on 2009-07-20
could you post the contents of fstab here?

---

### Post by chinmaya_n on 2009-07-20
```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=0929fd93-aed3-4cef-962d-fe0463e035c7 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=a98b32b7-380d-42ba-92d4-83ecefc108d3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

These r the contents of fstab

---

### Post by balaknair on 2009-07-20
> **chinmaya_n said:**
> ```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
[COLOR="Red"]# / was on /dev/sda3 during installation[/COLOR]
UUID=0929fd93-aed3-4cef-962d-fe0463e035c7 /               ext3    relatime,errors=remount-ro 0       1
[COLOR="Red"]# swap was on /dev/sda9 during installation[/COLOR]
UUID=a98b32b7-380d-42ba-92d4-83ecefc108d3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

These r the contents of fstab

I've never seen an fstab look quite like this. :confused:

I think this is beyond my understanding and I doubt if I'm able to help you, but there are a few points I'm curious about. Could you please answer these just to satisfy my curiousity?

1) Is this from an actual working install of Ubuntu that you're logged in to or is it from a Live CD session?

2) 
```
[COLOR="Red"]# / was on /dev/sda3 during installation[/COLOR]
UUID=0929fd93-aed3-4cef-962d-fe0463e035c7 /               ext3    relatime,errors=remount-ro 0       1
[COLOR="Red"]# swap was on /dev/sda9 during installation[/COLOR]
UUID=a98b32b7-380d-42ba-92d4-83ecefc108d3 none            swap    sw              0       0
```

So where exactly are / and swap located now?

3) There are no entries pointing to Windows partitions, so can you see the partitions(mounted or unmounted) in nautilus?

---

### Post by chinmaya_n on 2009-07-20
yes .........
1. THis is a complete installed system( dual boot )
2. They r located as seperate partitions on the hard disk.
3. i can access the windows partitions and can see whether they can be mounted r not.

But one thing i forgot to mention, Presently my windows is corrupted!! But there are other NTFS partitions with my data

---

### Post by balaknair on 2009-07-20
Hmmm.

What does "sudo fdisk -l" show?

---

### Post by michy99 on 2009-07-20
This is a perfectly ordinary fstab file. The windows partitons are not automounted, but are available though the file manager and the Places menu. They are mounted the first time you click on them. What you want is some way to make them invisible to Ubuntu. I am sure there is a way to do it, but someone with more knowledge than I will have to tell you how to do it.

---

### Post by chinmaya_n on 2009-07-20
This is the output of $sudo fdisk -l
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0aaf0aaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3315    26627706    7  HPFS/NTFS
/dev/sda2            3316       34050   246878887+   f  W95 Ext'd (LBA)
/dev/sda3           34051       38913    39062047+  83  Linux
/dev/sda5            3316        9689    51199123+   7  HPFS/NTFS
/dev/sda6            9690       22437   102398278+   7  HPFS/NTFS
/dev/sda7           22438       28811    51199123+   7  HPFS/NTFS
/dev/sda8           28812       33214    35367066    7  HPFS/NTFS
/dev/sda9           33215       34050     6715138+  82  Linux swap / Solaris

```
Thanx michy99. Can some one help me plz?

---

### Post by balaknair on 2009-07-20
@michy99
Is this normal?
"# / was on /dev/sda3 during installation"

I've never seen an fstab entry like that. Could it be due to an absolutely new install(booting from the HDD for the first time after install)?

---

### Post by michy99 on 2009-07-20
> **balaknair said:**
> @michy99
Is this normal?
"# / was on /dev/sda3 during installation"

I've never seen an fstab entry like that. Could it be due to an absolutely new install(booting from the HDD for the first time after install)?

You must have upgraded to Jaunty instead of doing a fresh install. The install now uses the UUID of the partitions in fstab, so the comment line above each entry lets you know which partition it is.

---

### Post by michy99 on 2009-07-20
As to the original question about hiding partitions, I found a possible solution in this thread:

[http://ubuntuforums.org/showthread.php?t=668748](http://ubuntuforums.org/showthread.php?t=668748)

---

### Post by balaknair on 2009-07-20
> **michy99 said:**
> You must have upgraded to Jaunty instead of doing a fresh install. The install now uses the UUID of the partitions in fstab, so the comment line above each entry lets you know which partition it is.

Ah.
OK, that makes sense. I haven't done an upgrade since Gutsy, always prefer to do a fresh install, so I've never come across an fstab like that. Thanks for clearing that up for me.:)

---

### Post by chinmaya_n on 2009-07-21
I could not get it from 
[http://ubuntuforums.org/showthread.php?t=668748](http://ubuntuforums.org/showthread.php?t=668748) !!

I didnt find "S10xserver-xorg-input-wacom" this file in my system.

But i inserted the line in another file, I observed that '/dev/sda2' file is removed. But i could access to that partition !!

For more info
```
$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0aaf0aaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3315    26627706    7  HPFS/NTFS
/dev/sda2            3316       34050   246878887+   f  W95 Ext'd (LBA)
/dev/sda3           34051       38913    39062047+  83  Linux
/dev/sda5            3316        9689    51199123+   7  HPFS/NTFS
/dev/sda6            9690       22437   102398278+   7  HPFS/NTFS
/dev/sda7           22438       28811    51199123+   7  HPFS/NTFS
/dev/sda8           28812       33214    35367066    7  HPFS/NTFS
/dev/sda9           33215       34050     6715138+  82  Linux swap / Solaris

```

plz does anyone know ab't it !!

---

### Post by ryanhaigh on 2009-07-21
Hi chinmaya_n, Im zero-9376 the author of the original post that was referenced in previous replies.

Since posting that information I have learnt that you should use the /etc/rc.local file if you want to perform admin operations during the boot process. Unfortunately this doesn't work because the rc.local script is called too late in the boot process. What I found when trying that was nautilus still had a reference to the 10GB FAT volume I created but I was unable to mount it because the file itself (/dev/sdb1) had been deleted. As such I don't understand how you could have mounted the partiton after that file had been deleted.

The script I used contained the following:
```

#! /bin/sh
#dont forget to sudo chmod +x /etc/rc2.d/S**rmsdb1 to make this script executable
rm /dev/sdb1
exit 0

```

I have just tried using this script in a virtualbox install of ubuntu 9.04/Jaunty. Because ubuntu has optimised the boot process my suspicion was that gvfs/hal etc was becoming aware of the partition before it was deleted. However when I used an rc script beginning with S10 (/etc/rc2.d/S10rmsdb1) the file was still removed and nautilus could not see it althout it could see an unmountable mass storage device that I would guess corresponds to /dev/sdb.

I then tried to moved the script to /etc/rc2.d/S99rmsdb1 and rebooted the machine and as was the case when using /etc/rc.local the partition was visible in nautilus as 10GB volume but was not mountable because the /dev/sdb1 file did not exist.

Can you tell me which file you used on your machine?

---

### Post by chinmaya_n on 2009-07-22
I tried that using the file "/etc/rc2.d/S01policykit","/etc/rc2.d/S99rc.local" and also tried by creating a new file with name "S101.sh" containing just that line only.

In both cases i could note that the sda2 file not present in /etc (removed by that line) , but i could mount that partition !! 
I removed that line, then i could see sda2 file after reboot.!

---

### Post by ryanhaigh on 2009-07-23
Could you post the output of the command following commands both with and without the script in place:

```

ls /dev | grep sd
mount
#then mount using nautilus
mount

```

---

### Post by chinmaya_n on 2009-07-23
I'm very much sorry 'ryanhaigh'.........  Its all my foolishness and dumpness !!!

Actually what u told, had worked !!:popcorn:
I removed /dev/sda2. But mounted /dev/sda1:( 
Its all working perfectly now. When tried to mount the sda1, it is showing an error !!:P

But I've a doubt... what is '/dev/sda2' on my computer ( I thought it was the windows partition !! but sda1 is the actual windows partition )
```
$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0aaf0aaf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3315    26627706    7  HPFS/NTFS
/dev/sda2            3316       34050   246878887+   f  W95 Ext'd (LBA)
/dev/sda3           34051       38913    39062047+  83  Linux
/dev/sda5            3316        9689    51199123+   7  HPFS/NTFS
/dev/sda6            9690       22437   102398278+   7  HPFS/NTFS
/dev/sda7           22438       28811    51199123+   7  HPFS/NTFS
/dev/sda8           28812       33214    35367066    7  HPFS/NTFS
/dev/sda9           33215       34050     6715138+  82  Linux swap / Solaris

```

---

### Post by ryanhaigh on 2009-07-23
That would be your extended partition. A disk with a DOS partition table can only have 4 primary partitions, using a extended partition allows you to increase the number of partitions. The extended partition 'holds' the rest of the partitions which are called secondary partitions. You will notice that iff you add all the blocks of the partitions below the extended one they are approximately equal to the number of blocks in the extended partition.

For more info: [http://en.wikipedia.org/wiki/Disk_partitioning#Extended](http://en.wikipedia.org/wiki/Disk_partitioning#Extended)

---

### Post by Old_Grey_Wolf on 2009-07-23
> **chinmaya_n said:**
> Hi 

I would like to have a linux system such that it should not access the windows partitions but it should do its linux partitions.( for some security reason, i need this) From linux we should not see the windows partitions. Can we do this??

Thanx

Just curious, are you trying to protect the Windows partition from someone that has physical access to the computer?

---

### Post by Whiffle on 2009-07-23
Why not add the windows partition to the fstab, but tell it not to auto mount.  I'm pretty sure the gnome file manager ignores anything in fstab, and you'd need sudo to mount it if you did want to.  Something like:

```

/dev/sda1 /windows ntfs noauto 0 0 

```

---

### Post by solitaire on 2009-07-23
Just a thought but...

Would it be easy to compile a kernel without NTFS support? Or at least remove the ntfs modules loaded during boot. Then at least the kernel will not recognize the NTFS partitoins so can't read or write to them.

---

### Post by ryanhaigh on 2009-07-23
These are good suggestions, I think the reason I went with the rm /dev/sd* approach originally was because the OP in the older threads didn't want the drives visible at all.

I'm not sure if using the fstab/noauto option would mean that the drive isn't visible at all in computer:/// but would be interested in finding out (bit busy to fire up the VM and check myself). 

Regarding the ntfs module removal the only issue I can see here is when you want to plug in an external drive however this could be overcome by simply blacklisting the ntfs-3g module and when required sudo modprobe ntfs-3g (or whatever the module is actually called) although I'm not sure if the module can be easily removed once its been loaded (ipv6 can't just be rmmoded once loaded for example).

EDIT: just to clarify I was talking about the possibility of blacklisting the ntfs-3g module not deleting the actual files for the module.

---

