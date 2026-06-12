---
title: "Pending Doom?  HD Error"
date: 2011-09-25
forum: General Help
---

### Post by Quarkrad on 2011-09-25
Running 10.10  I have two HDs one I use for OSs (sda) and the other for simple storage (sdb).  On sda I have 4 partitions - win7 (sda1), Ubuntu 10.10 (sda2), storage (sda3) and a swap partition.  sdb has just a single partition that I use for backup.  I can see all this graphically using **System/Admin/Disk Utility**.  However, when I launch Gparted and look at my sda HD it is all greyed out as a single partition.  The partition is unallocated with a yellow warning triangle.  If I right click on the partition and choose **Information** there is another warning triangle that says:  **Invalid partition table on /dev/sda - wrong signature 0.** My whole pc is running as normal - I have no problem with it but potentially worried about what Gparted is telling me.  The other odd thing is that originally I set up a 8GB swap partition at the end of my disk but now **System/Admin/Disk Utility** shows it as Free 8.4 GB.  Any help appreciated.

---

### Post by patryk77 on 2011-09-25
Does GParted ask for a password on startup?

It might just be misconfigured and not have permissions to read the partition details.

Try in the terminal:
sudo fdisk -l

Edit: Oh, and every time is a good time, but now might be an even better time for a backup ;)

---

### Post by Quarkrad on 2011-09-25
Yes - I do get asked for my password when I launch Gparted.  This is the output from terminal:

dad@dadubuntu:~$ sudo fdisk -l
[sudo] password for dad: 
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfa0c1e50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12749   102398976    7  HPFS/NTFS
/dev/sda2           12749       25497   102400000   83  Linux
/dev/sda3           25497       59782   275393536    7  HPFS/NTFS
/dev/sda4           59782       60802     8192000   85  Linux extended

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x638c197f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976760832    5  Extended
/dev/sdb5               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b34ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      121602   976760832    5  Extended
/dev/sdg5               1      121602   976759808    7  HPFS/NTFS

---

### Post by patryk77 on 2011-09-25
> **Quarkrad said:**
> The other odd thing is that originally I set up a 8GB swap partition at the end of my disk but now **System/Admin/Disk Utility** shows it as Free 8.4 GB.  Any help appreciated.

```
/dev/sda4 59782 60802 8192000 85 Linux extended
```

That is indeed very weird...

sda4 should be ID 82, Linux Swap, not 85 :\

Though I will not actually venture a guess as to what could be wrong, because I have no idea... Sorry

---

### Post by Quarkrad on 2011-09-25
Thanks for your help.  Perhaps somebody else could advise - I do not really want to have to do another rebuild.

---

### Post by matchett808 on 2011-09-25
Not sure, but i would maybe try reformating and preparing the 8gig partition as swap again, looks like a swapiness problem to me!


before doing that wait for any other suggestions though!! lol

---

