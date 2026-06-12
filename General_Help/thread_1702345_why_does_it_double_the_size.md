---
title: "why does it double the size?"
date: 2011-03-07
forum: General Help
---

### Post by timjay73 on 2011-03-07
so i recently had ubuntu installed on an 8GB partition and it decided to take up 16GB, then i got a warning saying i was out of space.

 [_here's my previous inquiry_]("http://ubuntuforums.org/showthread.php?p=10504429#post10504429")  

after no luck resizing partitions with gparted (i was getting errors) i gave up, deleted all the partitions, combined them into one partition, and reformatted the partition to ext4 (with gparted) with 30gb of space. i then reinstalled 10.10 64bit and when i boot into windows it shows that it now has 60GB. what?!? i dont understand how or why this happens. 

what can i do to keep ubuntu within the 30gb of space i give it and not take up anymore space?

any advice or direction on this would be greatly appreciated.

win7pro
ubuntu 10.1064bit

---

### Post by mikewhatever on 2011-03-07
Can you post the outputs of the following commands from a terminal window:
```
df -h
sudo fdisk -l
```

---

### Post by timjay73 on 2011-03-07
legalxchech@legalxchech:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              27G  2.9G   23G  12% /
none                  994M  284K  993M   1% /dev
none                 1000M  196K 1000M   1% /dev/shm
none                 1000M   88K 1000M   1% /var/run
none                 1000M     0 1000M   0% /var/lock
/dev/sdb1             1.9G  544M  1.4G  29% /media/CRUZERII
legalxchech@legalxchech:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd5876b2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3920    31486376    7  HPFS/NTFS
/dev/sda2            3921       31428   220954211    7  HPFS/NTFS
/dev/sda3           35093       38914    30692352   83  Linux
/dev/sda4           31428       35093    29435905    5  Extended
/dev/sda5           31428       34936    28175360   83  Linux
/dev/sda6           34936       35093     1259520   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 2000 MB, 2000682496 bytes
64 heads, 63 sectors/track, 969 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         969     1953439+   b  W95 FAT32
legalxchech@legalxchech:~$

---

### Post by mikewhatever on 2011-03-07
You have Ubuntu installed on /dev/sda5, a 27GB linux partition, however, you also have another linux partition, /dev/sda3, of about 30GB. Not really sure what Windows shows, perhaps the two separate linux partitions?

---

### Post by timjay73 on 2011-03-08
here is what windows shows with the partitions. i assume even tho it shows that the two "other" partitions are filled that they are not in fact so. 

i have no problems reinstalling again since i havent done anything with this install yet. 

how do i do an install that does not take up twice it's size but rather stays in the space that i give it?

---

### Post by mikewhatever on 2011-03-08
The current installation of Ubuntu doesn't take twice the size, it's limited to the 27GB /dev/sda5 partition only. The /dev/sda3 partition seems to be unused, and, I can only guess, remains there from the previous installation attempt. Since you don't appear to need another linux partition, just remove it with the Disk Utility under System->Administration, there is no need to reinstall.

---

### Post by timjay73 on 2011-03-10
> **mikewhatever said:**
> The current installation of Ubuntu doesn't take twice the size, it's limited to the 27GB /dev/sda5 partition only. The /dev/sda3 partition seems to be unused, and, I can only guess, remains there from the previous installation attempt. Since you don't appear to need another linux partition, just remove it with the Disk Utility under System->Administration, there is no need to reinstall.
so i did deleted the sda3 partition and everything is fine but now i have another question. the partition i deleted is at the end of the disk so i now have unallocated free space that i dont want to format into another data partition. 

question: how do i move the linux  partitions to the end of the disk so i can merge the unallocated space into sda2 (my main data partition)?

gparted wouldnt let me do that.

---

### Post by grahammechanical on 2011-03-10
You expand the partition to the left until it takes up all the unallocated space. Then you shrink that partition until it is back to its original size. The unallocated space is now between the two Linux partitons.

Next you expand the other Linux partition until it takes up the unallocated space. Then you shrink it to the size it was. 

Now, the unallocated space is next to the Data partition. Which you now expand to take up the unallocated space.

Regards.

---

### Post by timjay73 on 2011-03-12
> **grahammechanical said:**
> You expand the partition to the left until it takes up all the unallocated space. Then you shrink that partition until it is back to its original size. The unallocated space is now between the two Linux partitons.

Next you expand the other Linux partition until it takes up the unallocated space. Then you shrink it to the size it was. 

Now, the unallocated space is next to the Data partition. Which you now expand to take up the unallocated space.

Regards.
Thanks! that worked. problem solved!

---

