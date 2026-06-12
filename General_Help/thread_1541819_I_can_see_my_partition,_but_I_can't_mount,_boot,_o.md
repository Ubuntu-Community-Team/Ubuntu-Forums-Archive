---
title: "I can see my partition, but I can't mount, boot, or repair it."
date: 2010-07-29
forum: General Help
---

### Post by NPALeech on 2010-07-29
Ok, here's the situation. I just now re-installed 10.04 on my box, but now I can't get back into Windows. I'm getting the BOOTMGR not found error, that I'm familiar with, but the circumstances surrounding it are completely new to me. In the past I've encountered errors from hard-shutdowns where I couldn't mount the partition, until I checked it with windows first, but I can't boot into windows at all any more. 

I'm pretty sure my grub is pointing to the right location:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       20887   167774796    7  HPFS/NTFS
/dev/sda2           20888       31330    83883397+  83  Linux
/dev/sda3           31331       31591     2096482+  82  Linux swap / Solaris
/dev/sda4   *       31592      121601   723005325    7  HPFS/NTFS

```

My windows partition is sda1. An important thing to note here is that sd4 is set to the device boot. I've changed it multiple times to be sda1 to boot, but it always defaults back upon restart. 

```
title 		Windows 7 Ultimate
rootnoverify 	(hd0,1)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1
```

```
leech@NexTop:~$ cat /boot/grub/device.map
(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
```

So, unless I'm mistaken, that should be pointing to the right place. (hd0,0 takes me back to grub) When I looked into it further, I realised that I can't even mount the partition, or even modify it in gparted. When I launch the program I see this:

[img]http://img299.imageshack.us/img299/8449/screenshotqb.png[/img]

I have never seen the yellow ! next to a partition before. I tried to do a "Check" on it using Gparted, but it wouldn't let me touch it. I loaded up my Ubuntu live cd, and then tried it from there. That resulted in this error:
```
Check and repair file system (ntfs) on /dev/sda1  00:00:00    ( ERROR )
     	
calibrate /dev/sda1  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 335549654
size: 335549592 (160.00 GiB)
check file system on /dev/sda1 for errors and (if possible) fix them  00:00:00    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/sda1
     	
ntfsresize v2.0.0 (libntfs 10:0:0)
Failed to startup volume: Invalid argument.
ERROR(22): Opening '/dev/sda1' as NTFS failed: Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong partition? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? This error might also occur
if the disk was incorrectly repartitioned (see the ntfsresize FAQ).
```

I'm not sure what that means, exactly. I never touched that partition other than booting into it from windows, so I'm not sure why it's not reading as a "valid" NTFS filesystem. The filesystem hasn't changed, and there have been no modifications to it, it wasn't resized or anything of the sort. Normally, I'd just cut my losses and format, but I have some relatively important information on it, that I'd rather not lose. 

Any ideas on what could be going on here? I'm at a loss, and have no idea where to go from here.

---

### Post by prodigy_ on 2010-07-29
Since it's NTFS - did you try to boot from your Windows installation CD into recovery console and check the partition with chkdsk?

---

### Post by NPALeech on 2010-07-29
This specific box started out as a pre-built. I don't have an actual windows disc, I only have a "recovery" disc. The only two options that disc presents will result in data loss in some fashion. Restoring to defaults, which wipes settings, or a format which wipes everything. So in that aspect, my options are extremely limited.

Thanks for the prompt response.

Edit: 

Good thing I kept searching the forum, I found this:
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Going to run chkdisk from there and see if it helps.

---

### Post by NPALeech on 2010-07-29
chkdsk did not even detect the partition

---

### Post by Quackers on 2010-07-29
I'm afraid I don't have a link, but you can download a Windows boot disk and run that to get into the recovery environment, then use the command prompt to run sfc /scannow or even fix the boot manager. Or set the windows partition active with diskpart.

---

### Post by prodigy_ on 2010-07-29
> **NPALeech said:**
> chkdsk did not even detect the partition

Are you sure that this partition isn't encrypted somehow? If yes, you can try to recover it from Ubuntu using testdisk:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by NPALeech on 2010-07-29
No it wasn't encrypted. I couldn't mount it, but I did manage to make an image from testdisk. I then formatted that partition, and restored the image. 

From there, using the disc I linked to above, chkdsk managed to fix the problems on the partition. (I don't see how an exact image was different than the original state of the partition, but it apparently was.) Now things are working perfectly. Well, windows is booting anyway. I still have to re-install grub (which I believe is what caused this in the first place.) 

So *hopefully* this is solved. Thanks for the help guys. This isn't the first time that testdisk saved my bacon, I'm surprised I didn't think of it immediately.

---

