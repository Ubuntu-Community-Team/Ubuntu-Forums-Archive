---
title: "setting up a second harddrive - what did I do wrong?"
date: 2009-10-14
forum: General Help
---

### Post by sab0tage on 2009-10-14
```
$ sudo mkdir /Storage
$ sudo chmod -R 777 /Storage

$ sudo mkfs.ext3 /dev/sdb
$ mount /dev/sdb /Storage
```

```
pw@rk:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb74510e2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4775    38355156   83  Linux
/dev/sda2            4776        4865      722925    5  Extended
/dev/sda5            4776        4865      722893+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
```
pw@rk:~$ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="dc619db9-1de4-4b1b-b555-909ca15a8339" TYPE="ext3" 
/dev/sda5: UUID="57f01442-de08-44c1-8af0-018943fbdc43" TYPE="swap"

I was trying to locate the UUID of /dev/sdb and noticed blkid didn't show it. Then fdisk showed the error, though it mounts fine.

Thanks!

---

### Post by jerome1232 on 2009-10-14
You never created a partition on the disk. You would use fdisk to create one.

```
sudo fdisk /dev/sdb
```

If I remember right it sort of prompts on the way, when your done you should have created the partition /dev/sdb1, which you can then put a filesystem on.

---

### Post by sab0tage on 2009-10-14
Hey thanks for the info!

I was following a guide I found with google:
[http://www.ghacks.net/2009/09/10/add-a-second-drive-to-your-ubuntu-server/](http://www.ghacks.net/2009/09/10/add-a-second-drive-to-your-ubuntu-server/)

It seems to have missed that step all together.

So, to recap, this was the entire process:

```
$ sudo mkdir /Storage
$ sudo chmod -R 777 /Storage

$ sudo fdisk /dev/sdb
$ sudo mkfs -t ext3 /dev/sdb1
$ mount /dev/sdb /Storage
$ sudo fdisk -l
$ sudo blkid
$ sudo nano /etc/fstab
UUID=ENTEREDUUIDHERE /Storage ext3 defaults 0 0
$ sudo mount -a
or reboot
$ sudo fdisk -l
```

Success! Thanks!!

---

### Post by jerome1232 on 2009-10-15
For your fstab, I would set the disk to get checked during startup (unless for some reason you specifically didn't want that)

```
UUID=ENTEREDUUIDHERE /Storage ext3 defaults 0 **2**
```

The 2 tells the system to check it after having checked the main system partitions.

---

### Post by sab0tage on 2009-10-15
Nice idea. Thanks again

---

