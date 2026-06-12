---
title: "how would someone conbin 3 drives?"
date: 2010-08-27
forum: General Help
---

### Post by KEE on 2010-08-27
Hi,
I want to know how would I combine the 3 drives under extended. Im have issues having no drive space. so I removed some old installations and re format them but I dont know how to combine them so that their under one /home
please help [IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-1-4.png[/IMG]

---

### Post by KEE on 2010-08-29
is this possible?

---

### Post by lmarmisa on 2010-08-29
Of course, this is possible.

You do not provide detailed information but basically you need to do three things:

[LIST=1]
[*]Automount the 2 new hard drives adding 2 lines to the file /etc/fstab
[*]Create the new directories with the correct owner and privileges and move the files you want to the new folders of the new hard drives.
[*]Define at least two symbolic links (**ln -s**) in your $HOME directory pointing to the new directories in the new hard drives.
[/LIST]
The complete process is not too dificult, but maybe you could provide more details of your system if you wish more detailed help.

Best regards,

Luis

---

### Post by KEE on 2010-08-29
> **lmarmisa said:**
> Of course, this is possible.

You do not provide detailed information but basically you need to do three things:

[LIST=1]
[*]Automount the 2 new hard drives adding 2 lines to the file /etc/fstab
[*]Create the new directories with the correct owner and privileges and move the files you want to the new folders of the new hard drives.
[*]Define at least two symbolic links (**ln -s**) in your $HOME directory pointing to the new directories in the new hard drives.
[/LIST]
The complete process is not too dificult, but maybe you could provide more details of your system if you wish more detailed help.

Best regards,

Luis
oh its 10.04 lucid lynx.what do i put in fstab? ```
# /dev/sda7
UUID=654fdfda-3147-4d09-a9f8-211286fe0b54 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=808079bc-17b0-4d69-a41d-d2169b03b0af none            swap    sw              0       0
``````
drwx------ 15 ops   ops   4096 2010-08-28 22:33 File System
drwx------  3 ops   ops   4096 2010-08-29 13:48 File System_
```

---

### Post by lmarmisa on 2010-08-29
Please, open a terminal, type these commands and copy the outputs in this thread:

```

sudo fdisk -l
df -h

```

---

### Post by KEE on 2010-08-31
> **lmarmisa said:**
> Please, open a terminal, type these commands and copy the outputs in this thread:

```

sudo fdisk -l
df -h

```
ok ```
 sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd84dcfc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19112   153516116    7  HPFS/NTFS
/dev/sda2           19113       38913   159051532+   5  Extended
/dev/sda5           38638       38913     2216938+  82  Linux swap / Solaris
/dev/sda6           19113       31770   101675322   83  Linux
/dev/sda7           32313       38637    50805531   83  Linux
/dev/sda8           31771       32312     4353583+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2028 MB, 2028994560 bytes
55 heads, 54 sectors/track, 1334 cylinders
Units = cylinders of 2970 * 512 = 1520640 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1335     1981314+   6  FAT16
```
```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              96G   52G   40G  57% /
none                  1.8G  332K  1.8G   1% /dev
none                  1.8G   52K  1.8G   1% /dev/shm
none                  1.8G  204K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  1.8G     0  1.8G   0% /lib/init/rw
/dev/sdb1             1.9G   44M  1.9G   3% /media/FC30-3DA9

```

---

### Post by lmarmisa on 2010-08-31
> **KEE said:**
> ok ```
 sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd84dcfc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19112   153516116    7  HPFS/NTFS
/dev/sda2           19113       38913   159051532+   5  Extended
/dev/sda5           38638       38913     2216938+  82  Linux swap / Solaris
/dev/sda6           19113       31770   101675322   83  Linux
/dev/sda7           32313       38637    50805531   83  Linux
/dev/sda8           31771       32312     4353583+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 2028 MB, 2028994560 bytes
55 heads, 54 sectors/track, 1334 cylinders
Units = cylinders of 2970 * 512 = 1520640 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1335     1981314+   6  FAT16
``````
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              96G   52G   40G  57% /
none                  1.8G  332K  1.8G   1% /dev
none                  1.8G   52K  1.8G   1% /dev/shm
none                  1.8G  204K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  1.8G     0  1.8G   0% /lib/init/rw
/dev/sdb1             1.9G   44M  1.9G   3% /media/FC30-3DA9

```

I suppose you have deleted another Linux installation located on partitions /dev/sda7 (root partition of the deleted Linux) and /dev/sda8 (swap). Is it true?.

I recommend a different solution to solve your problem. This solution is to delete the partitions /dev/sda7 and /dev/sda8 and then extend your Ubuntu partition /dev/sda6 with all the space released.

This is the procedure to follow: boot your system from an Ubuntu Live CD. Then, open the partition editor GParted (System -> Administration -> GParted).

GParted is a very powerfull tool for create, modify (resize) or delete partitions of the hard drives:


[LIST=1]
[*]Delete the /dev/sda8 partition.
[*]Delete the /dev/sda7 partition.
[*]Extend the /dev/sda6 partition until the right border.
[/LIST]

GParted is a very reliable tool, but I recommend a backup before you make any changes on your partitions.

If you have an external USB hard drive, try to make a backup of the /dev/sda6 partition using [Clonezilla]("http://www.clonezilla.org/"). The risk for modifying the partitions with GParted is very low, but I recommend the backup.

Please, check that all your Linux information is located in /dev/sda6 and the other two partitions /dev/sda7 and /dev/sda8 have no data (they will be erased, so verify that you have no data stored there).

When you finish the procedure, your Linux partition will be 55 Gbytes bigger with a total size of 157 Gbytes. Your problems about space will be over.

If you have any doubt about the procedure, please write a message. Do not start the procedure until you are 100% sure!!!.

Best regards,

Luis

---

### Post by KEE on 2010-08-31
> **lmarmisa said:**
> I suppose you have deleted another Linux installation located on partitions /dev/sda7 (root partition of the deleted Linux) and /dev/sda8 (swap). Is it true?.

I recommend a different solution to solve your problem. This solution is to delete the partitions /dev/sda7 and /dev/sda8 and then extend your Ubuntu partition /dev/sda6 with all the space released.

This is the procedure to follow: boot your system from an Ubuntu Live CD. Then, open the partition editor GParted (System -> Administration -> GParted).

GParted is a very powerfull tool for create, modify (resize) or delete partitions of the hard drives:


[LIST=1] 
[*]Delete the /dev/sda8 partition.
[*]Delete the /dev/sda7 partition.
[*]Extend the /dev/sda6 partition until the right border.
[/LIST]

GParted is a very reliable tool, but I recommend a backup before you make any changes on your partitions.

If you have an external USB hard drive, try to make a backup of the /dev/sda6 partition using [Clonezilla]("http://www.clonezilla.org/"). The risk for modifying the partitions with GParted is very low, but I recommend the backup.

Please, check that all your Linux information is located in /dev/sda6 and the other two partitions /dev/sda7 and /dev/sda8 have no data (they will be erased, so verify that you have no data stored there).

When you finish the procedure, your Linux partition will be 55 Gbytes bigger with a total size of 157 Gbytes. Your problems about space will be over.

If you have any doubt about the procedure, please write a message. Do not start the procedure until you are 100% sure!!!.

Best regards,

Luis

not sure if it worked =( is there another step? like /mbr to reset the grub? [IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-7.png[/IMG]```
 sudo fdisk -l


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd84dcfc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19112   153516116    7  HPFS/NTFS
/dev/sda2           19113       38913   159051532+   5  Extended
/dev/sda5           38638       38913     2216938+  82  Linux swap / Solaris
/dev/sda6           19113       38637   156834499+  83  Linux

Partition table entries are not in disk order

``` ```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              96G   69G   23G  76% /
none                  1.8G  300K  1.8G   1% /dev
none                  1.8G   96K  1.8G   1% /dev/shm
none                  1.8G  208K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  1.8G     0  1.8G   0% /lib/init/rw
/dev/sda1             147G  119G   28G  81% /media/VistaOS

```

---

### Post by deserthowler on 2010-08-31
you could just reformat the drives to ext2 or ext3 and add the diskmounter app to your panel.  Then you can just click on the partition you wish to mount.  Mount it and it will appear on your desktop.

Earl

---

### Post by lmarmisa on 2010-09-01
> **KEE said:**
> not sure if it worked =( is there another step? like /mbr to reset the grub? ```
 sudo fdisk -l


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd84dcfc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19112   153516116    7  HPFS/NTFS
/dev/sda2           19113       38913   159051532+   5  Extended
/dev/sda5           38638       38913     2216938+  82  Linux swap / Solaris
/dev/sda6           19113       38637   156834499+  83  Linux

Partition table entries are not in disk order

``` ```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              96G   69G   23G  76% /
none                  1.8G  300K  1.8G   1% /dev
none                  1.8G   96K  1.8G   1% /dev/shm
none                  1.8G  208K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  1.8G     0  1.8G   0% /lib/init/rw
/dev/sda1             147G  119G   28G  81% /media/VistaOS

```

You do not need any more commands. That is all.

The sudo fdisk -l command looks good: the size of /dev/sda6 is near 157 Gbytes.

But the command df -h shows us a different size for /dev/sda6 (96 Gbytes).

This is strange.

Reboot your system and repeat the two commands (sudo fdisk -l and df -h), please.

---

### Post by lmarmisa on 2010-09-01
Maybe the reason of the incongruence is this comment of the fdisk command:

> 
Partition table entries are not in disk order
I would like if you could open GParted and take a snapshot of your screen.

It should be similar to my attachment (sizes are different there and I have used /dev/sdb unit in muy example, but the image should be similar).

---

### Post by KEE on 2010-09-01
> **lmarmisa said:**
> Maybe the reason of the incongruence is this comment of the fdisk command:

I would like if you could open GParted and take a snapshot of your screen.

It should be similar to my attachment (sizes are different there and I have used /dev/sdb unit in muy example, but the image should be similar).

ok here it is [IMG]http://i222.photobucket.com/albums/dd124/assripp3r/Screenshot-8.png[/IMG]

---

### Post by lmarmisa on 2010-09-01
This seems good.

Could you repeat the two commands?.

---

### Post by KEE on 2010-09-01
> **lmarmisa said:**
> This seems good.

Could you repeat the two commands?.yes of course ```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd84dcfc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19112   153516116    7  HPFS/NTFS
/dev/sda2           19113       38913   159051532+   5  Extended
/dev/sda5           38638       38913     2216938+  82  Linux swap / Solaris
/dev/sda6           19113       38637   156834499+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 65 MB, 65404928 bytes
16 heads, 32 sectors/track, 249 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x1256ea36

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         249       63728    6  FAT16
ubuntu@ubuntu:~$ 
```
```
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.8G  2.0M  1.8G   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 1.8G  2.0M  1.8G   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G   88K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  2.8M  1.8G   1% /dev
tmpfs                 1.8G  104K  1.8G   1% /dev/shm
rootfs                1.8G   85M  1.7G   5% /
/dev/scd0             699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 1.8G   12K  1.8G   1% /tmp
/dev/sdb1              63M   16M   47M  25% /media/disk
ubuntu@ubuntu:~$ 
```

---

### Post by lmarmisa on 2010-09-01
> **KEE said:**
> yes of course ```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd84dcfc1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19112   153516116    7  HPFS/NTFS
/dev/sda2           19113       38913   159051532+   5  Extended
/dev/sda5           38638       38913     2216938+  82  Linux swap / Solaris
/dev/sda6           19113       38637   156834499+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 65 MB, 65404928 bytes
16 heads, 32 sectors/track, 249 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x1256ea36

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         249       63728    6  FAT16
ubuntu@ubuntu:~$ 
``````
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.8G  2.0M  1.8G   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 1.8G  2.0M  1.8G   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 1.8G     0  1.8G   0% /lib/init/rw
varrun                1.8G   88K  1.8G   1% /var/run
varlock               1.8G     0  1.8G   0% /var/lock
udev                  1.8G  2.8M  1.8G   1% /dev
tmpfs                 1.8G  104K  1.8G   1% /dev/shm
rootfs                1.8G   85M  1.7G   5% /
/dev/scd0             699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 1.8G   12K  1.8G   1% /tmp
/dev/sdb1              63M   16M   47M  25% /media/disk
ubuntu@ubuntu:~$ 
```

Are you able to boot normally?. This seems a boot from a Live CD.

---

### Post by srs5694 on 2010-09-01
> **lmarmisa said:**
> The sudo fdisk -l command looks good: the size of /dev/sda6 is near 157 Gbytes.

But the command df -h shows us a different size for /dev/sda6 (96 Gbytes).

This is strange.

This means that the partition has been resized, but not the filesystem it contains. You can resize the filesystem, and therefore fix the problem, by typing "sudo resize2fs /dev/sda6" at a shell prompt.

[quote=Imarmisa]Maybe the reason of the incongruence is this comment of the fdisk command:> Partition table entries are not in disk order[/quote]

No; this is harmless. It just means that the order of the partitions themselves doesn't match the order of the partition entries in the partition table. This is perfectly legal, but it can be confusing to mere human brains. In the case of the specified system, /dev/sda6 is earlier than /dev/sda5 on the disk.

---

### Post by lmarmisa on 2010-09-01
> **srs5694 said:**
> This means that the partition has been resized, but not the filesystem it contains. You can resize the filesystem, and therefore fix the problem, by typing "sudo resize2fs /dev/sda6" at a shell prompt.



No; this is harmless. It just means that the order of the partitions themselves doesn't match the order of the partition entries in the partition table. This is perfectly legal, but it can be confusing to mere human brains. In the case of the specified system, /dev/sda6 is earlier than /dev/sda5 on the disk.

Thanks for your comments. First time I see this problem after a GParted resize operation.

---

### Post by KEE on 2010-09-01
thanks all , that worked =D

---

