---
title: "grub erors that i can't solve"
date: 2010-03-09
forum: General Help
---

### Post by tali_le on 2010-03-09
i installed ubuntu a week ago

two days ago wanted to re-format my windows partition int Extd system using the command mkfs

i did some mistake cause after restarting i only got to the Grub rescue menu

how can i solve this? 
i tried using this eror section of the documentation

i wrote:
**grub-install /dev/sda**
in order to re-install grub
but got this line:
**grub-mkdevicemap: eror; cannot open /boot/grub/device.map**

i think i also have problems in my partitions now but i don't know how to check it

i really wsanna fix this without re formatting the all disk

any suggestions?

tali

---

### Post by Method X on 2010-03-09
Hello
First, try this method: [http://ubuntuforums.org/showpost.php?p=8932032&postcount=7]("http://ubuntuforums.org/showpost.php?p=8932032&postcount=7")

Replace sdb5 with yours sdbX, where X is your number.

---

### Post by tali_le on 2010-03-09
when u say my number ehwhat number are you talking about?

i have my disc devided into two partitions, one with extd and one with ntfs but the partition that has extd has in it a smaller partition of swap memory...

tali

---

### Post by tali_le on 2010-03-09
i tried writing:
**sudo mount /dev/sdb1 /mnt**

and got the reply:
**mount: secial device /dev/sdb1 does not exist**

when tried writing:
**sudo mount /dev/sda1 /mnt**

i got the reply:
**mount: you must specify the filesystem type**

---

### Post by tali_le on 2010-03-09
i tried to get more info

here is what i got for the fdisk

ubuntu@ubuntu:~$ sudo fdisk -l
Warning: ignoring extra data in partition table 5
Ignoring extra extended partition 2

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d5c8436

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    f  W95 Ext'd (LBA)
/dev/sda2            5100        9729    37190475    f  W95 Ext'd (LBA)
/dev/sda5   ?       13578      119522   850995205   72  Unknown


i'm also attaching a screenshot that has the terminal, gParted and the disk utility, all give different answers about the partitions

tali

---

### Post by MasterNetra on 2010-03-09
Tried removing the /mnt ? And do the sda1 version again?

---

### Post by tali_le on 2010-03-10
tried it...
got the answer:
**mount: can't find /dev/sda1 in /etc/fstab or etc/mtab**

---

