---
title: "can't see other partitions, i want to mount one of those"
date: 2011-11-20
forum: General Help
---

### Post by Mappenz on 2011-11-20
Hi,

my primary Ubuntu installation doesn't boot anymore. Now I want to access my data. On some website it says to mount the partition.

```

michael@michi11:~$ sudo mount /
/      /proc  

```

Thats what happens when I enter sudo mount and press tap twice using another Ubuntu installation from a different partition on the same drive. I can see the partitions with gparted.

---

### Post by hal8000 on 2011-11-20
Boot from your other Ubuntu install and post the output of:

sudo fdisk -l

(Which partitions did you install your broken Ubuntu into?)

---

### Post by Mappenz on 2011-11-20
```

michael@michi11:/mnt$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00014a8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   474605563   237301758   83  Linux
/dev/sda2       552732670   591802367    19534849    5  Extended
/dev/sda4       612911880   621088964     4088542+  82  Linux swap / Solaris
/dev/sda5       552732672   591802367    19534848   83  Linux
michael@michi11:/mnt$ 

```

sda1 is the broken one. sda5 is the second one.

---

### Post by Mappenz on 2011-11-20
I can mount the other partition with the graphical file manager. In the terminal the the i can't find it with mount or umount. But thats ok for now. I think i encrypted my home directory. How can access my data now?

---

### Post by hal8000 on 2011-11-20
> **Mappenz said:**
> ```

michael@michi11:/mnt$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00014a8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   474605563   237301758   83  Linux
/dev/sda2       552732670   591802367    19534849    5  Extended
/dev/sda4       612911880   621088964     4088542+  82  Linux swap / Solaris
/dev/sda5       552732672   591802367    19534848   83  Linux
michael@michi11:/mnt$ 

```

sda1 is the broken one. sda5 is the second one.


As there are only 4 partition then sda1 and sda5 must be complete / partitions with no separate /home partition.

From your alternate linux run an fsck on the faulty partition. What filesystem did you choose? ext3 or ext4 or something else?

The command will be

sudo fsck.ext4 /dev/sda1

To check , however you MUST use the correct filesystem, fsck.ext3 for ext3
systems.
Can you remembet what happened before your system became unbootable?

---

### Post by Mappenz on 2011-11-20
The command didn't work, and it didn't work when i replaced the dot with a space. I took a screenshot of my geparted. Don't be confused by the enumeration, I deleted sda 3. I didn't know you could have only 4 primary partitions and ran out of partitions.

---

### Post by hal8000 on 2011-11-20
Sorry I had a typo in my last post. OK it is sda1 and gparted shows filesystem as ext4 so use


sudo fsck.ext4 /dev/sda1


You can only have 4 primary partitions, create an extended partition to use more partitions. Be aware that Ubuntu uses scsi-emulation so you are limited to 16 partitions
in total (which is enough should you want to multiboot).

---

### Post by Mappenz on 2011-11-20
The directory is now mounted. I am warned that i will cause severe damage if I continue with the fsck command. Its not possible to unmount since the directory is in use. I am not sure who uses the directory but I think I know how I caused it to be used.

Trying to access my data I tried:
```

sudo mount -t ecryptfs <my home on the mountet partition>/ /home/michael/otherHome
```

didn't work properly, i have encrypted data in otherHome.

---

### Post by Mappenz on 2011-11-20
```
sudo umount -t ecryptfs <my home on the mountet partition>/ /home/michael/otherHome
``` did it. The partition is now unmounted.

```
michael@michi11:~$ sudo fsck.ext4 /dev/sda1e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1: clean, 364022/14835712 files, 3819408/59325439 blocks
```

---

### Post by fdrake on 2011-11-20
> **Mappenz said:**
> The directory is now mounted. I am warned that i will cause severe damage if I continue with the fsck command. Its not possible to unmount since the directory is in use. I am not sure who uses the directory but I think I know how I caused it to be used.

Trying to access my data I tried:
```

sudo mount -t ecryptfs <my home on the mountet partition>/ /home/michael/otherHome
```

didn't work properly, i have encrypted data in otherHome.
try
```

sudo umount /dev/sda1
sudo fsck /dev/sda1

```
if it still says the disk is used try to close all the windows and terminals that are working with /dev/sda1 or do
```

lsof /dev/sda1

```to see which program is using it

ps to mount it do:
```

sudo mkdir /media/myHDD
sudo mount /dev/sda1 /media/myHDD

```or even better add an entry to fstab

---

### Post by Mappenz on 2011-11-20
Thank you for your help. After mounting i accessed my data with.
```
sudo ecryptfs-recover-private
```
Thats good enough for now.

---

