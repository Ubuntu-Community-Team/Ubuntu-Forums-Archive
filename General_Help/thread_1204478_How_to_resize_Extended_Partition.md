---
title: "How to resize Extended Partition"
date: 2009-07-04
forum: General Help
---

### Post by simple_boy on 2009-07-04
I currently have a 250 GB harddrive running WinXP and Ubuntu 9.04 which has 2 partitions. The first one, a NTFS windows partition of 120 GB and the second one a 112 GB partition with Ubuntu installed.

I need to resize my Ubuntu (ext3) partition since I need more space. I managed to downsize my Window partition to 45 GB. I now have 75 of unallocated space which is clearly visible in GParted.

Here is my actual disk information (fdisk) :

```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1dea1de9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5875    47190906    7  HPFS/NTFS
/dev/sda2           15666       30400   118358887+   f  W95 Ext'd (LBA)
/dev/sda5           15666       30269   117306598+  83  Linux
/dev/sda6           30270       30400     1052226   82  Linux swap / Solaris

```

I now need to resize my ext3 Ubuntu partition. From what I understand and read, I need to resize the extended partition first.

Does anyone know how to proceed ?

Thanx in advance.

---

### Post by michy99 on 2009-07-04
Either boot from a Gparted Live CD or boot from an Ubuntu Live CD and go to System->Administration->Partition Editor.

Choose the extended partition.

Resize.

Resize logical partition(s) inside extended partition.

---

### Post by simple_boy on 2009-07-04
I just tried with the Ubuntu Boot CD, I ran GParted as specified but the option to resize the Extended partition is not active. 

I have the option to resize the ext3 partition but I can only downsize it not gain more space since I do not have any space preceding or following.

---

### Post by michy99 on 2009-07-04
Can you post a screenshot from gparted?

---

### Post by simple_boy on 2009-07-04
As requested. png attached file of a screenshot of GParted

---

### Post by michy99 on 2009-07-04
You need to unmount your partitions before you can resize them.

---

### Post by theozzlives on 2009-07-04
> **simple_boy said:**
> As requested. png attached file of a screenshot of GParted

This should work:

1. move your swap and ext3 down so that unallocated space is on top of the ext3.
2. delete or resize (if you resize, skip step 3) the extended.
3. create a new extended using all the unallocated space.
4. resize your ext3 (this will take awhile).

---

### Post by simple_boy on 2009-07-05
Thank you Michy99 and theozzlives. It worked.

I booted with the Ubuntu CD, started the partition editor. Although I didn't have the resize option on the Extended partition, selecting the "swapoff" option when right cliking on the linux-swap gave me the option to resize the Extended partition.

Thank you for your help. My partition is now 75 GB larger.

---

