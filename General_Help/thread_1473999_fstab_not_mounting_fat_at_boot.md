---
title: "fstab not mounting fat at boot"
date: 2010-05-05
forum: General Help
---

### Post by eltopo1 on 2010-05-05
Hello,

I'm puzzled as to why this fstab isn't working:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=edd61501-358a-4610-961f-2cd4e3b963c1 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=5d1f1508-069b-4274-9bfa-ae2bf7ffb5e0 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=be0afdc6-10bb-4744-a71c-02e0e2812160 none            swap    sw              0       0

UUID=BD41-1F70    /dev/sdb1       /media/MUZ      vfat         uid=1000,gid=1000,shortname=mixed,user,umask=0000 0 0        
UUID=D7A8-B7BB    /dev/sdb2       /media/MOVIEZ   vfat         uid=1000,gid=1000,shortname=mixed,user,umask=0000 0 0    
UUID=D91E-6728    /dev/sdb3       /media/TOPO     vfat         uid=1000,gid=1000,shortname=mixed,user,umask=0000 0 0 
```

Problem is at boot I'm getting 

```
mount: unknown filesystem type '/media/MUZ'
```
and 
```
mountall terminated with status error 32
```

for all 3 fat partitions. No login, the screen just hangs there with these errors.

When I leave the fat partitions out of the fstab I can log in, and mount them manually (in media/MUZ_, media/MOVIEZ_, etc).

I've taken the fstab syntax from my previous 9.10 install, it worked fine then (I've done a clean install of 10.04 on another disk).

Here's some more info, possibly non-pertinent but you never know:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb3 starts at sector 778236795.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    39,063,551    39,061,504  83 Linux
/dev/sda2          39,065,598   156,301,311   117,235,714   5 Extended
/dev/sda5          39,065,600    46,876,671     7,811,072  82 Linux swap / Solaris
/dev/sda6          46,878,720   156,301,311   109,422,592  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   409,593,239   409,593,177   b W95 FAT32
/dev/sdb2         409,593,240   778,236,794   368,643,555   b W95 FAT32
/dev/sdb3         778,236,795   976,768,064   198,531,270   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        edd61501-358a-4610-961f-2cd4e3b963c1   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        be0afdc6-10bb-4744-a71c-02e0e2812160   swap                                     
/dev/sda6        5d1f1508-069b-4274-9bfa-ae2bf7ffb5e0   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BD41-1F70                              vfat       MUZ                           
/dev/sdb2        D7A8-B7BB                              vfat       MOVIEZ                        
/dev/sdb3        D91E-6728                              vfat       TOPO                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda6        /home                    ext4       (rw)
/dev/sr0         /media/Ubuntu 10.04 LTS i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdb1        /media/MUZ_              vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb3        /media/TOPO_             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdb2        /media/MOVIEZ_           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```

Could it be a permissions issue maybe? Or maybe the Windows installed on another disk is the cause? It was wrongly recognized as the sdb disk instead of the fat one when all 3 were plugged in, I figure I've got to change that in the bios but right now it's completely unplugged.

Help?

---

### Post by WorMzy on 2010-05-05
You have too many arguments for the bottom three entrys. Remove the /dev/sdb# from the last three lines.

---

### Post by eltopo1 on 2010-05-06
That was it indeed, seems pretty obvious now.

Thank you dude.

---

### Post by WorMzy on 2010-05-06
Any time. :)

---

