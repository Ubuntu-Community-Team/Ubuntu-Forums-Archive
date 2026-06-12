---
title: "partitions not accessible"
date: 2006-06-28
forum: General Help
---

### Post by m.musashi on 2006-06-28
I have been trying for several weeks to figure out why my various partitions are not accessible. Although all partitions have an icon in nautilus, when I double click I get an error message that the partition can't be mounted (see screenshots). The more details button shows ```
error: device /dev/hdc1 is not removable

error: could not execute pmount
```
Any ideas on what the problem might be and how I fix it? If I connect an external drive it is mounted and accessible without any problem.

Oh, and fdisk gives this:
```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12498   100390153+   7  HPFS/NTFS
/dev/sda2           12499       23967    92124742+  83  Linux
/dev/sda3           23968       24321     2843505    5  Extended
/dev/sda5           23968       24321     2843473+  82  Linux swap / Solaris

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4943    39704616    c  W95 FAT32 (LBA)
/dev/hdc2   *        4944        9729    38443545    f  W95 Ext'd (LBA)
/dev/hdc5            4944        5125     1461883+  82  Linux swap / Solaris
/dev/hdc6            5126        6975    14860093+  83  Linux
/dev/hdc7            6976        9729    22121473+  83  Linux
```
Hope that helps.

Thanks in advance for any help.

---

### Post by woedend on 2006-06-28
I get that message in debian as well with my partitions.  Did you specify each one in /etc/fstab?  Thats the only way I could make them accessible

---

### Post by m.musashi on 2006-06-29
[QUOTE=woedend]I get that message in debian as well with my partitions.  Did you specify each one in /etc/fstab?  Thats the only way I could make them accessible[/QUOTE]
Thanks for the input, but I'm not sure I know how to do that. Could you provide some info? Althought, I thought this was now automated in Dapper and on the two other computers that have Dapper other partitions show up just fine - just not on my desktop. The fdisk command shows the partitions but I just can't access them.

---

### Post by woedend on 2006-06-29
its a bit tricky and even I dont know everything yet, and since im not using ubuntu its a bit harder.  but I do think adding it to fstab will fix this problem.

You need to decide what folder to mount to, in this case lets assume you wanted to do /media/hdc1
sudo mkdir /media/hdc1

then do
sudo gedit /etc/fstab

you will get a file that has mount points, and where to mount them.
try adding

/dev/hdc1      /media/hdc1     vfat     defaults     0      0 

somewhere in the file(assuming this doesnt already exist)
then save, then reboot.

---

