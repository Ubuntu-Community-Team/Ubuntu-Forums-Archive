---
title: "Need help formating a hard drive"
date: 2010-04-17
forum: General Help
---

### Post by polardude1983 on 2010-04-17
I need serious help with formatting a hard drive. I know there are step by step walkthroughs on the net I found 2. But I'm still not getting it.

I really do need someone basically to visually walk it through with me.

Not sure how i would be able to do it. but i do need help.

I'm trying to format a second hard drive that has partitions on it and stuff.

---

### Post by polardude1983 on 2010-04-17
Ok well i think I erased everything on my second hard drive and now Should i select it as primary partition? or extended? its a second hard drive so....

---

### Post by Serpher on 2010-04-17
First of all, how do you want it formatted? If you don't know, what's going to be the purpose of this hardrive? Just to install Ubuntu on it? Also other partitions with no OS's on it, act like USB's you connect to computer and show up under Places.

---

### Post by polardude1983 on 2010-04-17
Ok so im trying to format it as fat32 and it keeps failing :/

---

### Post by Serpher on 2010-04-17
Why FAT32 @_@? FAT32 should never be used on a hardrive except in very VERY specific cases. Again what are you trying to accomplish with this formatting?

---

### Post by polardude1983 on 2010-04-17
GParted 0.4.5

Libparted 1.8.8.1.159-1e0e

Create Primary Partition #1 (fat32, 465.76 GiB) on /dev/sdb  00:00:01    ( ERROR )
    	
create empty partition  00:00:01    ( SUCCESS )
    	
path: /dev/sdb1
start: 63
end: 976768064
size: 976768002 (465.76 GiB)
set partition type on /dev/sdb1  00:00:00    ( SUCCESS )
    	
new partition type: fat32
create new fat32 file system  00:00:00    ( ERROR )
    	
mkdosfs -F32 -v -n "" /dev/sdb1
    	
mkdosfs 3.0.3 (18 May 2009)
/dev/sdb1: No such file or directory
libparted messages    ( INFO )
    	
Error informing the kernel about modifications to partition /dev/sdb1 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sdb1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sdb (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sdb.
Error informing the kernel about modifications to partition /dev/sdb1 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sdb1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sdb (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sdb.
========================================

---

### Post by polardude1983 on 2010-04-17
I had a lot of crap on my computer and I have done some things that I probably shouldnt have done. as I have now somehow 3 installations of linux. 2 or 3 versions of ubuntu 9.10 installed and one mint.

Trying to clean up

---

### Post by Serpher on 2010-04-17
So do you just want one partition with one Operating system? Also you can't format the partition you're using, you'll want to use a LiveCD.

---

### Post by polardude1983 on 2010-04-17
i know newb. 

I have my main hard drive which has 2 partitions The current ubuntu 9.10 im using sda1 and the one with windows install sda2.

Its the sdb the one that i cleared and trying to use as additional storage space.

---

### Post by Serpher on 2010-04-17
Do you want that hardrive to be accessible for both Windows and Linux? And don't worry, it took me weeks to get my first distro, Ubuntu 8.04 off the ground xP. We were all noobs.

Due to my lack of time, if you want them accessed by both, use some Windows 7 (for the best NTFS to date I guess) instillation CD and simply install Windows until it formats the hardrive as NTFS. NTFS is like FAT32 but FAT32 tends to fragment a LOT more.

If just Ubuntu, and gparted isn't working, type in these commands in terminal

```
sudo fdisk /dev/sdb
n
p
1
[Enter]
[Enter]
w
sudo mkfs -t ext4 /dev/sdb1
```

I might have some of the stuff between 1 and w wrong and you might have to press 'q' to quit fdisk, however you should probably get the idea.

sudo fdisk /dev/sdb = Run the program fdisk to partition the sdb hardrive
n = Make a new partition
p = Primary partition
1 = number assigned to partition
[Enter] = Start at block 1
[Enter] = End at last block
w = Partition disk
q = Quit
h = Show fdisk commands
sudo mkfs -t ext4 /dev/sdb1 = Make an ext4 type file system (Fastest file system evar) to the first partition in the sdb hardrive.

---

### Post by polardude1983 on 2010-04-17
I am way more noobish :/ Now i need to find my live cd. god i suck. Since I formatted the sdb partition my grubs gone. so Im currently running mint from my usb. and now trying to restore grub. gawd i suck

---

### Post by polardude1983 on 2010-04-17
i need to stop before i kill msyelf. lol

---

### Post by john newbuntu on 2010-04-17
Boot using an Ubuntu liveCD.  Open gparted.  Select one partition at a time from /dev/sdb and delete it one by one.  Then choose the entire disk and partition it as type NTFS.  This way, both your windows and Linux can share this partition.

Being the first partition on /dev/sdb, yYou can choose it as primary.  But remember that there can be no more than 4 primaries or 3 primaries and an extended one per disk.

I would prefer just partitioning(primary) a small portion of it (say around 100GB) as NTFS.  Leave the rest as unpartitioned.  This way, you can later format it to any other partition or even extend it if necessary.

Yeah and get off that FAT stuff.

Once you do all these, log on to Ubuntu and run the following if you are using karmic:
sudo update-grub

---

