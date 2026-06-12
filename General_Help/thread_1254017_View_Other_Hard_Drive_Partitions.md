---
title: "View Other Hard Drive Partitions"
date: 2009-08-30
forum: General Help
---

### Post by Kristofer Van Orton on 2009-08-30
Okay so my computer has a total 320GB hard drive broken up into 2 approx. 160GB partitions. I set up Ubuntu onto the DATA partition (rather than the one labled ACER which contains my Windows OS)
My problem is that I want to be able to view the files contained in ACER using UBUNTU, but while in Ubuntu all I can view is the second partition that UBUNTU is located on. So is there anyway to make it so I can view both my partitions in the Places menu or is it just a lost cause?
(sorry if this is a stupid question but I'm totally new to linux as a whole)

---

### Post by uylug on 2009-08-30
What is the ouput of

```
sudo fdisk -l
```

---

### Post by Kristofer Van Orton on 2009-08-30
I put it in and it said:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c5e10f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2089    16777216   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *        2089       20254   145905664    7  HPFS/NTFS
/dev/sda3           20254       38913   149884749    7  HPFS/NTFS

---

### Post by uylug on 2009-08-30
Then do

To mount the first one:
```
sudo mkdir /media/mntdisk;sudo mount /dev/sda1 /media/mntdisk/ -t ntfs-3g 

```

To mount the second one:
```
sudo mkdir /media/mntdiskb;sudo mount /dev/sda3 /media/mntdiskb/ -t ntfs-3g 

```

---

### Post by Kristofer Van Orton on 2009-08-30
that mounted something labled PQSERVICE with 6.2GB which appears to have my some of the WINDOWS files but when I go into the users folder my username isn't in there
therefore im confused now...i only have 2 partitions on my computer and there both about 160GB...

---

### Post by uylug on 2009-08-30
Disk 1:
```
nautilus /media/mtndisk
```
Disk 2:
```
nautilus /media/mtndiskb
```

That?

---

### Post by Kristofer Van Orton on 2009-08-30
for both of them it said "could not find please check your spelling and try again"

---

### Post by uylug on 2009-08-30
> **Kristofer Van Orton said:**
> for both of them it said "could not find please check your spelling and try again"

Sorry :lolflag:

Disk 1:
```
nautilus /media/mntdisk
```
Disk 2:
```
nautilus /media/mntdiskb
```

---

### Post by Kristofer Van Orton on 2009-08-30
The first one just opened the random PQSERVICE disk, and the second one just opened the DATA partition that I already had...
sorry to take so much of your time...if you have any other ideas id be glad to here them, if not thank you so much for your time and effort to helping me

---

### Post by uylug on 2009-08-30
Can you see the rest of the files with Windows?

Sorry for being completely useless but you said you could see some of the files, then you should be able to see all of them

---

### Post by Kristofer Van Orton on 2009-08-30
when I'm in windows I can view either of the partitions no problem
the PQSERVICE disk first of all is only 6.2GB while my other partion is something like 160GB (as mentioned before) what I mean by I can see some of the files that are in the PQSERVICE partition i can see things like the Windows folder, Program Files, Users, ect. you know like you would see in my other partition. except the problem is for example when I go to users it only shows 2 profiles (niether of which are mine and neither of which have my music/pictures ect. in them
it seems as if I've opened part of the partition, only being able to view some of the files, which makes no sense to me, it doesnt even sounds possible, i just dont know where this PQSERVICE partition even came from
ugh,...im so confused

---

### Post by uylug on 2009-08-30
See what you mean.
What is the output of this command:

```
sudo ls -la /media/mntdisk/Users
```

---

### Post by Kristofer Van Orton on 2009-08-30
```
ls: cannot access /media/mntdisk/Users: No such file or directory
```:confused:damn


also i dont know if this makes a difference but i just logged onto windows and went in and looked at both the partitions only to realize that the partition thats not showing up is actually the one with ubuntu installed on it  (both windows and ubuntu for that matter)
i dont know how i didnt realize this before :P
sorry for being a noob, but again i dont even know if this makes a bit of difference

---

### Post by Kristofer Van Orton on 2009-08-31
*bump*
sorry i dont know if bumping a topic in considered spamming here but does anyone else have some suggestions?

---

