---
title: "ubuntu boot drive corrupted"
date: 2010-04-04
forum: General Help
---

### Post by krishna1650 on 2010-04-04
hello all, i am facing a big problem, my ubuntu boot drive has corrupted. i am using live cd to mount that drive, but it shows "bad super block" and other stuffs.
Can anyone tell, any way to recover files from that drive? or how can use fdisk or other tools to correct that file system?

thanks

---

### Post by koma77 on 2010-04-04
If you can mount it using the live CD then just copy the files over the network or to an external drive.

If not you will have to run fsck to try to at least make the disk mountable.

If that does not succeed you will have to dig up yor most recent backup, buy a new disk and reinstall.

---

### Post by ronnielsen1 on 2010-04-04
I used testdisk from Caine Rescue CD (If you run in gui - it's slow) Puppy Unleashed also has this file. It works great.

---

### Post by krishna1650 on 2010-04-04
> **koma77 said:**
> If you can mount it using the live CD then just copy the files over the network or to an external drive.

If not you will have to run fsck to try to at least make the disk mountable.

If that does not succeed you will have to dig up yor most recent backup, buy a new disk and reinstall.

I am not able to mount that drive. Can you please tell the options should be given to command fsck?
Thanks for the reply.

---

### Post by john newbuntu on 2010-04-04
Boot using the Ubuntu liveCD.  Determine the linux root partition using:
sudo fdisk -l

Then run:
sudo e2fsck -C0 -p -f -v /dev/sda5
(assuming /dev/sda5 to be your linux root partition).

Please report back all the errors.

---

### Post by krishna1650 on 2010-04-04
> **john newbuntu said:**
> Boot using the Ubuntu liveCD.  Determine the linux root partition using:
sudo fdisk -l

Then run:
sudo e2fsck -C0 -p -f -v /dev/sda5
(assuming /dev/sda5 to be your linux root partition).

Please report back all the errors.

Many thanks for your reply, i am able to get the files using testdisk. I am using "sudo testdisk /dev/sda3", as my corrupted drive is /dev/sda3. And one question about the command you have given, is it going to recover the drive or just will give the files?

Thanks again for your reply.

---

### Post by krishna1650 on 2010-04-04
> **ronnielsen1 said:**
> I used testdisk from Caine Rescue CD (If you run in gui - it's slow) Puppy Unleashed also has this file. It works great.

Thanks for the reply, you saved my projects. I am able to copy the files. Can you tell how to fully get it recovered?

Thanks for the quick reply.

---

### Post by john newbuntu on 2010-04-04
Well, assuming that it is an ext* filesystem, e2fsck would have checked it and reported any errors.  From your initial post, it appeared to be a bad superblock problem that could potentially have been corrected.  If so, you could have recovered the partition (sda3). Again no guarantees.

---

### Post by krishna1650 on 2010-04-04
> **john newbuntu said:**
> Well, assuming that it is an ext* filesystem, e2fsck would have checked it and reported any errors.  From your initial post, it appeared to be a bad superblock problem that could potentially have been corrected.  If so, you could have recovered the partition (sda3). Again no guarantees.

No i am not able to mount it, i am only able to copy the files using testdisk.

---

### Post by krishna1650 on 2010-04-04
> **john newbuntu said:**
> Boot using the Ubuntu liveCD.  Determine the linux root partition using:
sudo fdisk -l

Then run:
sudo e2fsck -C0 -p -f -v /dev/sda5
(assuming /dev/sda5 to be your linux root partition).

Please report back all the errors.
These are the error reports
1) sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44c144c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        1913    15257600    7  HPFS/NTFS
/dev/sda3            1913        3825    15360000   83  Linux
/dev/sda4            3826       19457   125564040    5  Extended
/dev/sda5            3826        7569    30073648+  83  Linux
/dev/sda6            7570       11316    30097746    7  HPFS/NTFS
/dev/sda7           11317       15401    32812731    7  HPFS/NTFS
/dev/sda8           15402       15650     2000061   82  Linux swap / Solaris
/dev/sda9           15651       19457    30579696    7  HPFS/NTFS


2) sudo e2fsck -C0 -p -f -v /dev/sda3
/dev/sda3: recovering journal
/dev/sda3: Clearing orphaned inode 838059 (uid=1000, gid=1000, mode=0100600, size=0)
/dev/sda3: Clearing orphaned inode 838045 (uid=1000, gid=1000, mode=0100600, size=0)
/dev/sda3: Clearing orphaned inode 838042 (uid=1000, gid=1000, mode=0100600, size=0)
/dev/sda3: Clearing orphaned inode 708653 (uid=0, gid=0, mode=040000, size=4096)
/dev/sda3: Clearing orphaned inode 708652 (uid=1000, gid=1000, mode=0100600, size=552)
/dev/sda3: Clearing orphaned inode 708609 (uid=1000, gid=1000, mode=0100600, size=3324)
/dev/sda3: Clearing orphaned inode 708650 (uid=1000, gid=1000, mode=0100600, size=64)
/dev/sda3: Clearing orphaned inode 708636 (uid=1000, gid=1000, mode=0100600, size=504)
/dev/sda3: Clearing orphaned inode 708635 (uid=1000, gid=1000, mode=0100600, size=2931)
/dev/sda3: Clearing orphaned inode 708604 (uid=1000, gid=1000, mode=0100600, size=256)
/dev/sda3: Clearing orphaned inode 708602 (uid=1000, gid=1000, mode=0100600, size=4096)
/dev/sda3: Clearing orphaned inode 708600 (uid=1000, gid=1000, mode=0100600, size=20766)
/dev/sda3: Clearing orphaned inode 263197 (uid=0, gid=0, mode=0100644, size=1831)
/dev/sda3: Clearing orphaned inode 708558 (uid=1000, gid=1000, mode=0140755, size=0)
/dev/sda3: Clearing orphaned inode 708540 (uid=114, gid=121, mode=0100600, size=0)
/dev/sda3: Clearing orphaned inode 708539 (uid=114, gid=121, mode=0100600, size=0)
/dev/sda3: Clearing orphaned inode 708538 (uid=114, gid=121, mode=0100600, size=0)
/dev/sda3: Clearing orphaned inode 708537 (uid=114, gid=121, mode=0100600, size=0)
/dev/sda3: Clearing orphaned inode 708536 (uid=114, gid=121, mode=0100600, size=0)
/dev/sda3:                                                                      Inode 386140, i_blocks is 712, should be 104.  FIXED.
/dev/sda3: Inode 386171, i_blocks is 10416, should be 10600.  FIXED.
/dev/sda3: Inode 386164, i_blocks is 9480, should be 9680.  FIXED.
/dev/sda3: Inode 386157, i_blocks is 11008, should be 11208.  FIXED.
/dev/sda3: Inode 386136 has illegal block(s).  

/dev/sda3: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)

---

### Post by john newbuntu on 2010-04-04
Now run:
sudo e2fsck -y -v /dev/sda3

---

### Post by krishna1650 on 2010-04-04
> **john newbuntu said:**
> Now run:
sudo e2fsck -y -v /dev/sda3

Thanks, i am able to mount it. You taught me a great lesson.
Thanks for your time and help.

---

### Post by chiwi on 2010-04-04
If I understood correctly, your filesystem has a bad superblock, I had the same problem last week, i could fix with these commands:

[http://klingonwarrior.com/cms/?p=75](http://klingonwarrior.com/cms/?p=75)

---

### Post by ronnielsen1 on 2010-04-04
Glad you got your files back. I recently had to use it to recover files off a hard drive I couldn't mount. Great little program. Wish I knew how to use all of the other programs on Caine or Puppy.
 I know I'm sure I've thrown hard drives away I could have fixed.

---

### Post by chiwi on 2010-04-04
right, BIG lesson i've learned is that you should NEVER fsck your disk while mounted.

Boot from a live CD and do it from there. That fixed all my problems.

---

