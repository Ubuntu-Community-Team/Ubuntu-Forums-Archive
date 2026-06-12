---
title: "usb partition backup help"
date: 2011-08-13
forum: General Help
---

### Post by joncorp on 2011-08-13
hi i have a question, i have an usb flashdrive with 2 partitions on it (1 is ext2 and the other one is FAT32) and i was wondering how could make a backup file of those 2 partitions at the same time, (i want the back up to be an ISO file because if i screw up the usb with my experiments i just will use disk utility and say that the iso file is the restore image and vuala). Does anyone know how to make this tipe of back up??? thanks and sorry for my bad grammar.

---

### Post by lmarmisa on 2011-08-14
I recommend this method for making a backup of your flashdrive. The method is reliable but the result is not an ISO file.

Open a terminal and type the command:

```

sudo fdisk -l

```You have to identify the device assigned to your flash drive. I will suppose that this is **/dev/sdc** (change 'c' to 'b', 'd' or other letter if necessary).

You have to umount the two partitions of your flashdrive now. Type this other command:

```

mount

```You will see the two partitions if they are mounted. These two command will umount them:

```

umount /dev/sdc1
umount /dev/sdc2

```Finally this command will make the backup of your flashdrive:

```

sudo dd if=/dev/sdc conv=noerror,sync | gzip > flashdrive.dd.gz

```The file containing the backup is named **flashdrive.dd.gz**. Use another name if you want.

This is the restore procedure. 

Insert a flashdrive of the same size or bigger than the original flashdrive. I will suppose that its associated device is **/dev/sdc** (use command sudo fdisk -l).

Unmount the partition(s) of the flashdrive if they are mounted (use the command umount if necessary).

Finally type this command:

```

gzip -d < flashdrive.dd.gz | sudo dd of=/dev/sdc conv=noerror,sync

```

---

