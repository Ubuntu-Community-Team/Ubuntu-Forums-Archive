---
title: "Disk doesn't contain a valid partition table"
date: 2010-03-05
forum: General Help
---

### Post by 8301 on 2010-03-05
I got a big problem.
I formatted 4 harddrives from NTFS to ext4 with gparted and in terminal 
```
sudo mkfs -t ext4 /dev/sdb
``` 
all went smoothly.

Today after finally get my htpc done. After a reboot

fstab cannot mount  any of my drives

In /etc/fstab it's an error after my system partition

And the output of 

```
fdisk -l
```

Is

```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```  

After a fruitless attempt to fix the mounting problem am I forced to reinstall the system with Ubuntu live cd 64-bit. But when it's trying to format the partition where the old system were It cannot delete the old system files and closes down. 
WTF!!! This WAS not what I had in mind on a Friday night cmon give me a break.
In a last desperate measure Iam throwing in the alternative installer 32-bit and begin to install AND IT WORKS YEY.

But I have the same problem left

```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```  

I can mount the drives and play the content so the files isn't damaged.

So how can I fix this without losing data.

---

### Post by lavinog on 2010-03-05
can you post your fstab and the command you used to mount the drives

---

### Post by Intrepid Ibex on 2010-03-05
In simple words: if you can't mount it, your probably only hope is an app called testdisk. It's amazing tool for recovering partitions and disks.

Also I just had to do this :): [http://tinyurl.com/yfmzvbr](http://tinyurl.com/yfmzvbr)

---

### Post by lavinog on 2010-03-05
> **Intrepid Ibex said:**
> In simple words: if you can't mount it, your probably only hope is an app called testdisk. It's amazing tool for recovering partitions and disks.

[quote=8301]
I can mount the drives and play the content so the files isn't damaged.
[/quote]



> 
Also I just had to do this :): [http://tinyurl.com/yfmzvbr](http://tinyurl.com/yfmzvbr)
I don't think google is going to be much help in this situation...It is only going to confuse matters.

I suspect that the fstab is not correct.

---

### Post by 8301 on 2010-03-05
here is my fstab after reinstall

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=202713a7-dc8b-4179-ac4d-f6ed185c82c3 /               ext4    errors=remount-ro 0       1
/dev/sda5       /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=f81d6a58-5c67-4c55-b27a-34a110e762e7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

My mounting procedure is

```

htpc@ubuntu:~$ sudo mkdir /media/htpc2
[sudo] password for htpc: 
htpc@ubuntu:~$ sudo mount /dev/sdb /media/htpc2
htpc@ubuntu:~$ sudo fdisk -l

```

And my fdisk -l looks like this

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001a7bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         124      995998+  82  Linux swap / Solaris
/dev/sda2   *         125        1948    14651280   83  Linux
/dev/sda3            1949       60801   472736722+   5  Extended
/dev/sda5            1949       60801   472736691   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sde doesn't contain a valid partition table

```

To get them to automount I wrote in fstab before the crash

```

/dev/sdb /media/htpc2 auto defaults 0 0
```

One more thing that came to mind was that I had to choose between too kernels before booting up linux (never happend before) I think the last too numbers differs 36 and 14 but I cant remember.

The funny thing is that this time I didn't experimenting with linux I just want a stable OS for my htpc and this happens :P

Hope I get an answer while Im sleeping the is past 2 at night and Im really tried to ser Ubuntu right now so god night.

---

### Post by Bachstelze on 2010-03-05
You don't really have a problem. The message indicating that your drives don't contain a partition table is correct, but you don't absolutely need one. As you said, you can mount the filesystems on your drives just fine, so you can use them without a partition table.

---

### Post by darolu on 2010-03-05
> htpc@ubuntu:~$ sudo mount /dev/**sdb** /media/htpc2
*[COLOR="Silver"]^That won't work, even with a valid partitions table, you must specify a partition, not the actual hard drive. You must create a partition table in order to use your hard drives, it won't mount without it and mkfs won't do anything without it either.[/COLOR]*

It's seems like Gparted is not doing anything, are you sure you're applying the changes? (the green check mark on top). You can try with Parted, that way you'll have more control and can track what it's doing. To use it you need to open a terminal and run:
```
$ sudo parted <device>
```
You'll run parted and choose different options including a help one that will guide you through, you can also run everything in a single line though, this link has all the documentation you need:
[http://www.gnu.org/software/parted/manual/html_node/Using-Parted.html#Using-Parted](http://www.gnu.org/software/parted/manual/html_node/Using-Parted.html#Using-Parted)

Try with one disk, and then run "fdisk -l" again, to see if it worked; btw you can also use "fdisk <device>" to create partitions.

---

### Post by Bachstelze on 2010-03-05
> **darolu said:**
> ^That won't work, even with a valid partitions table, you must specify a partition, not the actual hard drive. You must create a partition table in order to use your hard drives, it won't mount without it and mkfs won't do anything without it either.

You are wrong.

---

### Post by darolu on 2010-03-05
> **Bachstelze said:**
> You are wrong.
Yes I am, I just run some tests and yes, it is possible to create a file system without partitions table, all docs I have read never mentioned this, so I made wrong conclusions. My apologies.
In my tests I couldn't paste files via Nautilus though, everything else worked fine.

---

### Post by lavinog on 2010-03-06
> **darolu said:**
> Yes I am, I just run some tests and yes, it is possible to create a file system without partitions table, all docs I have read never mentioned this, so I made wrong conclusions. My apologies.
In my tests I couldn't paste files via Nautilus though, everything else worked fine.

I would have made the same assumption...interesting stuff.
I guess it kind of makes sense since they are both device blocks.

Should the issue with Nautilus be considered a bug then, or should this type of configuration be considered invalid?

@OP:  To fix this, you may want to mount the filesystem, backup everything to another drive, and create a partition on the drive, then move your data back.
You should be able to do everything in gparted.
Don't use this command next time:
```

sudo mkfs -t ext4 /dev/sdb

```

here is some information on partitioning:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by 8301 on 2010-03-06
> **lavinog said:**
> I would have made the same assumption...interesting stuff.
I guess it kind of makes sense since they are both device blocks.

Should the issue with Nautilus be considered a bug then, or should this type of configuration be considered invalid?

@OP:  To fix this, you may want to mount the filesystem, backup everything to another drive, and create a partition on the drive, then move your data back.
You should be able to do everything in gparted.
Don't use this command next time:
```

sudo mkfs -t ext4 /dev/sdb

```

here is some information on partitioning:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

I did use gparted but when I tried to mount the drive in the terminal a message said that I needed to apply a file system and the only solution I found were 

```

sudo mkfs -t ext4 /dev/sdb

```

---

### Post by 8301 on 2010-03-07
I think I found the cause of the problem.

When I mounted the partitions I only mounted the disk

```
sudo mount /dev/sda /media/HTPC
```

It should have been 

```
sudo mount /dev/sda1 /media/HTPC
```

Gparted created sda1 on sda. And thats why the terminal asked me if I wanted a filesystem on sda.

---

