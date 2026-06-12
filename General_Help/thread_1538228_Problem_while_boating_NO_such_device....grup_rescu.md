---
title: "Problem while boating: NO such device....grup rescue"
date: 2010-07-24
forum: General Help
---

### Post by ashraf.abdelrahman on 2010-07-24
Hi everyone,

I am new to ubuntu and I face a problem after installing it inside windows using wubi I asked to update after finishing update I was asked to restart .... here is the problem occurred..the following message appear 
error: no such device: 72ba3405-a288-45e7-a4ab-7830e572a676
grup rescue>


I see the following thread at this forum

[http://ubuntuforums.org/showthread.php?t=1437840](http://ubuntuforums.org/showthread.php?t=1437840)

and I try every thing in this thread

ls
(hd0) (hd1) (hd2)

I tried the live cd and try the script and here is the output


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 68. But according to the info from fdisk, 
                       sda5 starts at sector 16133.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       /wubildr.mbr /wubildr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *         16,065   156,296,384   156,280,320   5 Extended
/dev/sda5              16,133    62,219,744    62,203,612   7 HPFS/NTFS
/dev/sda6          62,219,808   123,973,604    61,753,797   7 HPFS/NTFS
/dev/sda7         123,973,668   156,296,384    32,322,717   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    62,521,199    62,521,137   7 HPFS/NTFS
/dev/sdb2          62,521,200   312,575,759   250,054,560   f W95 Ext d (LBA)
/dev/sdb5          62,521,263   125,042,399    62,521,137   7 HPFS/NTFS
/dev/sdb6         125,042,463   187,563,599    62,521,137   7 HPFS/NTFS
/dev/sdb7         187,563,663   250,084,799    62,521,137   7 HPFS/NTFS
/dev/sdb8         250,084,863   312,575,759    62,490,897   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       72ba3405-a288-45e7-a4ab-7830e572a676   ext4                                     
/dev/sda1: PTTYPE="dos" 
/dev/sda5        704CDB7D4CDB3C92                       ntfs       UBUNTU                        
/dev/sda6        80EDD829D810147C                       ntfs       ASHRAF                        
/dev/sda7        D42C16692C1646C0                       ntfs       SONGS                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        76E0140AE013CF6D                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        96BC7F09BC7EE2E3                       ntfs       PROGRAMS                      
/dev/sdb6        FA749C1C749BD9A9                       ntfs       CARTOON                       
/dev/sdb7        4404A90C04A90252                       ntfs       ISLAMIC                       
/dev/sdb8        2E20B6B520B6837F                       ntfs       MEDIA                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sdb1/boot.ini: ================================

[boot loader]
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
timeout=30
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional" /Fastdetect
C:\wubildr.mbr = "Ubuntu"


Now I don't know what to do to gain access again to ubuntu and windows

Note that I am new in ubuntu or any other linux 
I have 2 hard disks attached to my pc
80 GB IDE connected
160 GB SATA connected

windows and ubuntu on the 80 GB and the other one is for storage

I need your help as fast as possible

Thank you

---

### Post by bcbc on 2010-07-25
> **ashraf.abdelrahman said:**
> Hi everyone,

I am new to ubuntu and I face a problem after installing it inside windows using wubi I asked to update after finishing update I was asked to restart .... here is the problem occurred..the following message appear 
error: no such device: 72ba3405-a288-45e7-a4ab-7830e572a676
grup rescue>


I see the following thread at this forum

[http://ubuntuforums.org/showthread.php?t=1437840](http://ubuntuforums.org/showthread.php?t=1437840)

and I try every thing in this thread

ls
(hd0) (hd1) (hd2)

I tried the live cd and try the script and here is the output
...
Now I don't know what to do to gain access again to ubuntu and windows

Note that I am new in ubuntu or any other linux 
I have 2 hard disks attached to my pc
80 GB IDE connected
160 GB SATA connected

windows and ubuntu on the 80 GB and the other one is for storage

I need your help as fast as possible

Thank you

You need to restore the windows bootloader to /dev/sdb for a start. grub should not be installed in either that or /dev/sda for a wubi install.

You can ether use a windows repair cd to fix this (command fixmbr) or you can install an equivalent bootloader from the live CD.
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
sudo lilo -M /dev/sda mbr
```

lilo used in this way works just like windows - it boots the partition marked active. You don't need it on /dev/sda, but you don't need grub there either - so the last line is optional.

This won't fix the ubuntu. It seems like there it has been corrupted. The [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?") has some instructions e.g. run chkdsk on windows, and try running fsck on the root.disk. It's worth a shot, but in the meantime let's see if windows will boot.

---

### Post by bcbc on 2010-07-25
Please could you post back the version of wubi you installed - was it 10.04? 
Did you run normal system updates or were you upgrading from 9.10 to 10.04?
Did you get a prompt asking you where to install grub and did you select /dev/sda and /dev/sdb if this is the case?
Is there anything else you might have done that was unusual or was this simply an normal update that silently did this?

This information will help others who encounter the same problem. Thanks

---

### Post by ashraf.abdelrahman on 2010-07-25
First of all thanks bcbc repairing windows boot loader works well

the wubi version is the version used within the ubuntu CD downloaded from ubuntu website

Ubuntu version 10.0.4

The update required is the update required by ubuntu after installation actually I don't remember if it asked or not as Iam new to ubuntu and I used to accept and click ok with windows not good thing to do that but windows works in a way like that

---

### Post by bcbc on 2010-07-25
> **ashraf.abdelrahman said:**
> First of all thanks bcbc repairing windows boot loader works well

the wubi version is the version used within the ubuntu CD downloaded from ubuntu website

Ubuntu version 10.0.4

The update required is the update required by ubuntu after installation actually I don't remember if it asked or not as Iam new to ubuntu and I used to accept and click ok with windows not good thing to do that but windows works in a way like that

Great that it's working. Thanks for the feedback.

If you can recall, did you see something like this:> 

Configuring grub-pc

GRUB Install Devices:

[] /dev/sda/ 

[] /dev/sdb/

'The Grub boot loader was previously installed to a disk that is no longer present or whose normally unique indentifier was changed for some reason. It is important to make sure that the installed grub stays in sync with other components such as the grub-cfg or with newer linux images it will have to load, and so you should check again, to make sure that GRUB is installed to the appropriate boot devices.

If you are unsure which drive is designated as boot drive, by your bios, it is often a good idea to install GRUB to all of them.

Note: It is possible to install GRUB to partition boot records as well, and some appropriate partitions are offered here. However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore not recommended.'

It would have been a very noticeable large window popup during the update process and hard not to notice.

---

### Post by angel34160 on 2010-07-25
Hi I'm new at this just 3 days with unbuntu and I just broke my lap :(

I have a Hp 2133 and a external hard drive western digital 80G connected by usb  what i tried to do was use the 80G HD with unbuntu and the 160G internal with Win xp as usual but now appear the error no such device and just the message 

error: no such device: xxxxxxx
grub rescue> _ 

I installed the unbuntu by usb and the HD external is in usb but now on the bios optiopn no usb boot option appear and i can't run the installer again  just the internal HD and netboot options the lap top don't include cd room so can't run the win setup  cd try the comand that say up but only 

>_  ls                            work 
(hd0)  (hd0,1)  (fd0)

and I'm really a new one at this so any response make it in a way easy to understand (with draws will be great :D)   any idea?

Thnaks

---

### Post by bcbc on 2010-07-25
> **angel34160 said:**
> Hi I'm new at this just 3 days with unbuntu and I just broke my lap :(



It's the same error but caused by a totally different thing. i recommend starting a new thread.

---

### Post by angel34160 on 2010-07-25
OK I'll start a new one Thanx :)

---

