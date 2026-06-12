---
title: "Ubuntu HDD space with Windows, VirtualBox"
date: 2012-05-13
forum: General Help
---

### Post by robawalsh on 2012-05-13
Hi, 

I want to install Ubuntu onto my laptop, which has a 750GB HDD. 

If I install Ubuntu and give it most of the HDD space (~650GB), and leave 100GB for Windows 7, firstly, is this enough for Windows 7? I won't really be using it unless I find some things I can't do on Linux (some high-end games, for instance). 

But also, if I run Windows in VirtualBox, and install/run applications in it, would this be using the space on the Ubuntu partition, or the Windows partition?

Or, is there an option to choose how much space to give Windows inside VirtualBox, or have it on a separate partition within VirtualBox?

Thanks

EDIT: If I want to run a game which won't run in Linux, would it run on Windows in VirtualBox, or would I have to boot from Windows?

---

### Post by westie457 on 2012-05-13
> **robawalsh said:**
> Hi, 

I want to install Ubuntu onto my laptop, which has a 750GB HDD. 

If I install Ubuntu and give it most of the HDD space (~650GB), and leave 100GB for Windows 7, firstly, is this enough for Windows 7? I won't really be using it unless I find some things I can't do on Linux (some high-end games, for instance). 

But also, if I run Windows in VirtualBox, and install/run applications in it, would this be using the space on the Ubuntu partition, or the Windows partition?

Or, is there an option to choose how much space to give Windows inside VirtualBox, or have it on a separate partition within VirtualBox?

Thanks

EDIT: If I want to run a game which won't run in Linux, would it run on Windows in VirtualBox, or would I have to boot from Windows?

IMHO the best route is dual-boot. 100GB is plenty of space for Windows as the minimum space requirement is around 20-25GB. Also Ubuntu does not really need 650GB again 20-25GB is adequate. However having installation partitions that small a large shared DATA partition formatted to NTFS or FAT32 is a must have.

Install Windows first if possible, if not possible then you will need a LiveCD/USB available to restore Grub to the MBR of the HDD.

Running Windows in a virtual machine will lag a bit and with 3d graphics will probably lag a lot because the hardware will be virtualized, not the native hardware as fitted in the computer.

---

### Post by robawalsh on 2012-05-13
> **westie457 said:**
> IMHO the best route is dual-boot. 100GB is plenty of space for Windows as the minimum space requirement is around 20-25GB. Also Ubuntu does not really need 650GB again 20-25GB is adequate. 


I thought, seeing as I will be primarily using Ubuntu, I should give it most of the disk space, for storing software/files?

> **westie457 said:**
> 
However having installation partitions that small a large shared DATA partition formatted to NTFS or FAT32 is a must have.

I'm confused about this, could you elaborate?

Also, it's formatted to NTFS. But what's the difference between NTFS and FAT32?

> **westie457 said:**
> 
Install Windows first if possible, if not possible then you will need a LiveCD/USB available to restore Grub to the MBR of the HDD.

Windows 7 is pre-installed. 

> **westie457 said:**
> 
Running Windows in a virtual machine will lag a bit and with 3d graphics will probably lag a lot because the hardware will be virtualized, not the native hardware as fitted in the computer.

OK - I thought this might be the case. So dual boot is necessary.

---

### Post by westie457 on 2012-05-13
> **robawalsh said:**
> I thought, seeing as I will be primarily using Ubuntu, I should give it most of the disk space, for storing software/files?



I'm confused about this, could you elaborate?

Also, it's formatted to NTFS. But what's the difference between NTFS and FAT32?



Windows 7 is pre-installed. 



OK - I thought this might be the case. So dual boot is necessary.

I too primarily use Ubuntu, Windows is pre-installed as well. Whichever OS I decide to use when something has finished downloading or has been ripped and I want to keep it, it goes into the DATA partition to be easily accessed by the OS I boot into later. This partition also serves as one of my backup storage areas.

The reason it is formatted to NTFS is simply because of the 4GB file size limit of FAT32.

Attached is a screenshot of my HDD as it was late last year.

---

### Post by robawalsh on 2012-05-13
> **westie457 said:**
> I too primarily use Ubuntu, Windows is pre-installed as well. Whichever OS I decide to use when something has finished downloading or has been ripped and I want to keep it, it goes into the DATA partition to be easily accessed by the OS I boot into later. This partition also serves as one of my backup storage areas.

The reason it is formatted to NTFS is simply because of the 4GB file size limit of FAT32.

Attached is a screenshot of my HDD as it was late last year.

So, I should have a partition for Ubuntu OS, a partition for Windows OS, and a DATA partition for music/video/games? I.e., 3 partitions?

---

### Post by Mopar1973Man on 2012-05-13
I'm partitioned even more so...

NTFS

(1.0 TB Drive - All split into 150 GB parts)
C: Windows Vista x64
D: Windows Swap Drive
E: Music (MP3)
F: Downloads
G: Web Site Stuff
H: Pictures

(1.5 TB)
I: Backup Drive

(250 GB)
Ubuntu Linux Ext4

Since Linux is capable of mounting any Windows drive I left my windows set up just the way I had it.

---

### Post by robawalsh on 2012-05-13
> **Mopar1973Man said:**
> I'm partitioned even more so...

NTFS

(1.0 TB Drive - All split into 150 GB parts)
C: Windows Vista x64
D: Windows Swap Drive
E: Music (MP3)
F: Downloads
G: Web Site Stuff
H: Pictures

(1.5 TB)
I: Backup Drive

(250 GB)
Ubuntu Linux Ext4

Since Linux is capable of mounting any Windows drive I left my windows set up just the way I had it.

So it's perfectly OK to have, for example, my music library (>70GB) on one partition, and using the Ubuntu boot partition I can still easily access it with software etc?

---

### Post by robawalsh on 2012-05-13
For software running on Ubuntu, should that be in the Ubuntu partition or the Data partition? I might have a lot of software, so if it has to go on the Ubuntu partition, I should probably give the Ubuntu partition at least 50GB.

---

