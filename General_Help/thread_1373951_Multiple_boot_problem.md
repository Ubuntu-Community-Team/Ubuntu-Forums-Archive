---
title: "Multiple boot problem"
date: 2010-01-06
forum: General Help
---

### Post by arty203 on 2010-01-06
I upgraded from XP to Windows 7 (I need this for legacy business) and decided to install Ubuntu permanently rather than using from CD. During an Ubuntu session I was prompted to upgrade, which I did, but when I boot up now, there seems to be 2 versions of Ubuntu which I can choose from the boot up menu, plus the usual mem test, safe mode etc, plus the option to boot Windows 7.
 
Firstly, is there in fact more than one Ubuntu image (and therefore precious disk space taken up), how do I find out, and if so what action should I take?
 
If there is only one Ubuntu and one Windows 7 image, how do I edit (and where is the file) to change the boot order and the various boot selections?
 
Regards, Roy:confused:

---

### Post by Leppie on 2010-01-06
please run the following command from a terminal and post the generated RESULTS.txt:
```
cd ~/Desktop \
&& wget 'http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.44/boot_info_script044.sh/download' \
&& chmod 755 boot_info_script044.sh \
&& sudo ./boot_info_script044.sh
```

this will help us analyse your system

---

### Post by arty203 on 2010-01-06
Sorry for the delay. the results text is as folows:
 
============================= Boot Info Summary: ==============================
 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdd
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM
sda2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sda5: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   
sdb1: _________________________________________________________________________
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab
sdb2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdb5: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sdd1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sdd2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  
sdd5: _________________________________________________________________________
    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab
sdd6: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf921f921
Partition  Boot         Start           End          Size  Id System
/dev/sda1    *             63   105,097,229   105,097,167   7 HPFS/NTFS
/dev/sda2         105,097,230   156,296,384    51,199,155   f W95 Ext d (LBA)
/dev/sda5         105,097,293   156,296,384    51,199,092   7 HPFS/NTFS

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x81543be3
Partition  Boot         Start           End          Size  Id System
/dev/sdb1                  63    37,351,124    37,351,062  83 Linux
/dev/sdb2          37,351,125    39,070,079     1,718,955   5 Extended
/dev/sdb5          37,351,188    39,070,079     1,718,892  82 Linux swap / Solaris

Drive: sdd ___________________ _____________________________________________________
Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000055d6
Partition  Boot         Start           End          Size  Id System
/dev/sdd1                  63   225,697,184   225,697,122   b W95 FAT32
/dev/sdd2         225,697,185   488,392,064   262,694,880   5 Extended
/dev/sdd5         225,697,248   482,335,559   256,638,312  83 Linux
/dev/sdd6         482,335,623   488,392,064     6,056,442  82 Linux swap / Solaris

blkid -c /dev/null: ____________________________________________________________
sda1: UUID="BC5C293F5C28F634" LABEL="ACL_MAIN" TYPE="ntfs" 
sda5: UUID="C8AC4E6CAC4E555A" LABEL="ACL1500Data" TYPE="ntfs" 
sdb1: UUID="5e963ef4-38d2-445a-ab49-60f08d48b104" TYPE="ext3" 
sdb5: UUID="d984c0b6-959f-40fa-9150-3ff040bf6bef" TYPE="swap" 
sdd1: LABEL="SEA_DISC" UUID="0000-0000" TYPE="vfat" 
sdd5: UUID="183f29f6-05a0-4e87-8a46-ef12b1514c44" TYPE="ext3" 
sdd6: UUID="1645c61e-e169-44a9-9aae-456f7a1cbb28" TYPE="swap" 
=============================== "mount" output: ===============================
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-17-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/roy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=roy)
/dev/sdd1 on /media/SEA_DISC type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdd5 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/ACL_MAIN type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/ACL1500Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

=========================== sdb1/boot/grub/menu.lst: ===========================
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
default  0
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout  10
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
# title  Windows 95/98/NT/2000
# root  (hd0,0)
# makeactive
# chainloader +1
#
# title  Linux
# root  (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=5e963ef4-38d2-445a-ab49-60f08d48b104 ro
## default grub root device
## e.g. groot=(hd0,0)
# groot=5e963ef4-38d2-445a-ab49-60f08d48b104
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
title  Ubuntu 9.04, kernel 2.6.28-17-generic
uuid  5e963ef4-38d2-445a-ab49-60f08d48b104
kernel  /boot/vmlinuz-2.6.28-17-generic root=UUID=5e963ef4-38d2-445a-ab49-60f08d48b104 ro quiet splash 
initrd  /boot/initrd.img-2.6.28-17-generic
quiet
title  Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid  5e963ef4-38d2-445a-ab49-60f08d48b104
kernel  /boot/vmlinuz-2.6.28-17-generic root=UUID=5e963ef4-38d2-445a-ab49-60f08d48b104 ro  single
initrd  /boot/initrd.img-2.6.28-17-generic
title  Ubuntu 9.04, kernel 2.6.27-7-generic
uuid  5e963ef4-38d2-445a-ab49-60f08d48b104
kernel  /boot/vmlinuz-2.6.27-7-generic root=UUID=5e963ef4-38d2-445a-ab49-60f08d48b104 ro quiet splash 
initrd  /boot/initrd.img-2.6.27-7-generic
quiet
title  Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid  5e963ef4-38d2-445a-ab49-60f08d48b104
kernel  /boot/vmlinuz-2.6.27-7-generic root=UUID=5e963ef4-38d2-445a-ab49-60f08d48b104 ro  single
initrd  /boot/initrd.img-2.6.27-7-generic
title  Ubuntu 9.04, memtest86+
uuid  5e963ef4-38d2-445a-ab49-60f08d48b104
kernel  /boot/memtest86+.bin
quiet
### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title  Windows Vista/Longhorn (loader)
root  (hd0,0)
savedefault
makeactive
chainloader +1

