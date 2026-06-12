---
title: "Ubuntu 10.04 can't mount my Hitachi simpledrive External drive"
date: 2010-05-14
forum: General Help
---

### Post by optix7 on 2010-05-14
hey guys, ive been facing a  problem lately after a week of a fresh install of 10.04

i am  being unable to mount my SimpleDrive external drive

[COLOR=Lime]the below info might help[/COLOR]
------------------------------------------------:confused:
optix@optix-laptop:~$ [COLOR=Red]sudo fdisk -l[/COLOR]
[sudo] password for optix: 


Disk /dev/sda: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x05c105c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2574    19459408+   7  HPFS/NTFS
/dev/sda2            2575        3123     4150440    7  HPFS/NTFS
/dev/sda3            3124        5168    15454468    f  W95 Ext'd (LBA)
/dev/sda5            5039        5168      982768+  82  Linux swap / Solaris
/dev/sda6   *        3124        5038    14466469+  83  Linux

Partition table entries are not in disk order

[B]Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x65b67a48[/B]

   Device Boot      Start         End      Blocks   Id  System


---------------------------------------------------------

optix@optix-laptop:~$ [COLOR=Red]sudo blkid[/COLOR]
[B]/dev/sda1: UUID="C29CB9FB9CB9EA55" TYPE="ntfs" 
/dev/sda2: UUID="1D06C7F0DF20467F" TYPE="ntfs" 
/dev/sda5: TYPE="swap" 
/dev/sda6: UUID="86a5bd4a-a859-4e29-a081-0ef610515755" SEC_TYPE="ext2" TYPE="ext3" 

[/B]

--------------------------------------------------------

optix@optix-laptop:~$ [COLOR=Red]cat /etc/fstab[/COLOR]
[B]#Entry for /dev/sda6 :
UUID=86a5bd4a-a859-4e29-a081-0ef610515755    /    ext3    defaults    0    1
#Entry for /dev/sda1 :
UUID=C29CB9FB9CB9EA55    /media/C29CB9FB9CB9EA55    ntfs-3g    defaults,user,locale=en_US.utf8    0    0
#Entry for /dev/sda2 :
UUID=1D06C7F0DF20467F    /media/sda2    ntfs-3g    defaults,locale=en_US.utf8    0    0
UUID=    swap    swap    sw    0    0
[/B]


---------------------------

ive got some important data that im trying to access , so please any help would be appreciated

---

### Post by optix7 on 2010-05-14
any ideas ??  a desperate noob here ;/

---

### Post by blueridgedog on 2010-05-14
The output of fdisk -l shows no partitions on sdb.  Have you been using the drive?  Can you use the drive in other systems or other operating systems?  If it is new, then you will need to use gparted to create and format a partition prior to use.

---

### Post by optix7 on 2010-05-14
Windows XP didnt detect it either

Gparted saw the drive but as Unallocated file system :(

what does this mean ? is my data gone for good ?

[[IMG]http://img404.imageshack.us/img404/8130/28195756.png[/IMG]]("http://img404.imageshack.us/i/28195756.png/")

[]("http://imageshack.us")

---

### Post by blueridgedog on 2010-05-14
perhaps it is lost, but you should try a program called testdisk to verify that there isn't a portion that you can recover.  If you search this forum and google you will find many step by step examples of using testdisk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by optix7 on 2010-05-15
Thanks **[blueridgedog]("http://ubuntuforums.org/member.php?u=459469") **for the help . i will give it a go and come back with the results

---

### Post by optix7 on 2010-05-15
testdisk did the job . thanks again for the help

i was able to see the files, i need to figure out a way to boot it now or at least back it up, the interface is kinda simple and doesnt have many options to work around with.well im glad the data is still there

---

### Post by blueridgedog on 2010-05-16
Use testdisk to restore the partition table...see the howto:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by optix7 on 2010-05-17
> **blueridgedog said:**
> Use testdisk to restore the partition table...see the howto:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Thank You ! that did it for me :)

---

### Post by GlennW on 2010-05-18
@blueridgedog, I've been following this thread and wondered if there is any similarity to my situation. Following a fresh install of 10.04, I cannot mount my dvd. The cd mounts nicely. 

After having read through other posts, I have commented out the /dev/... in my fstab. That had no effect. I've read that 10.04 now uses the media folder to house dvd and cd code. Not being very knowledgeable with Ubuntu any help you could offer would be appreciated.

Thanks.

```
glenn@glenn-desktop:~$ sudo hdparm -I /dev/sr0
[sudo] password for glenn: 

/dev/sr0:

ATAPI CD-ROM, with removable media
	Model Number:       HITACHI GD-2000                         
	Serial Number:      
	Firmware Revision:  0056    
Standards:
	Likely used CD-ROM ATAPI-1
Configuration:
	DRQ response: 50us.
	Packet size: 12 bytes
	cache/buffer size  = 128 KBytes
Capabilities:
	LBA, IORDY(can be disabled)
	Buffer size: 128.0kB
	DMA: sdma0 sdma1 sdma2 mdma0 mdma1 *mdma2 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns

```


```
glenn@glenn-desktop:~$ ls -l /dev/{cd,dvd}*
lrwxrwxrwx 1 root root 3 2010-05-18 15:59 /dev/cdrom -> sr1
lrwxrwxrwx 1 root root 3 2010-05-18 15:32 /dev/cdrom1 -> sr0
lrwxrwxrwx 1 root root 3 2010-05-18 15:59 /dev/cdrw -> sr1
lrwxrwxrwx 1 root root 3 2010-05-18 15:32 /dev/dvd1 -> sr0

```

---

### Post by blueridgedog on 2010-05-18
Not the same issue, and it should not require something special in fstab.  Did you install the restricted extras and libdvdcss2?

```
sudo apt-get install ubuntu-restricted-extras
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list 
sudo apt-get -q update
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring
sudo apt-get -q update
sudo apt-get install libdvdcss2
```

---

### Post by GlennW on 2010-05-19
@blueridgedog. I implemented your code but to no avail. 

Any other thoughts? It appears that there are many others with a similar issue. Might this be a bug?

Thanks.

---

### Post by blueridgedog on 2010-05-19
I suggest you start a new thread then with a title that 10.04 will mount CDROMS but not DVD.  Indicate that you have libdvdcss2.  Perhaps others will have better ideas.

---

### Post by GlennW on 2010-05-19
Thanks, blueridgedog, for your time and thought into this issue. I'll begin a new thread as you suggest.

All the best....

---

