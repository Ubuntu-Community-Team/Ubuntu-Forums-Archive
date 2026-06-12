---
title: "identify partitions with certain files"
date: 2009-12-30
forum: General Help
---

### Post by jamesr on 2009-12-30
I may asking the incorrect question, but I have not had success in answering question.

A fuller explanation would be
System with 2 internal hard drives , 
1st HD is mounted during boot up and has an entry in fstab
Similarly 2nd HD
3rd drive is an external USB disk

see attached fstab```
fdrold@fdrold-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=42619b80-c0ae-4fe1-b098-de615c91ea56 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d67dcdd1-1529-47a0-a8ac-e4f0f86e835f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   auto	rw,user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
fdrold@fdrold-desktop:~$ 

```


see attached fdisk
```
fdrold@fdrold-desktop:~$ sudo fdisk -l
[sudo] password for fdrold: 

Disk /dev/sda: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e0faa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1188     9542578+  83  Linux
/dev/sda2            1189        1247      473917+   5  Extended
/dev/sda5            1189        1247      473886   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00062b4b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2841    22820301    c  W95 FAT32 (LBA)
/dev/sdb2            2842        9729    55327860    f  W95 Ext'd (LBA)
/dev/sdb5            2842        5918    24715971    b  W95 FAT32
/dev/sdb6            5919        9729    30611826    b  W95 FAT32

Disk /dev/sdc: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009ff3b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1275    10241406   83  Linux
/dev/sdc2            1276        3649    19069155    5  Extended
/dev/sdc5            1276        1414     1116486   82  Linux swap / Solaris
/dev/sdc6            1415        2689    10241406   83  Linux
/dev/sdc7            2690        3649     7711168+  83  Linux
fdrold@fdrold-desktop:~$ 


```

I would like to correlate the partitions with the names in Ubuntu. These partitions are /media labels. The partitions as seen on the desktop are labeled as 
 DISK02PART1 ie the Windows label
JDR
25.3 GB media 

so I can reformat one to ext3 and then mount it as a new /home 

But, of course, I do not want to reformat the wrong partition. This may be a case of too much holiday spirit but I cannot find an answer.

---

### Post by Leppie on 2009-12-30
i may be missing something, but i don't understand the question.
what are you exactly trying to achieve? (first you say you want to use labels as mountpoints and then you say you want to mount as /home?)

---

### Post by Morbius1 on 2009-12-30
Yes, I'm a little lost myself.

Maybe if you post the output of **sudo blkid**, so we can see the labels and you can point out the problem.

---

### Post by oldfred on 2009-12-30
Are you looking at labels or mount points. I have some the same.

fred@fred-desktop:~$ ls -l /dev/disk/by-label/
total 0
lrwxrwxrwx 1 root root 10 2009-12-28 23:34 backup -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-12-28 23:34 Data -> ../../sdc6
lrwxrwxrwx 1 root root 10 2009-12-28 23:34 grub -> ../../sdc1
lrwxrwxrwx 1 root root 10 2009-12-28 23:34 newhome -> ../../sdc9

You can make a label in gparted or 
   2. Make a label
      e2label <dev> <label>
      tune2fs -L <label> <dev>

Here I set mount point in fstab as data, backup and shared:
# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2  
# Entry for /dev/sda2 :
UUID=13a684e4-2849-4566-9528-21cd07028a9a  /media/backup  ext3         auto,users,rw,relatime               0  2  
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

Instead of using UUIDs in fstab you can use the labels that you assign.

Understanding fstab from next link:
**IMO, LABEL is easiest to use as you can set a label and it is human readable.**
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by jamesr on 2009-12-30
That may be the problem that I am not asking the question correctly.

Ultimately I wish to reformat one of the partitions on the /dev/sdb drive but the correct partition. Once formatted, I will be changing it, to be my new /home partition. I have no problems in creating a new /home partition and transferring the old /home directory (using the excellent information posted by Asieyu) on current linux drive. I equally have no problems changing the mountpoints or fstab once it has been reformatted. Gparted only refers to the physical names. 

BUT I do not want to reformat the wrong partition. 

I suppose another way to say the same thing is where is the mountpoints information  stored for media devices that correlate to physical partitions ie /dev/sdb1.

Thinking further, I realise that a possible way, would be to add a known file ie known size and see the changes in used space in Gparted but I was hoping for a CLI approach

---

### Post by jamesisin on 2009-12-30
In order to reformat a partition, you have to unmount it.  Once you unmount the one you think is the correct one (to reformat), attempt to access the partition you do not want to reformat.  If you are able to access that partition, you know it is mounted.  Proceed with formating the unmounted partition.

---

### Post by Morbius1 on 2009-12-30
> I suppose another way to say the same thing is where is the mountpoints information stored for media devices that correlate to physical partitions ie /dev/sdb1.You have no entries in fstab for the other drives so they will appear in nautilus as unmounted drives.

They will mount to /media by default and by default they will use the LABEL information that you'd see if you opened a terminal and typed **sudo blkid**.

The reason you don't get a label on all of them is probably because blkid can't find a label because there is no label.

---

### Post by jamesr on 2009-12-30
To All to replied,

Thanks

But while logged I was thinking of other ways especially after to my long reply.

One way is to```
cat /etc/mtab
```

and another way which some of you have mentioned while I was logged off ie ```
sudo blkid
```. Most of my systems are based on on the older form of labels /dev/sd* not UUID's and fortunately I was reading an article about UUID's. I think that I will have to transfer ie learning cap on again.

Another that I had not thought about was after unmounting, check the file browser.

And yes the other suggestion
```
ls -l /dev/disk/by-label/
``` would have worked well, in fact I should have remembered, too much holiday spirit!!!

Yes I agree with you "oldfred"> IMO, LABEL is easiest to use as you can set a label and it is human readable. but Ubuntu on new installations always sets up UUID.

Thanks again

---

