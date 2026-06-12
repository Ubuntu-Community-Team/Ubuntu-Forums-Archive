---
title: "Copied partitons to new HDD, cannot boot into windows"
date: 2012-08-06
forum: General Help
---

### Post by krytorii on 2012-08-06
So I got myself a new hard drive and went and copied the partitions from the old to the new using the copy function on gparted. I then used the boot-repair livecd. Kubuntu boots fine, but I cannot get windows xp to start.

I don't have any errors, I just get a little underscore flashing in the top left corner of the screen after I select windows xp in grub, this usually happens for about a second or so before windows starts IIRC.

I also don't have an installation disc for xp ether, I've read that it can be fixed from that but I do believe the previous owners of the computer threw it out.

---

### Post by Kopkins on 2012-08-06
You're using the hard drive in the same computer, right?

I'm assuming the new hard drive was blank. You could 'dd' the contents of your old HD to the new HD. This would certainly take a long time, but I've dd'ed a HD onto another, wiped the HD I copied from, installed a series of linux operating systems, then dd'ed the original contents of the HD back onto it and booted windows fine.

Best of luck,
Kopkins

---

### Post by krytorii on 2012-08-06
Doublepost

---

### Post by krytorii on 2012-08-06
DD? What is that?

Also, until my new sata cable arrives, I can't use both the old and new hard drives at the same time... My hard drive came earlier than expected, so I've been copying from the old hard drive to the IDE one, and from that to the new one.

I can always wait until the cable arrives if need be, but I can still access the old drive with relative ease.

---

### Post by ahallubuntu on 2012-08-06
Did you used to boot XP with Grub previously, on the old hard drive?

Did you change the partition scheme at all on the new drive?  That is, was XP previously on sda1 and now it's on sda2?   Is XP still in a primary partition?

Since you can boot kubuntu, I'd also do that and do "sudo update-grub" from a terminal one time and try booting XP again.

---

### Post by krytorii on 2012-08-07
> **ahallubuntu said:**
> Did you used to boot XP with Grub previously, on the old hard drive?

Did you change the partition scheme at all on the new drive?  That is, was XP previously on sda1 and now it's on sda2?   Is XP still in a primary partition?

Since you can boot kubuntu, I'd also do that and do "sudo update-grub" from a terminal one time and try booting XP again.

Yeah, xp worked fine before when I've dual booted.

I do believe that the label has changed, yes. It used to be on sda2 now it's on sda4 (sda1 used to be some partition that came preinstalled, I think it's used for recovery/factory reset but I can't access that wither). The partition order for windows did not chance, this recovery one immediately followed by xp.

---

### Post by krytorii on 2012-08-07
I'm trying to follow this guide: [http://ubuntuforums.org/showthread.php?t=916146](http://ubuntuforums.org/showthread.php?t=916146)

I'm on step 3, I had to change the fdisk command to make it work, it really didn't like the u.
```
sudo fdisk -l /dev/sda
```The output of which is:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000e061c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       773597184  1140860927   183631872    7  HPFS/NTFS/exFAT
/dev/sda2      1672341504  1953523711   140591104    5  Extended
/dev/sda3            2048    12582911     6290432    b  W95 FAT32
/dev/sda4   *    12582912   773597183   380507136    7  HPFS/NTFS/exFAT
/dev/sda5      1949429760  1953523711     2046976   82  Linux swap / Solaris
/dev/sda6      1898229760  1949429759    25600000   83  Linux
/dev/sda7      1751298048  1812738047    30720000   83  Linux

```sda4 is the windows partiton, sda3 is the recovery partition.

The actualorder of the partitions is:sda3, sda4, sda1, sda.
gparted screenshot for a nice picture:
[IMG]http://ubuntuone.com/5ZtzcUFY1UsQiIsKBweoZf[/IMG]


I'm going to attempt part 3 on sda3. Wish me luck.

UPDATE: So I reckon I did step 3 correctly. However 4 and 5 are eluding me. In step 4 I cannot find the menu.lst,  in step 5 I can't see that I need to change anything. For anyone who's looking my boot.ini is:

```
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect$
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
```

I might go looking to see if the menu.lst is in another partition or something...

---

### Post by Mark Phelps on 2012-08-07
The menu.lst file hasn't been used in a long time.  It was the config file for the earlier version of GRUB.  Since GRUB2 came out, that file isn't used anymore.

---

### Post by krytorii on 2012-08-07
> **Mark Phelps said:**
> The menu.lst file hasn't been used in a long time.  It was the config file for the earlier version of GRUB.  Since GRUB2 came out, that file isn't used anymore.

I see...

I'm just gonna start from scratch I think. I have the original copy of the windows partition which still works.

---

### Post by vexorian on 2012-08-07
> **krytorii said:**
> So I got myself a new hard drive and went and copied the partitions from the old to the new using the copy function on gparted. I then used the boot-repair livecd. Kubuntu boots fine, but I cannot get windows xp to start.

I don't have any errors, I just get a little underscore flashing in the top left corner of the screen after I select windows xp in grub, this usually happens for about a second or so before windows starts IIRC.

I also don't have an installation disc for xp ether, I've read that it can be fixed from that but I do believe the previous owners of the computer threw it out.
Windows XP has something that makes it go into that sort of issue when a piece of hardware has changed. It is odd that it would happen if all you changed was the position of the hard drive, but maybe it did.

Another possibility could be that windows assigns a letter different than C:\ to the partition and havok breaks. Since you have many fat32 and ntfs this could be what's going on. Windows tends to assign C:\ to the first supported partition in the first hard drive.

---

### Post by krytorii on 2012-08-13
Right, my new sata cable finally arrived so I can sort this out without so much effort copying.

> **vexorian said:**
> Windows XP has something that makes it go into that sort of issue when a piece of hardware has changed. It is odd that it would happen if all you changed was the position of the hard drive, but maybe it did.

Another possibility could be that windows assigns a letter different than C:\ to the partition and havok breaks. Since you have many fat32 and ntfs this could be what's going on. Windows tends to assign C:\ to the first supported partition in the first hard drive.

It always used to boot with the same configuration of partitions. I also went and added the lba flag to sda3 (the first partition) as it was on my old HDD.

I might end up deleting a load of steam games from my windows partition, copying as much as I can to my original hard drive and the rest to a spare I have lying around, and then just cloning the whole disk rather than the partition.

I've used clonezilla to copy across the 2 windows partitions as well, but there's no improvement... I still get the same blank screen.

---

### Post by oldfred on 2012-08-13
Windows has to be in a primary NTFS partition with the boot flag. It also has info in the PBR - partition boot sector on what system to boot ntldr for XP or bootmgr for Vista/7. It also has the partition start sector and size, so any change means you have to run repairs including chkdsk and fixBoot. Also if XP the partition is hard coded into boot.ini and must match the partition you have installed into. you are showing sda4, but boot.ini says partition(3).

---

### Post by antmenj on 2012-08-21
I have a related question.

I have partimaged an XP partition.  I am trying to put it back and it started at sector 63.  How do I make gparted start a partition at sector 63 rather than 2048?

Edit
The gparted forum is down due to HDD failure so I'm asking here.

---

### Post by Kopkins on 2012-08-22
You will likely get more replies by starting your own thread.

I don't know how to solve your problem.

Best of luck,
Kopkins

---

