---
title: "Partitions problem"
date: 2011-12-09
forum: General Help
---

### Post by nickos on 2011-12-09
hey.


i have installed ubuntu 10.04 lts .I have two 500 GB and 750 GB HDD. (1250 total)
However i added ubuntu to a 20gb partition.How can i make ubuntu use 500 or 1250 gb?

---

### Post by BC59 on 2011-12-09
Could you please open a terminal with CTRL+ALT+T and run these commands?

```
sudo parted /dev/sda print
```

and

```
sudo fdisk -l
```

Then post the result to the forum.

---

### Post by nickos on 2011-12-09
> **BC59 said:**
> 
```
sudo parted /dev/sda print
``` 

Model: ATA ST3750528AS (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  50.0GB  50.0GB  primary   ext4            boot
 2      50.0GB  80.0GB  30.0GB  extended
 5      50.0GB  80.0GB  30.0GB  logical   linux-swap(v1)

> 
```
sudo fdisk -l
```Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001a41f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48827392   83  Linux
/dev/sda2            6079        9727    29295617    5  Extended
/dev/sda5            6079        9727    29295616   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc262c262

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488385536   83  Linux

---

### Post by BC59 on 2011-12-09
Let's see now.
You have installed Ubuntu on sda1 using 50GB.
Then you are using a swap of 30GB.

What partitions includes a recommended Linux/Ubuntu installation.

1. You need a ~/ partition like the sda1 you have, where is installed the boot system. The size could be something between 8-10GB.
2. Close to this you need a swap partition which Linux is using as supplementary to RAM. The size recommended is 2GB. Others say that is better to use RAM=swap means to add a swap partition the same size as your RAM.
3. A separate ~/home partition which is the storage place of your computer. you have to dedicate the rest of the space for your home directory/partition. In this partition are positioned the Documents, Music, Downloads, Videos, Pictures, Desktop of your system.

Finally I suggest you:
10GB for your system ( / )
2-4GB for your swap
and all the rest for ~/home.

Now after installing your system is a little late to make changes. So the suggestion is to boot from a Live CD (you installed ubuntu) and open the application Gparted. From there very carefuller delete the swap file and the extended partition you created. Then resize/expand the sd1 you have to cover almost all the space and leave only 4GB fro swap. Apply and that's it.

---

### Post by oldfred on 2011-12-09
I agree with BC59 suggestions, but in your case I might make / (root) a bit larger. I normally suggest 10-20GB and use for myself 25GB as I have lots of room. Minimal required space is 4.4GB.

If writing a DVD, you may need the 4GB in /tmp for a while and I used to keep forgetting to mount my /backup partition when running my backups  (since changed script to avoid that) and wondering why my / all of a sudden has used so much space. While you can get by with less space and some have to, having some extra often avoids problems. My typical install with lots of programs uses about 6 or 7GB in /.

---

### Post by BC59 on 2011-12-09
> **oldfred said:**
> If writing a DVD, you may need the 4GB in /tmp for a while 

I continue the misery of saving some GBs and I didn't think of such a detail. Thanks oldfred.

---

### Post by grahammechanical on 2011-12-09
To use the other drive, the 500Gb one you open the file manager and you will see the 500GB drive in the left panel under the heading of Devices. Just click on the 500GB drive icon once. This will mount the drive and all your programs be able to access and store files on the drive as you wish. You will have to do this every time you boot.

There is a way to edit a certain file so that this drive is mounted automatically every time you boot. Perhaps someone would explain how to do that as I do not know.

Regards.

---

