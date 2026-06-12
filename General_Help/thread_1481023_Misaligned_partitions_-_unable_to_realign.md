---
title: "Misaligned partitions - unable to realign"
date: 2010-05-12
forum: General Help
---

### Post by Quaxo76 on 2010-05-12
I had 9.10 installed on my laptop, with a 250GB HD. When the moment came to install 10.04, I decided to upgrade the HD with a new 500GB one. But I had several data partitions on the old HD that I didn't want to loose. So I just ghosted the old drive to the new one with the command
```
dd bs=1M if=/dev/sdb of=/dev/sda
```
and then installed 10.04 on the new drive, wiping the old /home and / partitions and replacing them with new ones, but keeping the various data partitions.
Now, when I open Disk Utility, it says that all the data partitions (but not the new ones) are misaligned, and this will cause poor performance.
I found out that the problem is that my new drive uses 4K sectors instead of 512b sectors, but the drive firmware "translates" the coordinates transparently so that the computer can assume it's a standard 512b/sector drive. But this lowers the performance.
The first thing I tried was to open GParted and slightly modify the start/end points of a partition, hoping that the new partition ends would "stick" to 4K boundaries, thus eliminating the misalignment; but this didn't work (apparently GParted knows nothing at all about this alignment thing).
I tried using the command-line Parted command, and setting the start/end sectors of the partitions to a multiple of 8, but:
- parted doesn't let me modify an existing partitions, it wants me to wipe the old one and recreate another (and re-copy the old data on it) -> time consuming.
- Even if I do so, it doesn't work: I was able to correctly align the first partition on the disk (now Disk Utility doesn't complain about that anymore) but not the others. When I try to enter the new start/end sectors for the second partition, parted says that those numbers will not produce an aligned partition.

What can I do to get my partitions aligned? Is there a GParted equivalent that is aware of this 4K sectors thing? I could wipe the disk but would of course prefer not to.

It's interesting to note that the Ubuntu installer created the two new partitions correctly aligned; is there a way to use that program now, to fix things?

Thanks in advance,
Cristian

---

### Post by srs5694 on 2010-05-12
First, you should try to verify that you've got a disk with 4096-byte sectors; it's conceivable that your disk was misidentified or that the message you read was a generic one. To the best of my knowledge, Western Digital is the only manufacturer making such drives at the moment. Check the drive's make and model. Various GUI tools will give you this information, as will "cat /proc/scsi/scsi" at a command-mode prompt. (You'll need to pick your hard disk out from other devices, such as you DVD drive.) With the manufacturer and model name in hand, check with the manufacturer to see if it uses 4096-byte sectors. In theory, you should be able to determine this information by checking certain Linux files, such as /sys/block/sdX/queue/physical_block_size and /sys/block/sdX/queue/logical_block_size, where "sdX" is your device filename (probably sda); if these files have identical values, then your disk is *not* affected.



If your disk does have 4096-byte physical sectors but 512-byte logical sectors, it may be possible to do something about it using raw dd copies; however, that's a very risky proposition. Given the [likely performance degradation](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html) in doing such copies, it's also likely to be faster to create fresh partitions and then copy your original disk back to the new one, so that's what I'd recommend you do.

---

### Post by Quaxo76 on 2010-05-12
Thank you for your reply!

> **srs5694 said:**
> First, you should try to verify that you've got a disk with 4096-byte sectors;
It is a 4k drive, I had already checked. It's a Toshiba MK5059GSX, and online specs say it's 4k; plus, /sys/block/sda/queue/logical_block_size reports 512, while physical reports 4096.


> **srs5694 said:**
> If your disk does have 4096-byte physical sectors but 512-byte logical sectors, it may be possible to do something about it using raw dd copies
That's actually what I tried to do. I originally made a dd copy of the WHOLE old disk, and that resulted in a badly misaligned disk. Wiping a partition, recreating it with GParted, and dd'ing the old partition into the new one (i.e. dd if=/dev/sdb1 of=/dev/sda1) still gave me a misalignment.
> **srs5694 said:**
>  it's also likely to be faster to create fresh partitions and then copy your original disk back to the new one, so that's what I'd recommend you do.
I would be prepared to do that, but as I said, I don't know how to create partitions that are aligned in the first place. When I wipe a partition and recreate it with GParted (even "wiggling" the end points) GParted still makes misaligned partitions, as if it had no clue it's a 4k drive.

Cristian

---

### Post by srs5694 on 2010-05-13
> **Quaxo76 said:**
> It is a 4k drive, I had already checked. It's a Toshiba MK5059GSX, and online specs say it's 4k; plus, /sys/block/sda/queue/logical_block_size reports 512, while physical reports 4096.

Interesting. I wasn't even aware that Toshiba manufactured hard disks. (Then too, maybe they don't; it could be that WD is the OEM. Not that it matters, really....)

