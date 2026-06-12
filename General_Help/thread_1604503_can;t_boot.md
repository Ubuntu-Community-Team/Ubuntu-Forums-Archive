---
title: "can;t boot"
date: 2010-10-24
forum: General Help
---

### Post by Foredeck on 2010-10-24
I tried to upgrade to Ubuntu 10.10 last week, and something happened  during the install.  The drives became read only, and had to reboot.  

After that, it would never reboot, and got stuck in initframs.  

I used the live CD to check the disk and the memory, and didn't find  anything.  When I tried to install again, it froze as soon as it  started.

I tried to mount the drive from the live CD, but that doesn't work. 

I don't mind formatting the drive, but I can't even do that.  Is there  any way to work around here without taking a hammer to the drive?

---

### Post by Rubi1200 on 2010-10-24
Use the LiveCD and post the results of the boot-script linked at the bottom of my post please.

The results will hopefully help us determine at least part of what is going on.

Thanks.

---

### Post by Foredeck on 2010-10-24
How long should that script take?

In terminal, I have :

> ubuntu@ubuntu:~/Downloads$ sudo bash boot_info_script055.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdf...
Searching sda1 for information... 

It's been like that for almost 30 minutes.

---

### Post by Rubi1200 on 2010-10-24
Very strange! The results should be generated in no more than a minute or so.

---

### Post by Foredeck on 2010-10-24
I tried to mount the drive, but it failed.  

After over an hour, it's still searching SDA1 for information...

It does see the drive in gparted, but unable to mount it.  It actually has the used and free space right in there as well.

---

### Post by Rubi1200 on 2010-10-24
Do not mount the drive, there is no need.

Put the script on the Desktop on the LiveCD and run it again using the instructions.

Hopefully, that will work.

EDIT: do you have a RAID setup?

---

### Post by Foredeck on 2010-10-24
I took the jumper off the hard drive, and it seems to have fixed the problem of not responding.  I previously had a master and a slave drive, but had to disconnect the slave drive to connect the CD rom.

When I ran the script, I got :  (the dev/sdf1 is the thumb drive)

 >                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   477,837,359   477,837,297  83 Linux
/dev/sda2         477,837,360   488,392,064    10,554,705   5 Extended
/dev/sda5         477,837,423   488,392,064    10,554,642  82 Linux swap / Solaris


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 4211 MB, 4211081216 bytes
130 heads, 62 sectors/track, 1020 cylinders, total 8224768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             62     8,221,199     8,221,138   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2: PTTYPE="dos" 
/dev/sda5        fcb8aa9d-e19b-4220-a38e-1858dcf54233   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdf1        8C24-5F3D                              vfat                                     
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /media/8C24-5F3D         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

---

### Post by Foredeck on 2010-10-24
I just tried rebooting without the Lice CD and got the following message :

error: unknown filesystem
grub rescue >
Not sure if this is a step forward, back or just a step sideways,  /i read somewhere that I just had to direct the computer to the ubuntu folder, but not sure how to do this.

---

### Post by Rubi1200 on 2010-10-24
I am concerned that the results show that your file systems are failing to mount. It could be that during the updates "something happened" as you mentioned.

I suggest running the following commands from the LiveCD and see if it brings the system back up again:

```
sudo e2fsck -C0 -p -f -v /dev/sda1
```

If you get errors then run this:

```
sudo e2fsck -f -y -v /dev/sda1
```

---

