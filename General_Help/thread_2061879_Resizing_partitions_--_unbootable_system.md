---
title: "Resizing partitions -- unbootable system"
date: 2012-09-23
forum: General Help
---

### Post by blenderfox on 2012-09-23
I am trying to get rid of the Windows partition on my system, and the current configuration is listed by parted as follows:

```
Model: ATA FUJITSU MHW2100B (scsi)
Disk /dev/sda: 100GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
                                                                                                                                      
Number  Start   End     Size    Type      File system     Flags                                                                       
 1      32.3kB  31.5GB  31.5GB  primary   ntfs            boot                                                                        
 2      31.5GB  100GB   68.6GB  extended                                                                                              
 5      31.5GB  99.0GB  67.5GB  logical   ext4
 6      99.0GB  100GB   1063MB  logical   linux-swap(v1)

```

and so I fire up gparted under the LiveCD and perform the following actions:

1. Delete the ntfs partition (1)
2. Grow the extended partition (2) to fill the space left by the now-deleted ntfs partition
3. Shift the ext4 partition (5) to the left.
4. Grow the ext4 partition to fit the space of the extended partition.

These all completed with no error, but when I reboot, I am left at a black screen with a flashing cursor in the top-left. No grub menu, no loading animation, nothing.

From experience repartition and resizing is also risky, so I made sure to reimage before I did this, and I restored back to my previous CloneZilla image which is where I am now. So, before I try again, I would like to know why my system became unbootable after I resized as listed above and how do I prevent/fix the problem?

---

### Post by black veils on 2012-09-23
the boot loader needs to be updated after changing partitions, this is at least one of the reasons.

if the boot loader is the only issue, then after you organise your partitions, boot **[this]("https://help.ubuntu.com/community/Boot-Repair")**.

---

### Post by blenderfox on 2012-09-24
I will give that a go. Thanks

---

### Post by blenderfox on 2012-09-24
Ah, I am sure I downloaded this a while ago... Nonetheless, as you say, I could run this straight from inside the Live CD, which will probably be my choice.

---

### Post by black veils on 2012-09-24
yes you can sort partitions on live system, then install the boot-repair ppa as instructed within that web page link.

it may or may not sort your booting problem, depends on if there is also something else causing a problem.

---

### Post by blenderfox on 2012-09-26
Well, it appears that I might have something deeper to do. I tried again yesterday evening and booted up the Boot Repair disc (physically burned it rather than use the PPA) and when I tried to reinstall grub through it, it gave me an embedding error, which unfortunately made no sense to me:

> grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and its use is discouraged.

---

### Post by oldfred on 2012-09-26
You should be installing to the MBR or first sector of hard drive or sda not sda1 or sda5 etc.

If trying to install grub2 to a PBR partition boot sector, it is not large enough and converts to blocklists or hard coded addresses. But you cannot boot a computer from a PBR unless using another boot loader in the MBR anyway.

---

### Post by blenderfox on 2012-09-26
> **oldfred said:**
> You should be installing to the MBR or first sector of hard drive or sda not sda1 or sda5 etc.

If trying to install grub2 to a PBR partition boot sector, it is not large enough and converts to blocklists or hard coded addresses. But you cannot boot a computer from a PBR unless using another boot loader in the MBR anyway.
When using Boot Repair and the recommended repair, I am not given a choice about where to install. I click on it, BR does its work and comes back with an error. I guess I will have to try again and use the advanced mode instead.

---

### Post by oldfred on 2012-09-26
The only time that message pops up when installing to a drive like sda not a partition like sda1 is if you have gpt  partitioning. But your first post showed MBR (msdos) partitioning.

---

### Post by blenderfox on 2012-09-26
Yes, you are right. Considering the NTFS partition is the one I want to get rid of, and the only partitions remaining on there are will be linux-related, can I convert from one to the other, then run BR?

---

### Post by oldfred on 2012-09-26
Most use MBR(msdos) as that  is the old system everyone knows and it has the limit of 4 primary partitions. The new gpt is required for drives over 2TB and UEFI boot systems. gpt is also recommended for gpt, but only if not booting with Windows in BIOS mode.

