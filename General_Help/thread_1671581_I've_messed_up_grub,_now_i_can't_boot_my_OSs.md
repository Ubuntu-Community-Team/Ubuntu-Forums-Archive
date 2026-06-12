---
title: "I've messed up grub, now i can't boot my OSs"
date: 2011-01-20
forum: General Help
---

### Post by oopsie on 2011-01-20
I've tried the instructions here
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

But I couldn't get that to work.

Anyone know what I can do?

---

### Post by ajgreeny on 2011-01-20
How did you mess up grub and what happens when you try to boot?

If you have edited the various grub files in **/etc/default/grub** and some of those in **/etc/grub.d/00_header,  05_debian_theme,  10_linux,  20_memtest86+,  30_os-prober,  **or** 40_custom, **reinstalling grub will not help as you will still have those incorrect configuration files which grub uses.

---

### Post by decrepit on 2011-01-20
you need to post your version of ubuntu. grub changed to version 2 recently, and is very different to version 1

---

### Post by oopsie on 2011-01-20
> **ajgreeny said:**
> How did you mess up grub and what happens when you try to boot?

If you have edited the various grub files in **/etc/default/grub** and some of those in **/etc/grub.d/00_header,  05_debian_theme,  10_linux,  20_memtest86+,  30_os-prober,  **or** 40_custom, **reinstalling grub will not help as you will still have those incorrect configuration files which grub uses.

I was installing a different distro of Linux to try out. Since it was on a different drive to Ubuntu and it promised not to touch any other drives, I thought it would be safe. I was wrong.

