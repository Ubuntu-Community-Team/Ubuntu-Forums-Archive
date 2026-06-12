---
title: "Local disk E..."
date: 2011-12-26
forum: General Help
---

### Post by EpicWorld on 2011-12-26
On Ubuntu I can view 2 of my partitions that i have on windows, AKA Local disk C and local disk D. But i can't view the most important one [for me] aka local disk E. How do i add it on Ubuntu? :confused:

---

### Post by BC59 on 2011-12-26
Can you post the result of these commands?

```
sudo parted /dev/sda print
sudo fdisk -l # 
```#(it's a lower case L)

---

### Post by EpicWorld on 2011-12-26
> **BC59 said:**
> Can you post the result of these commands?

```
sudo parted /dev/sda print
sudo fdisk -l # 
```#(it's a lower case L)

Erm no effect for me <:|

In other words:
I see to devices 
1st one says: 52 GB filesystem and it has same content as local disk C on windows
2nd one says: 105 GB filesystem and it has same content as local disk D on windows
[missing]3rd one that should have same content as local disk E on windows :|

---

### Post by BC59 on 2011-12-26
Can you copy and paste the result here?

---

### Post by EpicWorld on 2011-12-26
okee dokee

```
amigo@ubuntu:~$ sudo parted /dev/sda print
[sudo] password for amigo: 
Model: ATA WDC WD2500BEVT-2 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  52.4GB  52.4GB  primary   ntfs         boot
 2      52.4GB  250GB   198GB   extended               lba
 5      52.4GB  157GB   105GB   logical   ntfs
 6      157GB   250GB   92.8GB  logical   ntfs

amigo@ubuntu:~$ sudo fdisk -l #

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce6dce6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   102398309    51199123+   7  HPFS/NTFS/exFAT
/dev/sda2       102398310   488375999   192988845    f  W95 Ext'd (LBA)
/dev/sda5       102398373   307194929   102398278+   7  HPFS/NTFS/exFAT
/dev/sda6       307194993   488375999    90590503+   7  HPFS/NTFS/exFAT
amigo@ubuntu:~$ 

``` 

there

---

### Post by BC59 on 2011-12-26
You have right, there are 3 Windows partitions. The easiest way to mount the partition that cannot be mounted is through the Storage Device Manager. If you use Ubuntu 11.04 or 11.10 install it through Ubuntu Software Center. 
Then open it and from the left panel, you should see all the partitions. On the right panel is a button "mount" to mount them. Try with this tool to see if you can solve the problem.

---

### Post by WorMzy on 2011-12-26
I imagine the partition you can't find is the one you installed Wubi to? If that's the case it's already mounted under /host.

---

### Post by EpicWorld on 2011-12-26
> **WorMzy said:**
> I imagine the partition you can't find is the one you installed Wubi to? If that's the case it's already mounted under /host.


yeah i installed WUBI to this partition.

---

### Post by WorMzy on 2011-12-26
Then question answered, problem solved? :)

---

### Post by EpicWorld on 2011-12-27
> **WorMzy said:**
> Then question answered, problem solved? :)

one more question, where can i find it? P:

---

### Post by Elfy on 2011-12-27
Thread tools at the top :)

---

### Post by EpicWorld on 2011-12-27
> **forestpiskie said:**
> Thread tools at the top :)

i mean where can i find /host or how it's named P:

---

### Post by Elfy on 2011-12-27
:lol:

Have a look in Places - then filesystem then /host

Alternatively you could open nautilus at that point from a terminal

nautilus /host

---

### Post by WorMzy on 2011-12-27
Yeah, if you open a file manager, then go "up" the directory tree as far as you can go, you'll end up in "/", which is sort of like a combination of "My Computer" and "C:\" on Windows. From there you can get to any folder on any mounted filesystem; most are mounted under /media, but the Wubi host is under /host.

---