### Post by Quarkrad on 2011-09-25
Do you mean reformatting the whole HD?  I can see the 8GB partition via **System/Admin/Disk Utility**y and when I click on the partition there is an option to Format Drive (Erase the partition or drive). Clicking on Format Drive brings up another window with some options  - **Scheme, MasterBoot Record, GUID Partition Table, Don't Partition, Apple Partition Map.**  I'm in unknown territory here - which one do I select to reformat the (8GB) partition as swap?  (If I reboot to a LiveCD and look at my (sda) HD via Gparted I get the same error as per original post. I don't mind having a go at re-formating the 8GB partition but I would prefer, if possible, not to have to reformat the whole HD and rebuild two OSs -especially as my PC is functioning 100%.

---

### Post by Quarkrad on 2011-09-26
bump

---

### Post by Grenage on 2011-09-26
> **Quarkrad said:**
> Do you mean reformatting the whole HD?  I can see the 8GB partition via **System/Admin/Disk Utility**y and when I click on the partition there is an option to Format Drive (Erase the partition or drive). Clicking on Format Drive brings up another window with some options  - **Scheme, MasterBoot Record, GUID Partition Table, Don't Partition, Apple Partition Map.**  I'm in unknown territory here - which one do I select to reformat the (8GB) partition as swap?  (If I reboot to a LiveCD and look at my (sda) HD via Gparted I get the same error as per original post. I don't mind having a go at re-formating the 8GB partition but I would prefer, if possible, not to have to reformat the whole HD and rebuild two OSs -especially as my PC is functioning 100%.

Hi there,

Boot from the CD and open gparted again - you can delete and reformat the partition as swap from within gparted.  I recommend deleting the partition, and not just trying to format it.  This will cause the UUID to change, so you'll have to make the appropriate change in fstab.  For example, after formatting the partition:

```
sudo blkid
```
You'll get output such as:
```
/dev/sda1: UUID="f3d2d07c-f275-4954-bc0e-1c47c000d1e4" TYPE="ext4" 
/dev/sda5: UUID="e6626634-7cc2-4bfe-bc15-5c8c5d6bf721" TYPE="swap" 
/dev/sdb1: LABEL="archive" UUID="410ed6c9-48b6-43a0-af15-fa1062c0df04" TYPE="ext3"
```
Make note of the swap's UUID, then open your fstab file:
```
gksu gedit /etc/fstab
```
Change the old swap UUID for the new (if changed) UUID.

---

### Post by Quarkrad on 2011-09-26
The problem is when I open Gparted via LiveCD all I 'see' for my HD is a grey bar saying **unallocated 465.76GiB**. I cannot 'see' any of the partitions on my sda HD. So I am not in a position to re-format any partition via Gparted other than the whole of sda.  However, as per previous post I can 'see' the partitions via **System/Admin/Disk Utility** but I have no experience of re-formating via this environment and what options to choose.  The output of your sudo blkid command is the same in both my normal or LiveCD environments - it is:

[B]/dev/loop0: TYPE="squashfs"
/dev/loop1: UUID="a4114abd-0fce-41a4-aac5-2556882e3b65" TYPE="ext3"
/dev/sda1: LABEL="win7" UUID="889C0845C941877C" TYPE="ntfs"
/dev/sda2: UUID="e83b6963-d3c3-4c91-b8a5-5c7ac989b5f3" TYPE="ext4"
/dev/sda3: LABEL="store" UUID="09D6A06006C8DACD" TYPE="ntfs"
/dev/sdb5: LABEL="backup" UUID="53E871870E731F3D" TYPE="ntfs"
/dev/sdg1: UUID="0F66-0BCE" TYPE="vfat"[/B]

---

### Post by Quarkrad on 2011-09-26
Attached picture of my sda shown in **System/Admin/Disk Utility**.  Win7 is sda1, 105 GB ext4 is sda2 (this is my Ubuntu 10.10 partition), store 282 GB NTFS is sda3.  The odd thing to me is the Free 8.4GB unallocated space at the end - when I built this machine this was configure via Gparted as my swap space.

---

### Post by westie457 on 2011-09-26
> **Quarkrad said:**
> Yes - I do get asked for my password when I launch Gparted.  This is the output from terminal:

dad@dadubuntu:~$ sudo fdisk -l
[sudo] password for dad: 
[COLOR="Red"]Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)[/COLOR]

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfa0c1e50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12749   102398976    7  HPFS/NTFS
/dev/sda2           12749       25497   102400000   83  Linux
/dev/sda3           25497       59782   275393536    7  HPFS/NTFS
/dev/sda4           59782       60802     8192000   85  Linux extended

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x638c197f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976760832    5  Extended
/dev/sdb5               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b34ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1      121602   976760832    5  Extended
/dev/sdg5               1      121602   976759808    7  HPFS/NTFS

Hi Quarkrad, See the bit highlighted in red. I think that is the problem.
My suggestion is to use testdisk to recover the partition information.
```
sudo apt-get install testdisk
``` if it not already installed, then```
sudo testdisk
``` to run.```
man testdisk
``` to get information on how testdisk works.

It has a good track record at recovering information about partitions and should work for you.

Hope this helps.

---

### Post by Grenage on 2011-09-26
gparted seeing the whole drive as unallocated is a bit worrying; rewriting it should fix it.  If you are comfortable with the terminal, you could consider using fdisk.  What I would suggest (from fdisk) is:

```
sudo fdisk /dev/sda
```

Listing the current partition table. (press p)
Make sure that all of your main partitions are listed.
Delete the last (your 'swap') partition, if it shows up. (press d)
If it does not show up, create a new partition.  (press n)
After using the defaults where you can, change the type to swap. (press t).
List the new partition structure to make sure you're happy with it.  (press p)
Save and exit. (press w)

---

### Post by Quarkrad on 2011-09-27
I need a bit of help here as I am a newbie to Linux.  I am not concerned about recovering data from any partition - my machine is fully backed up and is functioning 100%.  I could rebuild if necessary but I would like to avoid if pos.  Here is the output of the fdisk command:

[B]dad@dadubuntu:~$ sudo fdisk /dev/sda
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): v
Remaining 16388142 unallocated 512-byte sectors

Command (m for help): [/B]


I'm interested in the statement ....**of partition table 5 will be corrected by w(rite)**  is there a way I can action this w(rite) - and is the culprit my 8 GB unallocated partition?

---

### Post by Grenage on 2011-09-27
Howdy.

If you look at my previous post, those are the steps I would take; If you want a quick and simple attempt, simply press *w* while in fdisk.  It will write the partition table again.

---

### Post by Quarkrad on 2011-09-27
Many thanks - hitting w did the trick.  Re-writing the table solved the issue.  Gparted now 'sees' sda.  All I had to do was reformat the 8GB partition as swap.

---

### Post by Grenage on 2011-09-27
Outstanding; glad to hear that you got in sorted.

---