This is what happens when I try to boot
[http://img691.imageshack.us/img691/7906/desktopyj.jpg](http://img691.imageshack.us/img691/7906/desktopyj.jpg)

> 
you need to post your version of ubuntu. grub changed to version 2 recently, and is very different to version 1

10.10

---

### Post by sanderd17 on 2011-01-20
If you have some space over, you can always install a second ubuntu. 10GB will do.

the new ubuntu will install a newer grub which points also to your older OSes.

You can also reinstall grub without ubuntu, but if you have more space, it's safer to install a new ubuntu. That way you won't have to do things in your current installation.

---

### Post by sanderd17 on 2011-01-20
> **oopsie said:**
> I was installing a different distro of Linux to try out. Since it was on a different drive to Ubuntu and it promised not to touch any other drives, I thought it would be safe. I was wrong.

This is what happens when I try to boot
[http://img691.imageshack.us/img691/7906/desktopyj.jpg](http://img691.imageshack.us/img691/7906/desktopyj.jpg)



10.10

Oh, I didn't read that

So the other distro put his grub on it. There is a big chance (if it's a slightly older distro) that it doesn't know about ext4 and therefore didn't find ubuntu. Just install a newer distro instead of the one you tried to install and it will be all right.

---

### Post by coffeecat on 2011-01-20
Boot up with a live CD, make sure you are connected to the internet and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file **in code tags for legibility**. You can use the # icon on the message toolbar for this. 

That will tell us what is on your machine and what is needed for you to be able to repair your Ubuntu grub. Once you've done that it is easy to modify Ubuntu's grub menu to include any other OSs you have subsequently installed.

---

### Post by ajgreeny on 2011-01-20
There should be no need to reinstall the system or add another OS just to get grub working again!!

Ubuntu 9.10 and later use Grub 2, so you need to find out what is on your drives using the terminal in live CD:
   ```
 sudo fdisk -l
```
From that you need to find the device name of your Ubuntu partition/drive, something like “/dev/sda5&#8243;.
Still in the terminal, type:
    ```
sudo mkdir /media/sda5
    sudo mount /dev/sda5 /media/sda5
```
To reinstall grub:
    ```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```
Push enter and you’re done! Of course you need to replace “/dev/sda5&#8243; and “/dev/sda” with what you found in the fdisk output.

---

### Post by oopsie on 2011-01-20
> **coffeecat said:**
> Boot up with a live CD, make sure you are connected to the internet and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script and post the RESULTS.txt file **in code tags for legibility**. You can use the # icon on the message toolbar for this. 

That will tell us what is on your machine and what is needed for you to be able to repair your Ubuntu grub. Once you've done that it is easy to modify Ubuntu's grub menu to include any other OSs you have subsequently installed.

I've installed a lot of different distros over the months. Looking over the output of the script, looks like I've manage to really mix some things up.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 14 (Laughlin) 
                       Kernel on an ()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sdb2: _________________________________________________________________________

    File system:       crypto_LUKS
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'crypto_LUKS'

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1         621,142,016   625,141,759     3,999,744  82 Linux swap / Solaris
/dev/sda2    *          2,047   621,142,015   621,139,969   5 Extended
/dev/sda5               2,048    97,656,831    97,654,784  83 Linux
/dev/sda6          97,658,880   621,142,015   523,483,136  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 27.3 GB, 27325218816 bytes
255 heads, 63 sectors/track, 3322 cylinders, total 53369568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    20,482,047    20,480,000  83 Linux
/dev/sdb2          20,482,048    53,368,831    32,886,784  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    13,671,314    13,671,252  83 Linux
/dev/sdc2          13,671,315   160,071,659   146,400,345   5 Extended
/dev/sdc5          13,671,378    19,695,689     6,024,312  82 Linux swap / Solaris
/dev/sdc6          19,695,753   160,071,659   140,375,907  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        dbb3c001-fc4f-4f79-bd55-7186f7a7a8ca   swap                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        bd203549-28cf-4411-852a-f7aa85b1af20   ext4                                     
/dev/sda6        e412d3d3-0e72-46c4-93bb-144f3c68e979   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c05eb533-d255-445d-98ec-d12f29ddad2c   ext4       _Fedora-14-x86_6              
/dev/sdb2        2e03ab70-21de-4282-9f68-7d4d3a0427bf   crypto_LUKS                               
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        873ede01-3682-4474-ad2a-63ff996de1d8   ext3                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5                                               swap                                     
/dev/sdc6        1091c7a7-f2b8-4dcd-96fe-596d27697e83   ext3                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set bd203549-28cf-4411-852a-f7aa85b1af20
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set bd203549-28cf-4411-852a-f7aa85b1af20
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set bd203549-28cf-4411-852a-f7aa85b1af20
insmod png
if background_image /usr/share/images/desktop-base/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bd203549-28cf-4411-852a-f7aa85b1af20
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=bd203549-28cf-4411-852a-f7aa85b1af20 ro nomodeset  quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bd203549-28cf-4411-852a-f7aa85b1af20
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=bd203549-28cf-4411-852a-f7aa85b1af20 ro single nomodeset
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bd203549-28cf-4411-852a-f7aa85b1af20
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=bd203549-28cf-4411-852a-f7aa85b1af20 ro nomodeset  quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bd203549-28cf-4411-852a-f7aa85b1af20
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=bd203549-28cf-4411-852a-f7aa85b1af20 ro single nomodeset
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bd203549-28cf-4411-852a-f7aa85b1af20
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=bd203549-28cf-4411-852a-f7aa85b1af20 ro nomodeset  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bd203549-28cf-4411-852a-f7aa85b1af20
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=bd203549-28cf-4411-852a-f7aa85b1af20 ro single nomodeset
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bd203549-28cf-4411-852a-f7aa85b1af20
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bd203549-28cf-4411-852a-f7aa85b1af20
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Fedora (2.6.35.6-45.fc14.x86_64) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set c05eb533-d255-445d-98ec-d12f29ddad2c
    linux /boot/vmlinuz-2.6.35.6-45.fc14.x86_64 ro root=UUID=c05eb533-d255-445d-98ec-d12f29ddad2c rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=uk rhgb quiet
    initrd /boot/initramfs-2.6.35.6-45.fc14.x86_64.img
}
menuentry "Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sdc1) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 4f11960a-361e-4a10-9bcf-697c1928fa1f
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=4f11960a-361e-4a10-9bcf-697c1928fa1f ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Linux Mint 10 64-bit, 2.6.35-22-generic (/dev/sdc1) -- recovery mode (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set 4f11960a-361e-4a10-9bcf-697c1928fa1f
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=4f11960a-361e-4a10-9bcf-697c1928fa1f ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda5       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=e412d3d3-0e72-46c4-93bb-144f3c68e979 /home           ext4    defaults        0       2
/dev/sda1       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  39.0GB: boot/grub/core.img
  15.2GB: boot/grub/grub.cfg
   2.8GB: boot/initrd.img-2.6.35-22-generic
   1.5GB: boot/initrd.img-2.6.35-23-generic
   2.9GB: boot/initrd.img-2.6.35-24-generic
  39.0GB: boot/vmlinuz-2.6.35-22-generic
  39.1GB: boot/vmlinuz-2.6.35-23-generic
  39.2GB: boot/vmlinuz-2.6.35-24-generic
   2.9GB: initrd.img
   1.5GB: initrd.img.old
  39.2GB: vmlinuz
  39.1GB: vmlinuz.old

=================== sda6: Location of files loaded by Grub: ===================


 116.7GB: boot/grub/core.img

========================== sdb1/boot/grub/grub.conf: ==========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,0)
#          kernel /boot/vmlinuz-version ro root=/dev/sda1
#          initrd /boot/initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=0
splashimage=(hd0,0)/boot/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.35.10-74.fc14.x86_64)
    root (hd0,0)
    kernel /boot/vmlinuz-2.6.35.10-74.fc14.x86_64 ro root=UUID=c05eb533-d255-445d-98ec-d12f29ddad2c rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=uk rhgb quiet
    initrd /boot/initramfs-2.6.35.10-74.fc14.x86_64.img
title Fedora (2.6.35.6-45.fc14.x86_64)
    root (hd0,0)
    kernel /boot/vmlinuz-2.6.35.6-45.fc14.x86_64 ro root=UUID=c05eb533-d255-445d-98ec-d12f29ddad2c rd_NO_LUKS rd_NO_LVM rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=uk rhgb quiet
    initrd /boot/initramfs-2.6.35.6-45.fc14.x86_64.img

=============================== sdb1/etc/fstab: ===============================


#
# /etc/fstab
# Created by anaconda on Tue Jan 18 10:22:14 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=c05eb533-d255-445d-98ec-d12f29ddad2c /                       ext4    defaults        1 1
/dev/mapper/luks-2e03ab70-21de-4282-9f68-7d4d3a0427bf /home                   ext4    defaults        1 2
UUID=dbb3c001-fc4f-4f79-bd55-7186f7a7a8ca swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0

=================== sdb1: Location of files loaded by Grub: ===================


    .1GB: boot/grub/grub.conf
    .1GB: boot/grub/menu.lst
    .1GB: boot/grub/stage2
   3.3GB: boot/initramfs-2.6.35.10-74.fc14.x86_64.img
   2.2GB: boot/initramfs-2.6.35.6-45.fc14.x86_64.img
   3.0GB: boot/initrd-plymouth.img
   2.8GB: boot/vmlinuz-2.6.35.10-74.fc14.x86_64
   1.6GB: boot/vmlinuz-2.6.35.6-45.fc14.x86_64

=========================== sdc1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

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

title        Debian GNU/Linux, kernel 2.6.26-2-amd64
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.26-2-amd64 root=/dev/hdb1 ro quiet
initrd        /boot/initrd.img-2.6.26-2-amd64

title        Debian GNU/Linux, kernel 2.6.26-2-amd64 (single-user mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.26-2-amd64 root=/dev/hdb1 ro single
initrd        /boot/initrd.img-2.6.26-2-amd64

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    errors=remount-ro 0       1
/dev/hdb6       /home           ext3    defaults        0       2
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .8GB: boot/grub/core.img
    .8GB: boot/grub/menu.lst
    .8GB: boot/grub/stage2
    .9GB: boot/initrd.img-2.6.26-2-amd64
    .8GB: boot/initrd.img-2.6.26-2-amd64.bak
    .9GB: boot/vmlinuz-2.6.26-2-amd64
    .9GB: initrd.img
    .9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  4c 55 4b 53 ba be 00 01  61 65 73 00 00 00 00 00  |LUKS....aes.....|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  00 00 00 00 00 00 00 00  78 74 73 2d 70 6c 61 69  |........xts-plai|
00000030  6e 36 34 00 00 00 00 00  00 00 00 00 00 00 00 00  |n64.............|
00000040  00 00 00 00 00 00 00 00  73 68 61 31 00 00 00 00  |........sha1....|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000060  00 00 00 00 00 00 00 00  00 00 0f c8 00 00 00 40  |...............@|
00000070  18 94 14 51 78 98 05 ff  5a af e1 cc 76 a7 4c 0a  |...Qx...Z...v.L.|
00000080  d7 05 5f 23 c3 89 fe b4  ef 84 4e 05 1f e2 a4 5f  |.._#......N...._|
00000090  96 3a 92 28 f5 3a 8d e4  e9 ed 7e af a8 e0 65 21  |.:.(.:....~...e!|
000000a0  33 6f 3a 12 00 00 64 96  32 65 30 33 61 62 37 30  |3o:...d.2e03ab70|
000000b0  2d 32 31 64 65 2d 34 32  38 32 2d 39 66 36 38 2d  |-21de-4282-9f68-|
000000c0  37 64 34 64 33 61 30 34  32 37 62 66 00 00 00 00  |7d4d3a0427bf....|
000000d0  00 ac 71 f3 00 01 93 b3  2b 56 07 2a 3f 96 ca 83  |..q.....+V.*?...|
000000e0  da df 56 31 29 89 ec 4e  ed 95 68 9c 17 50 80 48  |..V1)..N..h..P.H|
000000f0  e4 77 61 3a 02 d2 74 bc  00 00 00 08 00 00 0f a0  |.wa:..t.........|
00000100  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 00 00 00 00 00 00  00 00 02 00 00 00 0f a0  |................|
00000130  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000150  00 00 00 00 00 00 00 00  00 00 03 f8 00 00 0f a0  |................|
00000160  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 05 f0 00 00 0f a0  |................|
00000190  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  00 00 07 e8 00 00 0f a0  |................|
000001c0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 09 e0 00 00 0f a0  |................|
000001f0  00 00 de ad 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

```

---

### Post by coffeecat on 2011-01-20
> **oopsie said:**
> I've installed a lot of different distros over the months. Looking over the output of the script, looks like I've manage to really mix some things up.

It should be repairable. Ubuntu 10.10 is on sda5 and its fstab and grub.cfg look OK to boot itself at least. The bootscript says you have Debian 5 on sdc1 whereas your Ubuntu grub.cfg refers to Mint10 on that partition. Whatever - the link you posted in you first post is the one you need, but you didn't say what commands you used. The following *ought* to work.

Boot up with the live Ubuntu CD, open a terminal, and:

```
sudo mount /dev/sda5 /mnt
```Now...

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```Now try rebooting. If you can boot into Ubuntu, do so and once you're logged in, open a terminal and:

```
sudo update-grub
```That will regenerate grub to show all your installed OSs.

---

### Post by oopsie on 2011-01-20
I tried that before with no success. And at first it didn't work now either. But since you're sure it was right, I decided to play about with my hard drive boot order in BIOS.

That fixed it. Thank you very much for your time, It's working now.

---

### Post by coffeecat on 2011-01-20
> **oopsie said:**
> I decided to play about with my hard drive boot order in BIOS.

That's often the confounding factor. I'm glad you've fixed it.

---

