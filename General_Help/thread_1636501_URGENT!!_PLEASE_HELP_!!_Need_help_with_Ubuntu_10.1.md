---
title: "URGENT!! PLEASE HELP !! Need help with Ubuntu 10.10 netbook remix"
date: 2010-12-03
forum: General Help
---

### Post by TroubledPerson on 2010-12-03
HELP ME!!!
Okay I'm in the 'Allocate Drive Space' section of the installation and I want to kick out my 'Windows 7 Starter' and have just one operating system which is the 'Ubuntu Netbook Remix 10.10'.

But I have ONE question : If I choose the "Erase And Use The Entire Disk" option,will it disturb my drives and stuff??

---

### Post by Verbeck on 2010-12-03
'Erase And Use The Entire Disk' will delete everything on the hard-disk regardless of the partition on which the data is on

so i you want to keep the data on the 'd: drive' safe, choose manually partition (or something along those lines)

then from the following screen, select the partition on which windows is installed and delete it (it'll REMOVE EVERYTHING on THAT partition)

then select the unallocated space and make the following partitions (its just my preference : a separate /home makes things easier if you need to reinstall)

type=swap size=same as ram         <----------------like a page-file in windows
type=ext4 size=10-15gb mountpoint=/         <----------------main system files go here
type=ext4 size=therest mountpoint=/home         <-----------------------your user files and application preferences are here

---

### Post by TroubledPerson on 2010-12-03
> **Verbeck said:**
> 'Erase And Use The Entire Disk' will delete everything on the hard-disk regardless of the partition on which the data is on

so i you want to keep the data on the 'd: drive' safe, choose manually partition (or something along those lines)

then from the following screen, select the partition on which windows is installed and delete it (it'll REMOVE EVERYTHING on THAT partition)

then select the unallocated space and make the following partitions (its just my preference : a separate /home makes things easier if you need to reinstall)

type=swap size=same as ram         <----------------like a page-file in windows
type=ext4 size=10-15gb mountpoint=/         <----------------main system files go here
type=ext4 size=therest mountpoint=/home         <-----------------------your user files and application preferences are here


THANKS :D

I havent actually tried it yet,but thanks in advance :3

---

