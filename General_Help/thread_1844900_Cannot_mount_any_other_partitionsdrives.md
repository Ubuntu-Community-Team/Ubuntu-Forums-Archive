---
title: "Cannot mount any other partitions/drives"
date: 2011-09-15
forum: General Help
---

### Post by thebarisaxkid on 2011-09-15
I cannot mount any of my other partitons or any of my CD/DVD's other than what is in my fstab. I try to mount it and I get an error: Unable to mount a (drive/part.): Not Authorized.

I have checked that my user is in the storage and optical groups:
```
adm lp wheel games network video audio **optical** **storage** power vboxusers

```
Output of "sudo fdisk -l":

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e68fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   226441216   234440703     3999744   82  Linux swap / Solaris
/dev/sda2            2046   226441215   113219585    5  Extended
/dev/sda5       187379712   226441215    19530752   83  Linux
/dev/sda6        50661376   187379711    68359168   83  Linux
/dev/sda7            2048    24414207    12206080   83  Linux
/dev/sda8        24416256    50653183    13118464   83  Linux

Partition table entries are not in disk order

```
sda5 is my /usr partiton  and sda6 is my /home partition and sda7 is my / partition, I can read/write to these partitions. I however cannot mount sda8 or my CD drive.

---

### Post by raja.genupula on 2011-09-15
please go with this 
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by thebarisaxkid on 2011-09-16
I have now found out that the issue is not limited to the disks. I found that I cannot connect to a network other than the one I connect to by default (Which is Available to All users). I had tried to change the default connection, and it gave me the same error. Now it is clear there is a problem with permissions. However, even when using networkmanager as root, I still cannot change anything. (When I open nautilus as root, my other drives vanish, not shown at all)

I have a feeling this is  gonna get ugly

---

### Post by raja.genupula on 2011-09-16
hey man , do you know i had also faced same issue yesterday evening , actually morning i have seen your issue and evening its effect mine , well i got solution from our forum friends  .

there is a alternative temporary solution to mount manual 
sudo mount /dev/sdaXY /mnt

xy nothing but your drive sda index number .

this is permanent fix 

try to update your gdm, check for updates 

or
```
sudo dpkg-reconfigure gdm
``` 
all the best man

---

### Post by wildmanne39 on 2011-09-16
Hi, have you run some gui programs with sudo?
Thank you

---

### Post by raja.genupula on 2011-09-17
> **wildmanne39 said:**
> Hi, have you run some gui programs with sudo?
Thank you

hi larry , it nice to see you again 

are you asking to me or him ?
i thought that we need sudo to re configure , last night on my own issue also i did this i mean with sudo , but actually mine was xubuntu so it gave me gdm not installed .if is there anything wrong with my post please suggest me back.

thank you larry

---

### Post by wildmanne39 on 2011-09-17
Hi Raja, the sudo command should not be used with graphical programs like gedit, they should be run with gksu or gksudo because this causes programs and files sometimes to become owned by root here is a link to help explain, and it is good to see you my friend.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Thank you

---

### Post by raja.genupula on 2011-09-17
> **wildmanne39 said:**
> Hi Raja, the sudo command should not be used with graphical programs like gedit, they should be run with gksu or gksudo because this causes programs and files sometimes to become owned by root here is a link to help explain, and it is good to see you my friend.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Thank you

hey larry

thanks for suggesting me back , yeah actually i know about it . but what i thought for re-configure is its gonna change all the things to its defaults of the application , so for doing this i thought sudo is enough . but now i will update it . really once again thanks for this .

---

### Post by thebarisaxkid on 2011-09-17
> **raja.genupula said:**
> hey man , do you know i had also faced same issue yesterday evening , actually morning i have seen your issue and evening its effect mine , well i got solution from our forum friends  .

there is a alternative temporary solution to mount manual 
sudo mount /dev/sdaXY /mnt

xy nothing but your drive sda index number .

this is permanent fix 

try to update your gdm, check for updates 

or
```
sudo dpkg-reconfigure gdm
```all the best man

+17 awesome points for you my friend! Solved.

---

### Post by raja.genupula on 2011-09-17
you're welcome .

---