> That's actually what I tried to do. I originally made a dd copy of the WHOLE old disk, and that resulted in a badly misaligned disk. Wiping a partition, recreating it with GParted, and dd'ing the old partition into the new one (i.e. dd if=/dev/sdb1 of=/dev/sda1) still gave me a misalignment.

I would be prepared to do that, but as I said, I don't know how to create partitions that are aligned in the first place. When I wipe a partition and recreate it with GParted (even "wiggling" the end points) GParted still makes misaligned partitions, as if it had no clue it's a 4k drive.

I didn't realize you didn't know how to create properly aligned partitions. It's not too hard, actually, although GParted isn't the best tool for this. Check [this article for details.](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html) I recommend using fdisk, the text-mode parted, or gdisk for this. (Use gdisk only for GPT disks, though.) With fdisk or parted, you need to use the appropriate options ("c" and "u" in fdisk, or "unit s" in parted) and carefully check the sector start points. With recent versions of gdisk, it should align properly from the start -- but the version of gdisk that Ubuntu 10.04 installs is old enough that it requires careful attention to the partition start points.

---

### Post by Quaxo76 on 2010-05-13
> **srs5694 said:**
> 
I didn't realize you didn't know how to create properly aligned partitions. It's not too hard, actually, although GParted isn't the best tool for this. Check [this article for details.](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html) I recommend using fdisk, the text-mode parted, or gdisk for this. (Use gdisk only for GPT disks, though.) With fdisk or parted, you need to use the appropriate options ("c" and "u" in fdisk, or "unit s" in parted) and carefully check the sector start points. With recent versions of gdisk, it should align properly from the start -- but the version of gdisk that Ubuntu 10.04 installs is old enough that it requires careful attention to the partition start points.

I had already read that article, and tried the text Parted. To quote myself from my original message:
"I tried using the command-line Parted command, and setting the start/end sectors of the partitions to a multiple of 8, but:
- parted doesn't let me modify an existing partitions, it wants me to wipe the old one and recreate another (and re-copy the old data on it) -> time consuming.
- Even if I do so, it doesn't work: I was able to correctly align the first partition on the disk (now Disk Utility doesn't complain about that anymore) but not the others. When I try to enter the new start/end sectors for the second partition, parted says that those numbers will not produce an aligned partition."

So, for some reason I don't know, even parted has problems with this. To be sure to be on a 4K boundary, I tried to create the new partition with 8 consequent start sectors and 8 consequent end sectors (yes, I actually tried all 64 combinations, I thought I would find an aligned combination that way) but parted said, every single time, that those start/end points would create a misaligned partition. So, parted IS aware of the 4k problem, but for some reason can't easily create an aligned partition just by setting the start/end sectors as multiples of 8...

---

### Post by srs5694 on 2010-05-13
If you're having problems with parted, try fdisk (for MBR) or gdisk (for GPT). IMHO, parted tries to add too many layers to the partitioning task. This produces a simplified user interface when it works, but things can also go wrong in any of the layers, which can cause problems. To work around those problems, you've often got to resort to more direct partitioning tools (fdisk or gdisk). Note that neither fdisk nor gdisk supports any filesystem operations, which means you won't be able to directly resize the partitions or move their contents within these programs themselves.

---

### Post by Quaxo76 on 2010-05-15
I tried with fdisk. I was able to realign the second partition... launching fdisk with the -u option shows start/end/size in sectors instead of cylinders - but it still uses logical sectors instead of physical, so I had to be careful to set a multiple of 8 as a start sector. Then I restored the contents of the partition from a backup.
Now I have another problem... The next partition I need to align is not a primary partition, but logical (an "extended" partition). It contains several sub-partitions which total over 250GB of data, and I have no room to store a backup of them anywhere. Fdisk doesn't allow me to move the partition start point, I have to wipe it and start over, but I can't because I can't make a backup. So, how can I just move the start of the extended partition a bit without wiping it? If I can align the extended partition, then I can fix the partitions contained in it by backing up and wiping them one by one...

---

### Post by Quaxo76 on 2010-05-15
Disaaster!!
With fdisk I removed a partition and re-created it; after doing that, fdisk warned me that I had to reboot before the Kernel can be aware of the modifications; I rebooted, and... Grub doesn't load! It says "Invalid filesystem" or something like that, and drops me to a grub-rescue console; but the usual commands (find, root, setup) don't work. The command ls returns a list of partitions ( (hd0), (hd0,1) and so on) but ls'ing them says either "invalid filesystem" or "file not found"...
The data on the hd is still there, if I boot from a livecd I can access the partitions (both my / and /home are still ok).
It's possible that the partition names have changed or something, but how do I rescue my system??? Any help is GREATLY appreciated!!

---

