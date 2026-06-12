---
title: "volume &quot;filesystem root&quot; has only 25mb space remaining"
date: 2011-02-28
forum: General Help
---

### Post by timjay73 on 2011-02-28
I'm getting an error message that something along the lines of "volume "filesystem root" has only 25mb space remaining". what do i do? how do i increase the volume size so i never have to worry about it again? i havent been very successful in finding an answer here. 

I'm quite the newbie with this but this is the 3rd time i've tried ubuntu and it's sticking more and more but this has me thoroughly perplexed. 

i've got a 320GB HDD partitioned 3 times with a Linux partition being 7GB.

dual booting Win7Pro. 
running ubuntu 10.10 64-bit. 

i'm sure this is an easy fix but i couldnt find anything about it and the linux partition is not even close to being full.  

thanks for the help

---

### Post by seawolf167 on 2011-02-28
The suggested Ubuntu partition size is 10GB

[*"it's recommended you free up at least 10 GB of free space for your Ubuntu install"*]("https://help.ubuntu.com/community/WindowsDualBoot")

You'll want to use the program GParted from a Ubuntu LiveCD to resize your Ubuntu partition.

If you open a terminal and type 

```
sudo fdisk -l
```We can help you with partition sizes

As usual, I suggest backing up your drive with [Clonezilla ]("http://www.clonezilla.org")before you do anything so you can recover your disk if something goes wrong during partitioning.

If you type in 

```
sudo df -h
```

you can see the space used & available by each partition in your Ubuntu install

---

### Post by philinux on 2011-02-28
In addition to post #2 check this out.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by timjay73 on 2011-02-28
legalxchech@legalxchech:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd5876b2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3920    31486376    7  HPFS/NTFS
/dev/sda2            3921       36867   264646357    7  HPFS/NTFS
/dev/sda3           36868       38913    16434017+   f  W95 Ext'd (LBA)
/dev/sda5           37878       38913     8321638+   7  HPFS/NTFS
/dev/sda6           36868       37828     7712768   83  Linux
/dev/sda7           37828       37877      398336   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mmcblk0: 1967 MB, 1967128576 bytes
57 heads, 56 sectors/track, 1203 cylinders
Units = cylinders of 3192 * 512 = 1634304 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        1204     1920955+   6  FAT16

Disk /dev/sdb: 2000 MB, 2000682496 bytes
64 heads, 63 sectors/track, 969 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         969     1953439+   b  W95 FAT32



legalxchech@legalxchech:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             7.3G  6.8G   98M  99% /
none                  994M  292K  993M   1% /dev
none                 1000M  272K 1000M   1% /dev/shm
none                 1000M   92K 1000M   1% /var/run
none                 1000M     0 1000M   0% /var/lock
/dev/sda5             8.0G   63M  7.9G   1% /media/sda5
/dev/sda2             253G  131G  122G  52% /media/sda2
/dev/mmcblk0p1        1.9G     0  1.9G   0% /media/KINGSTON 2G
/dev/sdb1             1.9G  544M  1.4G  29% /media/CRUZERII


i'll work on getting a currennt back up disc image. 

thanks for the quick reply!

---

### Post by seawolf167 on 2011-02-28
> **timjay73 said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3920    31486376    7  HPFS/NTFS
/dev/sda2            3921       36867   264646357    7  HPFS/NTFS
/dev/sda3           36868       38913    16434017+   f  W95 Ext'd (LBA)
/dev/sda5           37878       38913     8321638+   7  HPFS/NTFS
**/dev/sda6           36868       37828     7712768   83  Linux**
/dev/sda7           37828       37877      398336   82  Linux swap / Solaris


