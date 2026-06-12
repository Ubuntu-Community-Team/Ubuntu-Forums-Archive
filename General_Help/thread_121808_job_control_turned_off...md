---
title: "job control turned off.."
date: 2006-01-26
forum: General Help
---

### Post by werty on 2006-01-26
I was working with ubuntu till yesterday..
Today when i tried to boot ubuntu it said 
"job control turned off - dev/sda9 not found" whatever that means i
cannot boot ubuntu anymore.. what should i do

---

### Post by amohanty on 2006-01-26
One possibility is that your partition table is messed up. Would it be possible for your to boot using a LiveCD and posting the output of:
> fdisk -l

AM

---

### Post by werty on 2006-01-26
ok now ubuntu seems to have returned to normal...
im using reiserfs and i want to change the file system to
ext2...
so what i m thinking right now is to reinstall ubuntu...
but now the install cd wont work...
i ve checked for the boot device priority. everything seems to be
correct but the install cd dosen't work...
???next

thx

---

### Post by amohanty on 2006-01-26
Do you get any error messages?

AM

---

### Post by werty on 2006-01-28
i had to reinstall ubuntu... with ext3 partitions.. the first time i booted there was no 
problem. but i did get the error message once.
you were saying about messed partition tables.  During the installations i saw that the partitions were not in order.. how can i make them correct?

---

### Post by amohanty on 2006-01-28
You can go through the install process, however when you get to the partition section do the following:
1. Select Manual Partition option
2. Dont change anything.
3. Resetup all partition to the correct mount points.
4. DO NOT select the format option
5. Hit save
6. Exit out of the install.

This regenerates the partition table.

HTH
AM

---

