---
title: "harddrive recovery after ubuntu installation"
date: 2012-08-19
forum: General Help
---

### Post by seyd on 2012-08-19
Hello

I installed Ubuntu from the live cd. I noticed the installation this time around looked quite differently, when choosing how to install i picked the first option *run ubuntu alongside windows 7, keep all your documents and settings*, sweet i thought, i get to keep all my files. After the installation was done i noticed ubuntu had freely chosen which harddrive and partition to format and install on. I was strangely enough never notified about this. 

The partition ubuntu had chosen turns out to be one of my windows storage disks. My question is, can i somehow recover the stored data or is it all lost questionmark.

Grateful for any help or advice.

---

### Post by darkapec on 2012-08-19
more than likely all of your windows data is still there, selecting the install alongside windows option, will tell ubuntu to automatically resize your primary windows partition and install ubuntu on the same partition. 

However I have not done that option for a long time, but I do recall it asking "how much disk space would you like to allow ubuntu to have" and if you told it to take the whole drive it will do precisely that. 

first thing, always backup data first

second thing, if your in the ubuntu environment use a testdisk utility called photorec it will be able to recover everything but its not going to be pretty. All files will have random names and it will also find all the files you dont care about eg the 7000+ images that come along with microsoft office.

another option would be to use another computer with windows and use some more advanced utilities (although there not free) like EASEUS data recovery aka "THE UNDELETE," or ACTIVE UNDELETE. Both of these tools will be able to scan your drive finding all of your old windows files. Again a lot of them may have lost there names so files like music / movies are almost worthless because it is not worth renaming them all. But you will still be able to get irreplaceable family photos etc. 

third thing, if it did install along side you should be able to boot from a windows 7 disk and select startup repair and then boot back into your windows installation. Once all of your data is backed up and you are comfortable enough to proceed. You will need to either update BCD to include the linux install or update grub to include the windows install. I am concerned that this did not happen otherwise you would see an option to boot into windows or linux when you turn on the computer.

best of luck and let us know if you need more help

---

### Post by seyd on 2012-08-19
Thank you so much for your reply.

I can still boot windows 7 without any problems, upon startup it asks wether to boot windows or ubuntu. It finds the disk but ofc it cannot open it as its now a linux partition.

With the tools you mention will i be able to open, read and possibly recover the windows files from the linux drive questionmark.

---

### Post by NikTh on 2012-08-19
Hi,
cay you boot in to Ubuntu and open a terminal (ctrl+alt+t) and post the results of these commands 
```
sudo fdisk -l 
sudo parted -l
```
Thanks

---

### Post by seyd on 2012-08-19
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x73bae658

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   611112591   305555272    7  HPFS/NTFS/exFAT
/dev/sda2       611112592   625137344     7012376+  79  Unknown

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe552e552

 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   112647779    56323858+   7  HPFS/NTFS/exFAT
/dev/sdb2       112647780   976751999   432052110    f  W95 Ext'd (LBA)
/dev/sdb5       112647843   976751999   432052078+   7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce39d914

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1250263727   625131863+  ee  GPT

Disk /dev/sdd: 1981 MB, 1981808640 bytes
1 heads, 1 sectors/track, 3870720 cylinders, total 3870720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        3552     3870719     1933584    c  W95 FAT32 (LBA)
```/////////////////////////////////////////////////////////////////////////////////////


```
 Model: ATA WDC WD3200AAKS-0 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  313GB  313GB   primary  ntfs         boot
 2      313GB   320GB  7181MB  primary  fat32


Model: ATA SAMSUNG HD501LJ (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  57.7GB  57.7GB  primary   ntfs         boot
 2      57.7GB  500GB   442GB   extended               lba
 5      57.7GB  500GB   442GB   logical   ntfs


Model: ATA WDC WD6400AACS-0 (scsi)
Disk /dev/sdc: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system     Name                          Flags
 1      17.4kB  134MB  134MB                   Microsoft reserved partition  msftres
 2      134MB   135MB  1000kB                                                bios_grub
 3      135MB   636GB  636GB   ext4
 4      636GB   640GB  4293MB  linux-swap(v1)


Model: Kingston DataTraveler G2 (scsi)
Disk /dev/sdd: 1982MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1819kB  1982MB  1980MB  primary  fat32        boot, lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
```

---

### Post by seyd on 2012-08-19
I should mention im currently running from the live cd, not the actual installation of ubuntu.

---

### Post by NikTh on 2012-08-19
> **seyd said:**
> I should mention im currently running from the live cd, not the actual installation of ubuntu.

No problem , the only problem is I forgot to mention .. 
please put the results inside ```
 tags so can be readable.. so if you not mind , edit your post and [noparse][code]put the results here
```[/noparse] 
Thanks

---

### Post by NikTh on 2012-08-19
Hi , 
you can run this automatic repair tool from liveCD --> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) , follow the 2nd option and see if  something has been fixed.
Also it will be good to provide the info file , that  will be created.

Although the problem could be the GPT partition table and I cannot help you with that. You must wait a  more experienced user.
Thanks

---

### Post by darkapec on 2012-08-19
> **seyd said:**
> Thank you so much for your reply.

I can still boot windows 7 without any problems, upon startup it asks wether to boot windows or ubuntu. It finds the disk but ofc it cannot open it as its now a linux partition.

With the tools you mention will i be able to open, read and possibly recover the windows files from the linux drive questionmark.


Data recovery should not be needed, everything is still there. Now it is just a matter of getting one of the OS's to boot and you can simply copy and paste the files you need to backup. 

can you access the drive from the livecd? I am not sure how to do it on 12.04 I am not familiar with unity enough and I do not know the easy command line way to do it.

In prior versions you would just click on "places" on the menu bar and it would show you drives that were connected but not mounted and all you had to do was click on the drive.

---

### Post by seyd on 2012-08-19
The filesystem i wish to recover is perfectly readable from the livecd and the installation of ubuntu. As i mentioned earlier i can ofc not open this disk from windows.

I cannot find my windows files on the disk however.

---

### Post by seyd on 2012-08-20
bump

---

### Post by seyd on 2012-08-20
Im leaving this to a recovery company today. They said over the phone its hard to estimate how much of it that can be recovered before they've actually explored it themselfs.

Does anyone have any experience with this? What are my chances here?

---

