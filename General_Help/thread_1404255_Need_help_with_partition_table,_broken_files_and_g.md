---
title: "Need help with partition table, broken files and grub loader"
date: 2010-02-11
forum: General Help
---

### Post by Anorexorcist on 2010-02-11
I'm using a dell inspiron 1525 with the kubuntu 9.10 distribution and dual boot with vista.
I'm not a complete n00b with kubuntu and I have been using it for about a year, but I still am not confident with the more advanced kubuntu stuff.

I tried resizing a partition in vista using the vista disk manager and it showed my KDE partition as "free space". I didnt think anything of it until next time I tried to boot, the grub loader showed error 22 and wouldnt work. I Used a super grub disk and could only find a boot option for vista.

I loaded vista and did some research on the internet and decided i'd try my luck with testdisk/photorec. Ran testdisk and it was succesful and I could load KDE again(although only using the super grub disk). All my files were still present on KDE but when I checked the vista partition all my windows files have been converted into text files ranging somewhere between 700mb and 1.2gb in size.

Also gparted shows my whole HDD as "unallocated".

Any help with either fixing the grub loader or with the windows files would be appreciated.

Thanks

---

### Post by Anorexorcist on 2010-02-11
bump

---

### Post by meierfra. on 2010-02-11
```
Ran testdisk and it was succesful 
```
What exactly did you do with testdisk?  
Could you post the screen with the [Deep search ]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")results?

Also  please follow these [instructions ]("http://bootinfoscript.sourceforge.net/")to run the boot info script and post the RESULTS.txt

---

### Post by Anorexorcist on 2010-02-11
I have ran testdisk in kubuntu and deep search finds the partition I am looking for but it says its deleted.

Results from boot_info_script.sh:

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x88000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       192,779       192,717   6 FAT16
/dev/sda2             192,780    67,312,349    67,119,570   c W95 FAT32 (LBA)
/dev/sda3         125,371,323   224,861,802    99,490,480  83 Linux
/dev/sda4         224,861,805   234,452,609     9,590,805   f W95 Ext d (LBA)
/dev/sda5         224,861,868   229,183,267     4,321,400  82 Linux swap / Solaris
/dev/sda6         229,197,824   234,438,655     5,240,832   c W95 FAT32 (LBA)

/dev/sda4 ends after the last sector of /dev/sda

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D8-0115                              vfat       DellUtility                   
/dev/sda2        07D8-0115                              vfat                                     
/dev/sda3        257eadb8-406a-4d37-828c-30b8339291fb   ext3                                     
/dev/sda5        ce3c6566-310f-48f9-a67e-90a73543913d   swap                                     
/dev/sda6        D466-F7A6                              vfat       MEDIADIRECT                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda2        /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,uid=1000,utf8,shortname=mixed,flush)


=========================== sda3/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=257eadb8-406a-4d37-828c-30b8339291fb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=257eadb8-406a-4d37-828c-30b8339291fb

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        257eadb8-406a-4d37-828c-30b8339291fb
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=257eadb8-406a-4d37-828c-30b8339291fb ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        257eadb8-406a-4d37-828c-30b8339291fb
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=257eadb8-406a-4d37-828c-30b8339291fb ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        257eadb8-406a-4d37-828c-30b8339291fb
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=257eadb8-406a-4d37-828c-30b8339291fb ro quiet splash 
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        257eadb8-406a-4d37-828c-30b8339291fb
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=257eadb8-406a-4d37-828c-30b8339291fb ro  single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        257eadb8-406a-4d37-828c-30b8339291fb
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=257eadb8-406a-4d37-828c-30b8339291fb ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        257eadb8-406a-4d37-828c-30b8339291fb
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=257eadb8-406a-4d37-828c-30b8339291fb ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        257eadb8-406a-4d37-828c-30b8339291fb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=257eadb8-406a-4d37-828c-30b8339291fb ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        257eadb8-406a-4d37-828c-30b8339291fb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=257eadb8-406a-4d37-828c-30b8339291fb ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, kernel 2.6.27-11-generic
uuid        257eadb8-406a-4d37-828c-30b8339291fb
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=257eadb8-406a-4d37-828c-30b8339291fb ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-11-generic (recovery mode)
uuid        257eadb8-406a-4d37-828c-30b8339291fb
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=257eadb8-406a-4d37-828c-30b8339291fb ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.10, memtest86+
uuid        257eadb8-406a-4d37-828c-30b8339291fb
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title        Windows Vista/Longhorn (loader)
root        (hd0,2)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title        Microsoft Windows XP Embedded
root        (hd0,4)
savedefault
makeactive
chainloader    +1


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=257eadb8-406a-4d37-828c-30b8339291fb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=ce3c6566-310f-48f9-a67e-90a73543913d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

================================ sda6/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768

---

### Post by meierfra. on 2010-02-11
Please use copy and paste to post the deep search screen, I really would like to see it. 
Also at the deep  search screen use the up/down arrow keys to select each partition listed  and press "p" to get a directory listing;  let us  know exactly which partitions give you a directory listing.

---

### Post by Anorexorcist on 2010-02-11
Its gonna take about 15 mins to get the deep search results again, I'll paste them as soon as I can. Thanks for helping me with this btw :)