Filesystem            Size  Used Avail Use% Mounted on
**/dev/sda6             7.3G  6.8G   98M  99% /**
none                  994M  292K  993M   1% /dev
none                 1000M  272K 1000M   1% /dev/shm
none                 1000M   92K 1000M   1% /var/run
none                 1000M     0 1000M   0% /var/lock
/dev/sda5             8.0G   63M  7.9G   1% /media/sda5
/dev/sda2             253G  131G  122G  52% /media/sda2
/dev/mmcblk0p1        1.9G     0  1.9G   0% /media/KINGSTON 2G
/dev/sdb1             1.9G  544M  1.4G  29% /media/CRUZERII

You'll need to resize one of your Windows partitions. I suggest doing this from within Windows itself using the built-in [Windows partition editor]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/"). 

You'll probably want to increase the / partition to 20GB or more since you do not have a separate partition for /home (i.e. /home resides under /, so downloads, personal files, etc. will all increase the / partition size)

Once you do that to get free space (unallocated space) you need to resize the linux partition into the free space. [Here ]("http://en.kioskea.net/faq/2036-how-to-resize-a-partition-using-gparted-on-linux")is a little how-to for using GParted.

---

### Post by timjay73 on 2011-02-28
oops. i did not mention that the 252GB partition is where i have all my docs, music, pics, etc. stored so i have none of those types of files stored on the linux partition (except downloaded files and such). i will repartition and that should solve the problem?

---

### Post by seawolf167 on 2011-02-28
Yea, resizing will solve your problem. On a 320GB drive, 20GB isn't too much space, and it'll save you the headache of having to resize again in the future. 

You can of course resize to any size you wish.

Don't forget to backup beforehand just in case!

---

### Post by timjay73 on 2011-02-28
i was in disk management in windows and noticed that there were 2 extra partitions that i was not aware of (see attachment). they have no names but are both at 100% and added up they are close to the size of linux partition. are they separate partitions or partitions within the linux partition? so confused. my question is which partition do i increase? one of the 100% filled partitions or the linux partition?

thanks

---

### Post by tredegar on 2011-02-28
Unless you want to lose all your linux data, do not let a windows program adjust your linux partitions.

Make backups if your data is important, then boot from a live cd and use **gparted** to resize your partitions.

---

### Post by seawolf167 on 2011-02-28
> **tredegar said:**
> unless you want to lose all your linux data, do not let a windows program adjust your linux partitions.

Make backups if your data is important, then boot from a live cd and use **gparted** to resize your partitions.

+1

---

### Post by timjay73 on 2011-02-28
> **timjay73 said:**
> i was in disk management in windows and noticed that there were 2 extra partitions that i was not aware of (see attachment). they have no names but are both at 100% and added up they are close to the size of linux partition. are they separate partitions or partitions within the linux partition? so confused. my question is which partition do i increase? one of the 100% filled partitions or the linux partition?

thanks

i promise to backup and use gparted. can anyone respond to my previous questions i quoted above?

---

### Post by seawolf167 on 2011-02-28
> **timjay73 said:**
> i promise to backup and use gparted. can anyone respond to my previous questions i quoted above?

Recovery partitions from the factory installation of your Windows OS

---

### Post by mcduck on 2011-03-01
> **timjay73 said:**
> i promise to backup and use gparted. can anyone respond to my previous questions i quoted above?

Those are your Linux partitions. Windows doesn't understand any other partitions/filesystems than it's own, which is why it lists Linux partitions like that.

The first nameless partition is /dev/sda6, your Linux root partition. And the other one is /dev/sda7, the swap partition.

---

### Post by timjay73 on 2011-03-03
thank you mcduck for your response, however my question is still not answered. 

i hope the following makes sense:

can anyone specify as to which partition i should increase? 

i have 5 partition options and i think i can exclude 2 of them: OS-windows (sda1) and data-my junk (sda2) - i can exclude these, true?

which leaves me with 3 options: 
gparted shows (along with the previously mentioned partitions): 
sda3 - extended
---(sda5) Linux 
---(sda6) ext4
---(sda7)linux-swap 

which of 3 do i increase? all of them? 

thanks.

---

### Post by mcduck on 2011-03-03
Like the *df -h* output tells, your Linux root partition is /dev/sda6 and that's also the one that's running out of space.
```

/dev/sda6 7.3G 6.8G 98M 99% /
```

---

### Post by timjay73 on 2011-03-07
i gave up. i couldnt get gparted to do what i wanted without throwing up errors so i reformatted the whole the thing and am starting from scratch. but now i have more questions which i will post in a new thread. thanks for the help.

---

