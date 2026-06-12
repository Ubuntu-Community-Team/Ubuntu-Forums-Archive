---
title: "grub and partition problems"
date: 2006-06-09
forum: General Help
---

### Post by m.musashi on 2006-06-09
I finally got around to updating my Dapper beta (or was it an alpha) install on my desktop and I've run into a couple problems.

[COLOR="Red"]BACKGROUND[/COLOR]

I have a 200 GB SATA drive and 80 GB ATA drive. The SATA drive has XP and I just got done doing a clean install of that (what a pain in the a**). The 80GB drive is partitioned and has half for fat32 storage and the other half as a Suse 10.1 install.

Using a downloaded CD I booted into a live session and then clicked the install icon. I told it to repartition the 200GB drive and use the space for Ubuntu. All went well.

[COLOR="Red"]PROBLEM 1[/COLOR]

However, when I reboot I get an error saying "error loading operating system). No grub menu or anything. When I set the 80GB drive to boot I do get the grub menu.

Question 1 - So, how did ubuntu install on the 200GB SATA drive but add grub to the 80GB ATA drive? Seems odd. However, it works.

[COLOR="Red"]PROBLEM 2[/COLOR]

While this setup should give me a total of 4 partitions (XP, Ubuntu, Suse, and a fat32 partition), I in fact have 5 with only the Ubuntu partion mounted. The others are the XP partion, an unknown 14.2 GB partition, an unknown 21.1 GB partion (these could be Suse but why 2? I am pretty certain they are part of the 80 GB drive). And then my XP, Ubuntu and fat32. All give me the error "unable to mount the selected partition."

Question 2 - I thought Dapper automatically mounted all drives - at least it does on both of my laptops. Any thoughts?

---

### Post by Ramses de Norre on 2006-06-09
Problem 1: you can reinstall grub to the sata drive if you want, but if it works from the other one this isn't really a problem I guess. I think grub just installed to the drive with the active mbr, in your case the ata drive.

Problem 2: What's the output of sudo fdisk -l and mount?

---

### Post by m.musashi on 2006-06-09
[QUOTE=Ramses de Norre]Problem 1: you can reinstall grub to the sata drive if you want, but if it works from the other one this isn't really a problem I guess. I think grub just installed to the drive with the active mbr, in your case the ata drive.[/quote]
The active mbr should have been the SATA drive as that is where XP is and the drive I have been booting from. Although Suse also installed a boot loader (grub?) on the ATA drive so maybe that just looked more friendly to the installer.

Do you know how I can install grub on the SATA drive? I like being able to boot from either in case I have problems.

> Problem 2: What's the output of sudo fdisk -l and mount?
I'm not sure exactly how to use those commands but fdisk -l gave
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12498   100390153+   7  HPFS/NTFS
/dev/sda2           12499       23967    92124742+  83  Linux
/dev/sda3           23968       24321     2843505    5  Extended
/dev/sda5           23968       24321     2843473+  82  Linux swap / Solaris

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4943    39704616    c  W95 FAT32 (LBA)
/dev/hdc2   *        4944        9729    38443545    f  W95 Ext'd (LBA)
/dev/hdc5            4944        5125     1461883+  82  Linux swap / Solaris
/dev/hdc6            5126        6975    14860093+  83  Linux
/dev/hdc7            6976        9729    22121473+  83  Linux
```

Thanks for the help.

---

### Post by Ramses de Norre on 2006-06-09
The ata is hdc, no? Do ```
sudo grub-install /dev/hdc
```

You do have two ext3 partitions on hdc: ```
/dev/hdc6            5126        6975    14860093+  83  Linux
/dev/hdc7            6976        9729    22121473+  83  Linux
```
How do you try to mount them?

---

### Post by m.musashi on 2006-06-09
hdc is that ATA drive but that is the drive that has grub now. I'd like to add it to the SATA drive (sda). However, from your post I think I can figure it out.

> You do have two ext3 partitions on hdc:
This makes sense but I don't know why. Suse didn't install all that nicely. The partitioner was frustrating (although so is the new one in Dapper). Since I had an earlier flight of Dapper on that drive maybe the Suse install left it and made a new partition for itself. That wasn't what I wanted though.

> How do you try to mount them?
Actually, I haven't tried to. I was under the impression that Dapper did this automatically. They do show up in nautilus. If I can remember how to do a screen shot I can show you.

---

### Post by Ramses de Norre on 2006-06-09
Ow yes :D replace hdc by sda ;)

I make screenshots by this (imagemagick needs to be installed) ```
import -window root ~/screenshot.png
```
Do you mean they show up under computer:/// ? If so you can right click>mount.

---

### Post by m.musashi on 2006-06-09
Here are a couple images. You can see the various partitions. When I try and double click or right click and choose mount I get the error you see.

---

### Post by m.musashi on 2006-06-09
Oops, should have clicked the show more details. Here is what that says:
```
error: device /dev/hdc1 is not removable

error: could not execute pmount
```

---

### Post by m.musashi on 2006-06-11
Okay, I thought that my drive mounting problem might have something to do with not having the main board drivers installed so I did that but still no luck.

Suggestions welcome.

Thanks.

---

