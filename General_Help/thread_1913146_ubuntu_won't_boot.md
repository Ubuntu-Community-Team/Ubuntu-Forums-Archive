---
title: "ubuntu won't boot"
date: 2012-01-22
forum: General Help
---

### Post by joshj70 on 2012-01-22
So I was messing around with my Ubuntu and I managed to completely screw it up.
I have two hard drive installed, a 250gb for Ubuntu and an 80gb for Windows XP.

I resized my 250gb hard drive to fit all for Ubuntu, sense before it was partitioned two ways, one for Ubuntu and one for windows, until I installed my other HD for windows, anyway I resized the 250 to fit all for Ubuntu, then it wouldn't boot, so I went to lookup how to reinstall grub and used the boot-rescue program that the grub2 Ubuntu page recommended, and that is where it all went horribly wrong. I forgot to click the option that installs grub just to sda1, which is my Ubuntu, and it moved it to both hard drives. luckily I made a backup before any of this, finally I gave up and reinstalled Ubuntu and copied my backup onto the new installation, now when I boot the grub menu pops up, and when I select any Ubuntu option it goes to a screen that says
```
error: fd0 cannot get C/H/S values
error: unknown filesystem
error: you need to load the kernel first
press any key to coninue...
```when I press a key it goes back to grub menu, and just to make things worse my windows is messed up to.

Any suggestions?

---

### Post by carl4926 on 2012-01-22
Can you boot a Ubuntu live cd
Open a terminal and post the result of

```
sudo fdisk -l
```

---

### Post by joshj70 on 2012-01-22
Yes,

```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007f477

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241162240   83  Linux
/dev/sda2           30024       30395     2975745    5  Extended
/dev/sda5           30024       30395     2975744   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00050639

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           1        9546    76678213+   7  HPFS/NTFS
/dev/sdb3            9547        9730     1467393    5  Extended
/dev/sdb5            9547        9730     1467392   82  Linux swap / Solaris

Disk /dev/sdc: 2032 MB, 2032664576 bytes
16 heads, 24 sectors/track, 10338 cylinders
Units = cylinders of 384 * 512 = 196608 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e9bc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           6       10336     1983488    b  W95 FAT32
```

---

### Post by carl4926 on 2012-01-22
There is much here that concerns me.

Not that this matters, but you unnecessarily have 2 swap partitions.

The 250GB is sda
Was it sda when you installed Ubuntu
You talk about re-sizing? So we don't really know what was, all we know is what you have now. Did you change the partition table with re-sizing?

Typically I would expect the 80GB to be sda with windows ntfs only
Then sdb to be Ubuntu
And with 250GB I would have:
swap as much as your RAM
/ ext4 25GB
/home ext4 (all the remaining space)

Might be time to backup and clean up:
delete swap on the 80GB, resize the the space, fix the MBR, set as sda, first boot device in BIOS

Format the 250GB as quoted above with the three partitions
Grub will write to sda MBR which is fine

---

### Post by joshj70 on 2012-01-22
Yeah, that boot rescue thing is what did all that, before it was Windows on the 80 and Ubuntu on the 250, sda has always been the 250. I had approximately 100 gb of unallocated before I resize. yes I did change the partition table, there was the 100gb of unallocated space that wasn't assigned to anything at all, so i made the whole sda partition the full 250 and then resized the Linux part specifically for all 250.

Just curious, why should I have the Windows as sda and MBR?

---

### Post by carl4926 on 2012-01-22
> Just curious, why should I have the Windows as sda and MBR?You don't have to

It's less of an issue now with grub 2

Increasing the size of partitions doesn't necessarily change the partition table
And now, looking, it seems unlikely that you did change it.

---

### Post by carl4926 on 2012-01-22
I found another thread with that error
[http://ubuntuforums.org/showthread.php?t=1628658](http://ubuntuforums.org/showthread.php?t=1628658)
But it doesn't seem that relevant

---

### Post by joshj70 on 2012-01-22
Alright. Sense I copied my backup onto my 80gb (my external decided to die on me about 2 months ago) I am working on moving it to a different location just to be safe.

> I found another thread with that error
[http://ubuntuforums.org/showthread.php?t=1628658](http://ubuntuforums.org/showthread.php?t=1628658)
But it doesn't seem that relevantI checked some of these threads out, and did a lot of googling, but nothing seemed that helpful. thanks though.

---

### Post by carl4926 on 2012-01-22
If grub was written only to the 250
Then if you pull the 250 out
The 80GB win drive should boot to windows, unless you have messed that up somehow.

---

### Post by joshj70 on 2012-01-23
Alright, so I finally got everything working again, but for some reason my programs aren't showing up, when I look in the application dropdown list it shows a few extra programs I added by hand, but the rest I installed aren't there, I checked and they are installed, they just won't show up. Any ideas?

---

### Post by carl4926 on 2012-01-23
Test a new user
See if it's the same there

---

### Post by joshj70 on 2012-01-23
I made a new user, but still no programs.

---

### Post by carl4926 on 2012-01-23
Try re-installing one that doesn't display
Does that make any difference?

---

### Post by joshj70 on 2012-01-23
Yes it does, I also found a forum that backs up and reinstalls all programs

[http://ubuntuforums.org/showthread.php?t=819396&highlight=application+list+installed+programs](http://ubuntuforums.org/showthread.php?t=819396&highlight=application+list+installed+programs)

Should I try this or is there an easier way to fix it?

---

### Post by carl4926 on 2012-01-24
Originally you quoted this

 > luckily I made a backup before any of this, finally I gave up and  reinstalled Ubuntu and copied my backup onto the new installation,

Clearly you made some big mistakes with respect to your backup.

I suggest you backup your personal files and do a completely fresh install

Of course with that in mind, assuming your personal files are backed up. I see no harm trying the idea in the link you posted. If it works, OK. If not, you are set for a new install.

My guess is that earlier you have not backed up the hidden folders in /home that contain the icons for the menu etc...

---

### Post by joshj70 on 2012-01-24
> Clearly you made some big mistakes with respect to your backup.
Thats what I assume too, but I have made a bunch of different backups with the same method and never ran into this problem, but anyway I was able to fix the program problem with the method I posted so everything is in working order again.

Thank you for the help, I appreciate it.

---