[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

But it should not matter which partitioning you have used, you should be able to install grub to the MBR. It is just with gpt you also need a bios_grub partition unformatted and only 1MB.

If you cannot install grub to MBR, it may be something else? A few BIOS have locked MBR for secuity and you have to change BIOS settings to reinstall to the MBR. 


Post this.

sudo fdisk -lu

---

### Post by blenderfox on 2012-09-27
```
$ sudo fdisk -lu

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000310bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61432559    30716248+   7  HPFS/NTFS/exFAT
/dev/sda2        61433854   195371007    66968577    5  Extended
/dev/sda5        61433856   193292287    65929216   83  Linux
/dev/sda6       193294336   195371007     1038336   82  Linux swap / Solaris

```

I do not have a >2TB partition so I am definitely not using GPT. As for locked MBR, I know that is not the case for my system as I have wiped and rewritten the MBR in the past, both intentionally and accidentally.... :P

---

### Post by bra|10n on 2012-09-27
Hi,
Just posting the following in case it is of some use to you, note the warning!

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT

```For the record I have 4 Ext 4 partitions on this drive, the usual 3 + /Data which do not show separately.

---

### Post by blenderfox on 2012-09-27
I do not get the warning, because as oldfred as pointed out, my drive runs a MBR, not GPT.

But back to the question at hand. My sda runs with a MPT and fails to boot when I delete the NTFS partition and resize the remainder. I still do not know why this fails, and I still do not understand why I get the embedding error when I try to reinstall grub via the Boot-Repair tool (unless I have missed something from the posts above)

Is there a way to convert between MBR style and GPT style? Although from what research I have done, I am not sure my system would boot because GPT requires a UEFI supporting motherboard, and my system is an old one, so there is a possibility it might not support it. But as before, I can always reimage. I can also convert before resizing.

---

### Post by bra|10n on 2012-09-27
Doesn't the MBR have to reside on a **primary** partition?

---

### Post by blenderfox on 2012-09-27
Sorry, I meant MPT (MSDOS Partition Table), not. :P Too many acronyms for my little brain to process. :P

---

### Post by bra|10n on 2012-09-27
> **momokoyukino said:**
> 
```
Model: ATA FUJITSU MHW2100B (scsi)
Disk /dev/sda: 100GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
                                                                                                                                      
Number  Start   End     Size    Type      File system     Flags                                                                       
[COLOR=Red] 1      32.3kB  31.5GB  31.5GB  primary   ntfs            boot      [/COLOR]                                                                  
 2      31.5GB  100GB   68.6GB  extended                                                                                              
 5      31.5GB  99.0GB  67.5GB  logical   ext4
 6      99.0GB  100GB   1063MB  logical   linux-swap(v1)

```and so I fire up gparted under the LiveCD and perform the following actions:

1. Delete the ntfs partition ([COLOR=Red]1[/COLOR])

I'm not very experienced with partition tables granted, but if you delete the partition highlighted in red, all I see is left is 1 extended partition containing two logical partitions, 1 ext4 and 1 swap?

---

### Post by blenderfox on 2012-09-27
That is correct. Then I resize the extended partition (2), then the logical partition within it(5) to make use of the space freed up by the NTFS partition being deleted. Simple deletion and resizing, but doing this seems to stop my machine from booting.

---

### Post by bra|10n on 2012-09-27
As you say. And as I said, I'm not an 'old hand' at this stuff by any stretch of the imagination, but going back to my earlier post;

> Doesn't the MBR have to reside on a **primary** partition?     It seems to me after your delete/resize your partitions, you still have no **primary** partition on which to install grub to...

If you look at your partition table I posted above you can see there is only 1 primary partition which in each test-case you have deleted.

Perhaps while you wisely have an image to restore to your machine, you might try the following:
delete sda1, create a new primary partition ext4 of 100Mb, then move/resize partitions to your liking as you have been doing. Then with your grub-recover cd you may be able to select your newly created sda1 partition to install grub to without the errors.

---

### Post by black veils on 2012-09-27
> **bra|10n said:**
> 
It seems to me after your delete/resize your partitions, you still have no **primary** partition on which to install grub to...

If you look at your partition table I posted above you can see there is only 1 primary partition which in each test-case you have deleted.

Perhaps while you wisely have an image to restore to your machine, you might try the following:
delete sda1, create a new primary partition ext4 of 100Mb, then move/resize partitions to your liking as you have been doing. Then with your grub-recover cd you may be able to select your newly created sda1 partition to install grub to without the errors.

that does seem like worth a try^  but an extended partition is a primary also, which made me think it should not need another.

---

### Post by blenderfox on 2012-09-27
I think what I will do first is image the state after deleting the NTFS. Whichever way I choose going forward after this point could work, or could aggravate the situation. I will record the fdisk outputs during this.

---

### Post by oldfred on 2012-09-27
You can convert from MBR to gpt, but I have never done it. But I use gpt on my 160GB drive just to learn about gpt and I boot with BIOS on a system from 2006. I even put gpt on my 16GB flash drive with a full install of Ubuntu in a 8GB partition. If booting with BIOS, you have to have a 1MB bios_grub flagged unformatted partition.

But some (primarily Intel) motherboards require a boot flag on a primary partition. That assumes Windows as that is a Windows requirement. Grub does not use a boot flag. But if your BIOS needs it, then you have to have one primary partition and have to have a boot flag on it. If booting with grub it can be any partition, not one you use to boot with. We have seen users with no primary partition boot with grub, but their BIOS did not require boot flag.

---

### Post by blenderfox on 2012-09-27
> **oldfred said:**
> You can convert from MBR to gpt, but I have never done it. But I use gpt on my 160GB drive just to learn about gpt and I boot with BIOS on a system from 2006. I even put gpt on my 16GB flash drive with a full install of Ubuntu in a 8GB partition. If booting with BIOS, you have to have a 1MB bios_grub flagged unformatted partition.

But some (primarily Intel) motherboards require a boot flag on a primary partition. That assumes Windows as that is a Windows requirement. Grub does not use a boot flag. But if your BIOS needs it, then you have to have one primary partition and have to have a boot flag on it. If booting with grub it can be any partition, not one you use to boot with. We have seen users with no primary partition boot with grub, but their BIOS did not require boot flag.
Considering I will not have Windows on sda after I am done, I guess the boot flag is the least of my problems.

---

### Post by blenderfox on 2012-09-27
Latest update. Deleting the NTFS partition and then rebooting it works. i.e. before I do any resizing, my system remains bootable. So it must be the resizing that is causing the problem.

---

### Post by bra|10n on 2012-09-27
> **momokoyukino said:**
> Latest update. Deleting the NTFS partition and then rebooting it works. i.e. before I do any resizing, my system remains bootable. So it must be the resizing that is causing the problem.

Is this because the MBR is still in place, despite having deleted sda1, (note sda1 starts @ 32.3kb). So presumably grub still shows "Windows" listed in the boot options also?

But if you move what is now the 'unformatted space' then the MBR becomes useless as it is no longer at the beginning of the drive, and why I suggested creating a new primary partition earlier.

Still, I could be wrong...

---

### Post by oldfred on 2012-09-27
Usually moving a partition does not change UUID and then it still boots. Are you doing something more?

But I do not like large / partitions but prefer either separate /home or just separate data partitions. Then you do not have to move anything. But I do data partitions as I want to mount them in multiple versions of Ubuntu I have installed.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by bra|10n on 2012-09-27
> **oldfred said:**
> Usually moving a partition does not change UUID and then it still boots. Are you doing something more?[]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")

With my limited knowledge of this I would have thought to move the partition would then require an EBR in place to continue to function, and cannot be done without the loss of data.

I'll say again, I could be wrong...

---

### Post by blenderfox on 2012-09-28
Open question, when I resize in gparted, I am asked to indicate which cylinder the partition starts from. Now, as bra|10n has pointed out, sda1 starts part way into the drive, I previously resized sda5 to cylinder 0 (i.e. as far left as I could go) -- would this have overwritten (wholly or partially) the MBR, causing the system not to boot any more?

---

### Post by bra|10n on 2012-09-28
Good question. I'm not able to say for sure, but I guess this resizing would be fine, as was the deletion of sda1. I think you trouble begins when you move this drive to the right or other(s) to the left, however you might like to say it.

---

### Post by blenderfox on 2012-09-28
> **bra|10n said:**
> Good question. I'm not able to say for sure, but I guess this resizing would be fine, as was the deletion of sda1. I think you trouble begins when you move this drive to the right or other(s) to the left, however you might like to say it.

My point was this bit from my fdisk listing:

$ sudo fdisk -lu

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61432559    30716248+   7  HPFS/NTFS/exFAT

As you can see, sda1 starts from 63, and not 0. So what I might try is resizing and moving my sda2 so that it also starts from 63, and see if that works.

---

### Post by oldfred on 2012-09-28
Grub installs its boot loader to the MBR which is the very first sector on a drive. Then it installs core.img to the area after the MBR. So if you tried to partition to the start of the drive you overwrote core.img or a important part of grub.

XP and older Ubuntu started at sector 63. Even grub legacy, Windows and security software use the area from the MBR to the first sector of sda1 as space to store things. 

Now all partitioning tools start at sector 2048. Windows Vista was the first to change to 2048. That is for compatibility with the new 4K drives, SSDs and with large drives a few sectors at the beginning do not matter.

---

### Post by blenderfox on 2012-09-28
> **oldfred said:**
> Grub installs its boot loader to the MBR which is the very first sector on a drive. Then it installs core.img to the area after the MBR. So if you tried to partition to the start of the drive you overwrote core.img or a important part of grub.

XP and older Ubuntu started at sector 63. Even grub legacy, Windows and security software use the area from the MBR to the first sector of sda1 as space to store things. 

Now all partitioning tools start at sector 2048. Windows Vista was the first to change to 2048. That is for compatibility with the new 4K drives, SSDs and with large drives a few sectors at the beginning do not matter.

I see, that explains this bit in my fdisk:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    61432559    30716248+   7  HPFS/NTFS/exFAT
```

As you pointed out it starts at sector 63. So if I resize it to start from 63, I should be fine. I do the resize and report back if there are any problems.

---

### Post by blenderfox on 2012-09-29
Problem now solved. My new layout is:

```
$ sudo fdisk -lu /dev/sda
Disk /dev/sda: 100 GB, 100027630080 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195366465 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda2            2048   195371007    97683232    5  Extended
Warning: Partition 2 does not end on cylinder boundary.                   
/dev/sda5            4096   193292287    96639007   83  Linux
Warning: Partition 5 does not end on cylinder boundary.                   
/dev/sda6       193294336   195371007     1036192   82  Linux swap
Warning: Partition 6 does not end on cylinder boundary.
```

Apart from the warnings, everything checks out. My system boots, and I have run update-grub2 to remove Windows from my grub menu.

You were right, older versions of the partitioning tools did not respect the space before the first partition, so the gparted I was using on my recovery CD was resizing all the way back to sector 0. When I updated my recovery CD, it resized back to 2048.

Now, to reimage for safety.

---

### Post by oldfred on 2012-09-29
Glad you have it resolved. :)

---

### Post by geoaraujo on 2012-09-29
> **oldfred said:**
> Glad you have it resolved. :)
But what about those warnings?

---

### Post by oldfred on 2012-09-29
Hard drive  access converted from cylinder, heads, sectors to LBA or logical block allocation which really is just sectors when hard drives went over 8GB. 

Or cylinders have not been used for 20 years. So you can ignore message. It is more important with SSD or new 4K drive on starting on sector count that can be divided by 8. End should not matter.

What is BIOS set to? It should be LBA, large or similar wording depending on type of BIOS, but not IDE.

[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

---

