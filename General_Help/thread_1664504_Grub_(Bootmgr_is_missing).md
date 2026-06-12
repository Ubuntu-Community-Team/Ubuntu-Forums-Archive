---
title: "Grub (Bootmgr is missing)"
date: 2011-01-11
forum: General Help
---

### Post by abdulqadir93 on 2011-01-11
I use ubuntu 10.10. Everything was great until i formatted my C drive which had win xp. Now at startup an error message occurs instead of booting ubuntu (BOOTMGR is missing. Press Cntrl+alt+delete to restart). I searched a little bit and found that may be I need to install GRUB (boot loader).

how do i install grub? Please help! using "fdisk -l" .. I found out that my bootable partition is C drive (NTFS /dev/sda1) while ubuntu is installed on another partition (ext3 /dev/sda3)!

---

### Post by wilee-nilee on 2011-01-11
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by abdulqadir93 on 2011-01-11
thnx ... i tried .. but looks like i;m doing something wrong ...

i mounted my two partitions as

sudo mount /dev/sda1 /mnt/boot (as it is the bootable partition)
sudo mount /dev/sda3 /mnt/home (it is the parition where ubuntu is isntalled)

Then when i ran this command

sudo grub-install --root-directory=/mnt /dev/sda

It asked me to run apt-get install grub. And when i wrote "apt-get install grub". An error occured like "unable to fetch some archives. Try running apt-update or fix missing"

So, what do i do now? please help

---

### Post by wilee-nilee on 2011-01-11
I don't think you read the link correctly maybe do this. So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by abdulqadir93 on 2011-01-11
Ok .. here it is ... Hope i did everything right this time :)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,872,319   104,872,257   7 HPFS/NTFS
/dev/sda2         209,728,636   625,137,344   415,408,709   f W95 Ext d (LBA)
/dev/sda5         209,728,638   314,584,829   104,856,192   7 HPFS/NTFS
/dev/sda6         314,584,893   419,441,084   104,856,192   7 HPFS/NTFS
/dev/sda7         419,441,148   524,297,339   104,856,192   7 HPFS/NTFS
/dev/sda8         524,297,403   625,137,344   100,839,942   7 HPFS/NTFS
/dev/sda3         104,873,984   202,528,767    97,654,784  83 Linux
/dev/sda4         202,528,768   209,727,487     7,198,720  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1998 MB, 1998585856 bytes
255 heads, 63 sectors/track, 242 cylinders, total 3903488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     3,903,487     3,903,425   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       0972d006-65d5-f349-85f1-597dd7b5452e   ext2       casper-rw                     
/dev/sda1        357699A342660D40                       ntfs       System                        
/dev/sda2: PTTYPE="dos" 
/dev/sda3        470557f8-7aa1-41f1-9f1d-84b99f510db5   ext4                                     
/dev/sda4        d2e9680e-ead6-4a62-af0a-d4cf27cdc247   swap                                     
/dev/sda5        645CA0275C9FF1D2                       ntfs       Muffu                         
/dev/sda6        2818AB8018AB4C1E                       ntfs       Muffu                         
/dev/sda7        CE3CCB1D3CCB0007                       ntfs       Abdul                         
/dev/sda8        EE3CDB3D3CDB000F                       ntfs       Murtaza                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B8CE-8987                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /mnt                     ext4       (rw)
/dev/sda1        /mnt/boot                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev             /mnt/dev                 none       (rw,bind)
/dev/sda3        /mnt/home                ext4       (rw)
/dev/sda7        /media/Abdul             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=470557f8-7aa1-41f1-9f1d-84b99f510db5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=d2e9680e-ead6-4a62-af0a-d4cf27cdc247 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 48 02  |.X.SYSLINUX...H.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c1 8f 3b 00 dc 0e 00 00  00 00 00 00 02 00 00 00  |..;.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 87 89 ce b8 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 d8 c7 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by wilee-nilee on 2011-01-11
Boot the live Ubuntu cd and open gparted in system-admin-gparted take a screen shot with the take screenshot tool in menu-accessories and post it.

The script is missing lots of stuff that should show and multiple partitions starting at sector 63. 

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       **at sector 63.**
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       **at sector 63.**
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       **at sector 63.**
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       **at sector 63.**
    Operating System:  
    Boot files/dirs:

---

### Post by abdulqadir93 on 2011-01-11
here it is ...

---

### Post by wilee-nilee on 2011-01-11
I suggest you wait for more qualified help. I see to much missing to feel comfortable any farther then this, sorry.

---

