---
title: "Accidentally Deleted Ubuntu Partition. Help!!!"
date: 2010-02-13
forum: General Help
---

### Post by sir_robert007 on 2010-02-13
Hey I was recently reinstalling Windows on my pc when I realized I accidentally deleted my Ubuntu root partition. Fortunately I realized this during the partitioning part of the installation and aborted the installation before I wrote any data to the disk. I have heard that you can recover data from a deleted partition by using a tool called testdisk. Never had to do a data recovery until now so I'll need some help using testdisk. I had important data on that partition that I really need to retrieve so an answer ASAP would be appreciated.

Comp Specs

Ubuntu 9.10 64-bit
1 TB hard drive
AMD Phenom II X4
4 GB ram

---

### Post by lenoirrichelieu on 2010-02-13
I didn't get entirely what means stopping before. If you stopped before any writing then how can you say is deleted? And viceversa if the partition disappeared then how you didn't write anything?

---

### Post by Mukoi on 2010-02-13
Don't know a lot about all this, but I have used testdisk.

This is what I did:
[http://ubuntuforums.org/showthread.php?t=1371185](http://ubuntuforums.org/showthread.php?t=1371185)

Hope that it will help.

---

### Post by ironclaw on 2010-02-13
If nothing has been written to the part of the drive that contained your Ubuntu root partition, then all you have to do is to find out which cylinders your partition was originally on, and add that to the partition table.

You can boot into a live CD, then unmount all partitions just to make sure that nothing is written to the disk while trying to recover the partition. Then install testdisk:
```
sudo apt-get install testdisk
```

In a terminal run
```
sudo testdisk /dev/<device>
```
where <device> is your hard drive, probably sda since you only have one hard drive. Follow the instructions (you probably have an Intel partition table type) and select 'Analyse', then 'Quick Search'.

When it has finished, you should get a list of partitions (including deleted ones that haven't been overwritten) that testdisk has found. Hopefully your Ubuntu root partition will be there. At this point, I think you can continue working in testdisk to recreate the partition table and add that partition, but I prefer to work with fdisk.

Use
```
sudo fdisk /dev/<device>
```
to add a new partition with cylinders that correspond to those found by testdisk.

Tell me if you need more instructions.

---

### Post by sir_robert007 on 2010-02-13
> **ironclaw said:**
> If nothing has been written to the part of the drive that contained your Ubuntu root partition, then all you have to do is to find out which cylinders your partition was originally on, and add that to the partition table.

You can boot into a live CD, then unmount all partitions just to make sure that nothing is written to the disk while trying to recover the partition. Then install testdisk:
```
sudo apt-get install testdisk
```In a terminal run
```
sudo testdisk /dev/<device>
```where <device> is your hard drive, probably sda since you only have one hard drive. Follow the instructions (you probably have an Intel partition table type) and select 'Analyse', then 'Quick Search'.

When it has finished, you should get a list of partitions (including deleted ones that haven't been overwritten) that testdisk has found. Hopefully your Ubuntu root partition will be there. At this point, I think you can continue working in testdisk to recreate the partition table and add that partition, but I prefer to work with fdisk.

Use
```
sudo fdisk /dev/<device>
```to add a new partition with cylinders that correspond to those found by testdisk.

Tell me if you need more instructions.

Ok I performed the steps you outlined and testdisk listed the following partitions:

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121602 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  9895 254 63  158979177
D Linux Swap           10214   1  1 10748 254 63    8594712
D Linux                10749   1  1 35373 254 63  395600562
D Linux                35374   1  1 47832 254 63  200153772
D Linux                47833   1  1 60799 254 63  208314792
D Linux                60800   0  1 89791 254 63  465756480
D FAT32 LBA            89792   1  1 92830 254 63   48821472 [NO NAME]
D Linux Swap           92831   1  1 93377 254 63    8787492
D HPFS - NTFS          93378   1  1 121600 254 63  453402432



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 232 GB / 216 GiB

```
I have no idea which one is my Ubuntu root partition. It was roughly about 200 GB in size so would I simply select one about that size? Or is there a way I can mount each of these partitions so I can look inside and see if I have the one with my data on it?

---

### Post by jwmislan on 2010-02-13
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 1000 GB / 931 GiB - CHS 121602 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0   1  1  9895 254 63  158979177
D Linux Swap           10214   1  1 10748 254 63    8594712
D Linux                10749   1  1 35373 254 63  395600562
D Linux                35374   1  1 47832 254 63  200153772
D Linux                47833   1  1 60799 254 63  208314792
D Linux                60800   0  1 89791 254 63  465756480
D FAT32 LBA            89792   1  1 92830 254 63   48821472 [NO NAME]
D Linux Swap           92831   1  1 93377 254 63    8787492
D HPFS - NTFS          93378   1  1 121600 254 63  453402432



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 232 GB / 216 GiB

Just follow what testdisk says for the cursor actions.

You need to change all the partitions from ' D ' ( deleted ) - to either, *=bootable  P=Primary  L=Logical  E=Extended  
by using left/right arrow keys and testdisk wil give a message at the bottom whether the new selection is Good or Bad .

The LBA 7 line down  - looks like to me that it's an extended partition you should probably mark that with E and see if testdisk says Good .

There's more than 4 partitions so they can't all be P primary ones - some have to be L logical as well - you should always keep track of how you partitioned your drive/s .
 
I just recently recovered my / and /home partitions that got deleted by a sudden shutdown when they were mounted while I was running from my other Debian partition.

So testdisk can do what you need , and by judging from what you pasted here, it should work OK.

You will need to follow through with the testdisk, save the partition table to disk -  for your changes to be saved.

If you get stuck quit out of testdisk without saving anything, and start it up again - then go through the menus - and read everything carefully.

Hope this helps 
Best of luck 
John WM

---

### Post by ironclaw on 2010-02-13
There is a good guide on the official [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") website.

You can use testdisk to view the files in a partition by pressing 'P'. You might also want to try 'Deeper Search' in testdisk to detect more partitions. This is all covered in the guide that I linked to.

---

### Post by sir_robert007 on 2010-02-14
Ok I performed all the steps that everyone here outlined and I was able to recover my Ubuntu root partition with all my data intact and was able to mount it under the Ubuntu live cd. Now is there a way that I can make it bootable again? Would I be able to do that via the live cd?

---

### Post by wilee-nilee on 2010-02-14
This is a wiki on grub2 step 11 has several ways to return grub.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

---

### Post by terrrorr on 2010-02-14
Hi,

There is couple recovery tools I know, but these all all Window based. Here is what I found. For sure, the best way is to create/use liveCD which includes these tools. Remember, try to use the hard drive as little as possible. Then you have better chances...

Here is list where TestDisk is included 

[http://www.cgsecurity.org/wiki/TestDisk_Livecd]("http://www.cgsecurity.org/wiki/TestDisk_Livecd")

I have used gparted and SystemRescue liveCDs to some other tasks.



Good luck

---

### Post by sir_robert007 on 2010-02-15
I'm back to report that I have succeeded in rebuilding Grub and got my Ubuntu installation to boot up with all my data intact. Just wanted to say thank you to everyone who helped me and I will continue to come to these forums for all my Linux/Ubuntu questions. Thanks!!

---