=============================== sdb1/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=5e963ef4-38d2-445a-ab49-60f08d48b104 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=d984c0b6-959f-40fa-9150-3ff040bf6bef none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=================== sdb1: Location of files loaded by Grub: ===================

  13.4GB: boot/grub/menu.lst
  13.5GB: boot/grub/stage2
  13.4GB: boot/initrd.img-2.6.27-7-generic
  13.5GB: boot/initrd.img-2.6.28-17-generic
  13.4GB: boot/vmlinuz-2.6.27-7-generic
  13.5GB: boot/vmlinuz-2.6.28-17-generic
  13.5GB: initrd.img
  13.4GB: initrd.img.old
  13.5GB: vmlinuz
  13.4GB: vmlinuz.old
=============================== sdd5/etc/fstab: ===============================
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc5
UUID=183f29f6-05a0-4e87-8a46-ef12b1514c44 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc6
UUID=1645c61e-e169-44a9-9aae-456f7a1cbb28 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
=================== sdd5: Location of files loaded by Grub: ===================

 168.9GB: boot/initrd.img-2.6.27-7-generic
 168.9GB: boot/vmlinuz-2.6.27-7-generic
 168.9GB: initrd.img
 168.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============
sdc

---

### Post by oldfred on 2010-01-06
We recommend that you keep 2 kernels as when a new one is released there can be issues with your specific install. Still having an older kernel lets you choose it and still work. The kernels do not take a lot of space. If you want to houseclean you can go into synaptic and search for linux. It should show your kernels, just be sure not to delete the one you are using.

I would also change this line in menu.lst
# howmany=all
to
# howmany=2

This will always show only two kernels on updates in menu.lst.

I always like to have my system set up to have the MBR of a drive have the boot for the operating system on that drive. That way if one hard drive fails you can change boot order and still boot another system.  I notice you have windows on sda but grub boot for the Ubuntu in sdb. And you have windows boot in sdb and sdd but only have windows in sda. Long term you may want to reinstall grub to sdb and reinstall windows boot loader to sda. You then would have to have sdb as the boot drive in BIOS or as first master if IDE/Pata.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by Leppie on 2010-01-06
Yes, you have 2 different ubuntu installations. 1 hosted on drive sdb (jaunty 9.04) and one on drive sdd (intrepid 8.10).

---

### Post by Leppie on 2010-01-06
the location of the file to edit is sdb1/boot/grub/menu.lst

to change the default choice edit this line:
> default 0

if you want only 1 kernel version to appear in the menu, delete this part:
> title Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid 5e963ef4-38d2-445a-ab49-60f08d48b104
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=5e963ef4-38d2-445a-ab49-60f08d48b104 ro single
initrd /boot/initrd.img-2.6.27-7-generic
title Ubuntu 9.04, memtest86+
uuid 5e963ef4-38d2-445a-ab49-60f08d48b104
kernel /boot/memtest86+.bin
quiet

if you want to delete the older version of ubuntu, format partition sdd5 (it shouldn't be appearing in your grub menu anymore with your current configuration).

---

### Post by arty203 on 2010-01-07
Thanks for the steer. I will keep 2 kernels but tidy things up on the boot screen and change the boot order.
 
I have attempted to edit the 'menu.lst' file but I am unable to save as I do not have the necessary permissions. I have tried to 'save as' with no luck. I have tried to change permissions, but In am not the owner. Can I have steer 2 please;)
 
By the way, I tried chown to my user and chmod 777 but still no luck

---

### Post by oldfred on 2010-01-07
It should be just from a terminal:

just incase have a backup
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
edit with
gksudo gedit /boot/grub/menu.lst

---

### Post by arty203 on 2010-01-08
Perfect:P worked a treat thanks. Before I close this thread how do I change the boot order. I want Windows 7 to be the default.
 
Thanks to al who have given assistance.

---

### Post by Leppie on 2010-01-08
to change the default boot, change the line:
```
default 0
```
the first entry in the menu is 0, count from there on to the entry you want to set as the default.

so if you wanted windows (5th entry) to be the default, the line should be:
```
default 4
```

---

### Post by arty203 on 2010-01-08
All sorted... thanks for your help

---

