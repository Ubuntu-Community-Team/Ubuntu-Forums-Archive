---
title: "Can't see external hard drive - want to write in linux and read on mac"
date: 2011-05-27
forum: General Help
---

### Post by MorrisseyJ on 2011-05-27
Hi, 

I am having trouble with an external hard drive (WD), connected via USB. 

My initial intention was to move some files from a linux machine (running natty) to a mac, running OSx. To do so i took the external hard drive, formatted it to FAT and copied the files across. When the hard drive was plugged into the mac it said that the disk was not readable. 

I then looked for help online, but couldn't find much. Since mac can read FAT i thought it might be a permissions issue, but when i right clicked on the drive and went to the permissions tab i got:
> Permissions of <disk> could not be determinedTo check if it was a permissions thing i booted to windows (XP) and plugged in the drive. Windows found the drive but would not let me access it in 'My Computer'. When i right clicked on 'my computer' and went to 'manage', i found that the drive was there but not initialized. So i right clicked and 'initialized'. i still couldn't see the drive in my computer, even though the drive now registered as initialized in disk manager.

When i came back to Ubuntu to try and fiddle some more i found the external drive would not show up when i plugged it in. That said > sudo fdisk -l gives:

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd53d826f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         243     1951866   1b  Hidden W95 FAT32
/dev/sda2   *         244        2793    20480870+   c  W95 FAT32 (LBA)
/dev/sda3            2793        9730    55716865    5  Extended
/dev/sda5            2793        9616    54800384   83  Linux
/dev/sda6            9616        9730      915456   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1c4ff6db

   Device Boot      Start         End      Blocks   Id  SystemSo it looks like it is seeing the 250GB external drive but not letting me do anything to it. 

I have seen threads online about chmod etc, but don't understand this stuff and, from what i have read, it seems that stuff is not relevant to FAT formats.

If anyone can tell me how i can get the drive back, that would be great. It would be wonderful if someone could tell me how to format it/set the permissions so that the files could be written on linux and read on a mac.

Thanks.

---

### Post by srs5694 on 2011-05-27
I'm not entirely sure what happened at all the stages, but right now you've got a disk with incomplete traces of a GUID Partition Table (GPT). A 100% legal GPT would be readable by both Linux and Mac OS X, but not by Windows XP. (Whether the filesystem(s) stored on the partition(s) defined by the GPT would be readable is another matter, though.) It's unclear how much of the GPT data remains, but that's irrelevant. I recommend you do this:


[list=1]
[*]Connect the drive to the Mac. (It might tell you that the disk is uninitialized, in which case it will prompt you to do the next step automatically.)
[*]Launch the Mac's Disk Utility (in the Utilities folder).
[*]In the pane on the left of the window, select the whole drive (*not* any specific partition on the drive; the main drive entry).
[*]In the pane on the right of the window, click Partition.
[*]Under Volume Scheme, change the entry from Current to 1 Partition.
[*]**Important:** Click Options and, in the resulting dialog box, select Master Boot Record, then close the dialog box. This step tells Disk Utility to wipe the remaining GPT data and convert the disk for MBR use.
[*]Under Volume Information, Format, select MS-DOS (FAT).
[*]Optional: Change the volume's Name.
[*]Click Apply. You'll be asked to confirm the operation. Do so.
[/list]


This procedure will prepare the disk as a FAT disk that should be readable by OS X, Linux, and Windows. You can now eject the disk and move it between systems as you see fit. The same operation could be performed under GParted, with theoretically identical results, but of course the details of the operation would differ.

If you try the disk and you have problems under Linux, please post back before you try re-initializing the disk. Include the output of the following two commands under Linux:

```

sudo fdisk -l
sudo blkid

```

Please post the results between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags; the [noparse]> [/noparse] and [noparse][/noparse] tags you used in your original post don't preserve the columnar output of fdisk, which makes it hard to read.

---

### Post by MorrisseyJ on 2011-05-27
Thanks very much for the detailed instructions. I will try this over the weekend and get back to you.

Apologies about the incorrect use of the quotation function.

---

### Post by MorrisseyJ on 2011-05-28
srs5694: Thanks very much. Worked perfectly.

---

