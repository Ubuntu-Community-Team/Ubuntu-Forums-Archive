---
title: "Extending Linux partition"
date: 2010-03-05
forum: General Help
---

### Post by Keith1212 on 2010-03-05
Originally my root file system was about 10gb. I decided i wanted more so i went back onto windows and shrunk my windows partition another 10gb. I rebooted to my Live Gparted cd and extended the "ext4" file system which is the one i recognized to have my linux install on it. It showed that the space was added, but rebooting back to Ubuntu still showed the same amount.
    So i read some more and a comment mention editing the fstab, but didn't go into detail. How can i get linux to recognize the added space?

---

### Post by flippo on 2010-03-05
It should be automatically detected, if the partition is larger.

What is the output of:
```
df -h
```and```
fdisk -l
```

---

### Post by Keith1212 on 2010-03-05
> **flippo said:**
> It should be automatically detected, if the partition is larger.

What is the output of:
```
df -h
```and```
fdisk -l
```


```
df -hFilesystem            Size  Used Avail Use% Mounted on
/dev/sda5            
 9.6G  5.5G  3.6G  61% /
udev                  497M  388K  497M   1% /dev
none                  497M  100K  497M   1% /dev/shm
none                  497M  288K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
none                  9.6G  5.5G  3.6G  61% /var/lib/ureadahead/debugfs
/dev/sdd1             1.9G  1.9G  6.0M 100% /media/2GB FLASH B
/dev/sdb2             408G  313G   95G  77% /media/1811-1722
/dev/sdb1              59G   11G   49G  18% /media/OneTouch 4
/dev/sdc1             2.0G  732M  1.3G  38% /media/2GB Flash OLD
```and 
fdisk -l
did nothing.

---

### Post by Keith1212 on 2010-03-05
I rebooted into Gparted and this is what it shows atm. 
[IMG]http://img413.imageshack.us/img413/5227/digi0001.jpg[/IMG]

This is the Tut I used btw.
[http://www.simplehelp.net/2008/11/04/how-to-resize-linux-partitions-using-gparted/](http://www.simplehelp.net/2008/11/04/how-to-resize-linux-partitions-using-gparted/)

---

### Post by bumanie on 2010-03-05
> sudo fdisk -l That is a lower case L, not the digit one. You screenshot looks as though you have a 19.92gb logical partition with linux on a 9.77gb partition as unallocated. You should be able to enlarge /dev/sda5 into the unallocated space. You may have drag the entire /dev/sda5 partition to the left and then enlarge it to the right. Working within a logical partition is slightly more difficult to a primary partition, but is should work OK. You may need to do two or three operations to get the job done. Here's a link to a [gparted tutorial]("http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html") - it may help. It's a while since I have played around with partitions with in a logical partition, but increasing the size and getting rid of the unallocated space, should be possible. Read the tutorial - post back if you have problems.

---

### Post by flippo on 2010-03-05
Okay, I see your problem.  You extended your extended partition (/dev/sda2), but you didn't extend the ext4 part of it (as seen by your unallocated part within /dev/sda2).  You need to extend /dev/sda5 by 10gb (which is next to it and free) to actually increase your linux FS size.

---

### Post by Keith1212 on 2010-03-06
Ok that worked. I think i got confused and didn't do that because i tryed to extend that one the first time. So when i extended the other one i thought it was done. Well ty for the help all!

---