### Post by srs5694 on 2010-05-15
> **Quaxo76 said:**
> Now I have another problem... The next partition I need to align is not a primary partition, but logical (an "extended" partition). It contains several sub-partitions which total over 250GB of data, and I have no room to store a backup of them anywhere. Fdisk doesn't allow me to move the partition start point, I have to wipe it and start over, but I can't because I can't make a backup. So, how can I just move the start of the extended partition a bit without wiping it? If I can align the extended partition, then I can fix the partitions contained in it by backing up and wiping them one by one...

You can move the start of the *extended* partition using sfdisk; however, there's very little point to that because you need to adjust the starts of the *logical* partitions it contains, and their start points are independent of the extended partition's start point (except that the logical partitions must be within the extended partition).

> Disaaster!!
With fdisk I removed a partition and re-created it; after doing that,  fdisk warned me that I had to reboot before the Kernel can be aware of  the modifications; I rebooted, and... Grub doesn't load! It says  "Invalid filesystem" or something like that, and drops me to a  grub-rescue console; but the usual commands (find, root, setup) don't  work. The command ls returns a list of partitions ( (hd0), (hd0,1) and  so on) but ls'ing them says either "invalid filesystem" or "file not  found"...
The data on the hd is still there, if I boot from a livecd I can access  the partitions (both my / and /home are still ok).
It's possible that the partition names have changed or something, but  how do I rescue my system??? Any help is GREATLY appreciated!!

If you deleted a partition using fdisk and then re-created it using a different start point, then the filesystem data are effectively useless because they all reside in the wrong place now. If you moved the start point up, the start of the filesystem also now resides outside of the partition. If you can reverse the process (that is, if you remember exactly where the partition used to start), you can fix it. Otherwise you might need to delete the partition (using fdisk) and then use testdisk to try to locate the filesystem and re-create the original partition.

Another possibility might be to use dd to move all the data in the partition by enough to put it into the right location; however, you should read and *thoroughly understand* the dd man page to see how it handles overlapping source and target areas. It wouldn't do to have it perform the copy in the wrong direction, which would end up completely wiping out your data, giving you absolutely no hope of recovery. I'm afraid I don't know enough about dd's features on this score to give you detailed advice, except to *be very very careful!* As I said in my very first post, your best bet is to wipe your current partitions and copy from your original source disk. If that's no longer an option, then you'll just have to try for data recovery.

---

### Post by Quaxo76 on 2010-05-15
> If you deleted a partition using fdisk and then re-created it using a different start point, then the filesystem data are effectively useless because they all reside in the wrong place now. If you moved the start point up, the start of the filesystem also now resides outside of the partition. If you can reverse the process (that is, if you remember exactly where the partition used to start), you can fix it. Otherwise you might need to delete the partition (using fdisk) and then use testdisk to try to locate the filesystem and re-create the original partition.

Actually, I just deleted the partition (and its filesystem data), and recreated a new partition and filesystem. I had backed up the data of that partition, and was planning to recreate it, but for now, the new partition is empty. And it was a data partition, I didn't touch the system partitions at all. So I thought the system should boot normally.
But something must have gone bad with fdisk: though I only modified a data partition (the 6th partition on the drive), now grub doesn't start at all, giving the error I reported. Somehow fdisk must have corrupted some super-structure... I don't know.
But if I boot from a live cd, I can see that all my data is there. So, data recovery is not a problem; I just have to fix grub.
The problem is that I need the computer, and I can't spend too much time just fixing this... Is there an easy way to reinstall grub on the hd (and re-configure it for boot) using the livecd?

---

### Post by srs5694 on 2010-05-15
Chances are one of two things is happening:


[list]
[*]GRUB's second stage may have been installed in the partition, so when you moved it and created a new filesystem on it, this confused GRUB's stage 1 or 1.5. If this is the cause, you'll need to re-install GRUB (that is, run "grub-install /dev/sda" or a similar command).
[*]GRUB may have included references to the partition or a subsequent partition in its configuration file (/boot/grub/menu.lst or /boot/grub/grub.cfg, depending on your GRUB version). If the partition number changed, as it might have confused GRUB, because now the partition number is pointing to another reference. If this is the cause, re-installing GRUB might not help; you'll need to load the GRUB configuration file in an editor and make appropriate changes to partition references (say, change /dev/sda7 to /dev/sda6 or whatever the appropriate change is).
[/list]


If you need to re-install GRUB, I believe there are ways to do this from the Ubuntu live CD/DVD, but I don't recall the details. Alternatively, you could try [Super GRUB Disk,](http://www.supergrubdisk.org) which can probably get your regular installation booted. From there, you can re-install GRUB.

---

### Post by Quaxo76 on 2010-05-15
Booting from the livecd, I run the command ```
sudo grub-install /dev/sda
```and I get the following error:```
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?)
No path or device is specified.
Try '/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option '--modules' explicitly.
```
Running the command ```
sudo grub-mkconfig /dev/sda
```gives this error:```
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)
```
If I run 'ls /dev' I can see all the usual devices.
All this is from the lucid livecd.
In /boot/grub there is no file named 'menu.lst'.

---