---

### Post by Anorexorcist on 2010-02-11
This is what I got when I listed files for the partition that is currently missing

```
    HPFS - NTFS           1317 134 34  7803 115  1  104196361 [OS]
Directory /

dr-xr-xr-x     0     0         0 26-Jan-2009 22:54 .
dr-xr-xr-x     0     0         0 26-Jan-2009 22:54 ..
dr-xr-xr-x     0     0         0 21-Jan-2008 17:02 DELL
-r--r--r--     0     0      4389 21-Jan-2008 17:24 dell.sdr
dr-xr-xr-x     0     0         0  4-Jun-2009 23:56 devkitPro
dr-xr-xr-x     0     0         0 21-Jan-2008 17:04 doctemp
dr-xr-xr-x     0     0         0 23-Jan-2008 08:49 Documents and Settings
dr-xr-xr-x     0     0         0 21-Jan-2008 17:02 Drivers
dr-xr-xr-x     0     0         0 23-Jan-2008 08:55 Intel
-r--r--r--     0     0         0  2-Apr-2008 02:56 IO.SYS
dr-xr-xr-x     0     0         0 19-Sep-2009 16:18 Microgaming
-r--r--r--     0     0         0  2-Apr-2008 02:56 MSDOS.SYS
-r--r--r--     0     0     22729 21-Jan-2008 09:48 newfile.enc
-r--r--r--     0     0     22729 21-Jan-2008 09:48 newkey
-r--r--r--     0     0   2450845696 24-Nov-2009 22:50 pagefile.sys
dr-xr-xr-x     0     0         0  2-Jun-2008 23:39 PerfLogs
dr-xr-xr-x     0     0         0 21-Jan-2008 16:55 Program Files
dr-xr-xr-x     0     0         0 21-Jan-2008 16:55 ProgramData
dr-xr-xr-x     0     0         0  2-Apr-2008 10:57 Programs
                                                   Next

```

---

### Post by meierfra. on 2010-02-11
The directory listing looks good, so you should be able to recover your missing partition. But
I really need to see the deep search screen which list all the partitions.

---

### Post by Anorexorcist on 2010-02-11
Should I get some screenshots?
Also the partition that should have windows on has renamed itself and decided to convert all my windows files to plain text documents.

---

### Post by meierfra. on 2010-02-11
You can  post a   screen shot or just use copy and paste. But I need see  the partitions listed on the deep search screen.

---

### Post by meierfra. on 2010-02-11
The screen I need to see looks something like this:

[IMG]http://www.cgsecurity.org/mw/images/Results_deeper_search.gif[/IMG]

---

### Post by Anorexorcist on 2010-02-11
I know what info you need now but I'll have to post it tomorrow, because I need to go now.

---

### Post by Anorexorcist on 2010-02-14
Before running quick search:
[IMG]http://i869.photobucket.com/albums/ab255/Anorexorcist13/snapshot1.jpg[/IMG]

After quick search:
[IMG]http://i869.photobucket.com/albums/ab255/Anorexorcist13/snapshot2.jpg[/IMG]

Deep search results:
[IMG]http://i869.photobucket.com/albums/ab255/Anorexorcist13/snapshot4.jpg[/IMG]

The [OS] partition is the one that originally had vista on.
If it is not possible to make vista bootable again, is there any chance of recovering my files?

This is an example of what the partition now looks like:
[IMG]http://i869.photobucket.com/albums/ab255/Anorexorcist13/snapshot5.jpg[/IMG]

---

### Post by meierfra. on 2010-02-14
> The [OS] partition is the one that originally had vista on.
If it is not possible to make vista bootable again, is there any chance of recovering my files?
I'm pretty confident that you  will be able to boot Vista again.

At the screen with the results of the  deep search, you can  use the up and down arrow keys  to select a partition and then the "left" and "right" arrow key to change to first column to   "D" (delete), "*" (primary boot),  "P" (primary)  or "L" (logical).

Mark the partition as follows

P  Fat16
D   FAT32 LBA
[COLOR="Red"]D[/COLOR]  HPPS-NTFS
[COLOR="Red"]P[/COLOR]  HPPS-NTFS
*  HPFS-NTFS
L  Linux 
L  Linux  Swap
L  FAT32 LBA


I'm not quite sure about the two partition I marked in red. One of them should have a "D", the other a "P".  Select each of those  partitions and press "p to get a directory listing. If one of them gives you a directory listing mark that one with "P" and the other one with "D".  If both of them or none of them give a directory listing just mark   them the way I did.

Once you marked the partitions press "enter" to continue. On the next screen choose "write" and then follow the instructions on the screen to save the new settings.

Reboot. You will still have to use SuperGrub to boot into Kubuntu.

Once you are back in  Kubuntu, open a terminal and type

```
sudo grub
```

and at the "grub>" prompt

```
root (hd0,4)
setup (hd0)
quit
```
Reboot. You should now get the grub-menu and be able to boot into Vista and Kubuntu.

---

### Post by Anorexorcist on 2010-02-15
Thank you very much for your time and effort, everything is working properly and you have saved me from completely reinstalling kubuntu :)

Sorry if I seemed a bit stupid at times but I dont know a lot about partition recovery.

Thanks again.

---

