---
title: "bootrec /fixmbr overwrote grub"
date: 2010-10-22
forum: General Help
---

### Post by chirag64 on 2010-10-22
I was having troubles with my Windows, so I tried fixing it with the command bootrec /FixMbr. Well, now grub does not show up which means I cannot boot up on Ubuntu. I searched a lot and found out that if I inserted the Live CD, I maybe able to fix it, and i tried installing and running grub from my Ubuntu 9.10 Live CD. But when I tried the commands below, it didn't work, giving me the following errors.
I don't know which partition has the grub records. Any help? :confused:

```
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
grub> find /grub/stage1
find /grub/stage1

Error 15: File not found
```

---

### Post by Quackers on 2010-10-22
You should find all the details you need in this thread. If you are unsure just ask again.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by chirag64 on 2010-10-22
Actually, I'm still not very good with commands and hence, don't understand a lot of stuff posted on that link :-k

Could u plz provide me d command that can fix my problem?!?

---

### Post by Quackers on 2010-10-22
As we don't know your partition layout you should go to the site below and download the boot info script to your desktop. Then run the script with the command shown on that page. This will produce a Results.txt file on your desktop. Please copy the contents of that file and paste them between CODE tags in your next post. (To use CODE tags click on New Reply then on the # in the toolbar and paste in between them).
This will give details of how your partitions are set up. We will then be able to give you specific commands to re-install the grub loader to your system.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by chirag64 on 2010-11-07
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

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
    Boot files/dirs:   /menu.lst

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfa94fa94

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   210,949,514   210,949,452   7 HPFS/NTFS
/dev/sda2         210,949,515   421,899,029   210,949,515   7 HPFS/NTFS
/dev/sda3         421,899,030   632,848,544   210,949,515   7 HPFS/NTFS
/dev/sda4         632,848,606   976,768,064   343,919,459   f W95 Ext d (LBA)
/dev/sda5         632,848,608   843,798,059   210,949,452   7 HPFS/NTFS
/dev/sda6         843,798,123   932,621,444    88,823,322   7 HPFS/NTFS
/dev/sda7         932,621,508   972,655,424    40,033,917  83 Linux
/dev/sda8         972,655,488   976,768,064     4,112,577  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2CCA9596CA955D40                       ntfs                                     
/dev/sda2        067EF8627EF84BC5                       ntfs       Local Disk                    
/dev/sda3        1C9427B794279276                       ntfs                                     
/dev/sda5        24D46934D46908FE                       ntfs                                     
/dev/sda6        F64C95214C94DDA5                       ntfs                                     
/dev/sda7        f248db2c-8039-40e9-a114-a58450c48ded   ext4                                     
/dev/sda8        ed9c8987-bc56-4a45-8ccc-c68e250c5529   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda6/menu.lst: ================================

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
# kopt=root=UUID=a4059b19-e84f-40f5-9203-9c449e195e68 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

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

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=a4059b19-e84f-40f5-9203-9c449e195e68 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=a4059b19-e84f-40f5-9203-9c449e195e68 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd0,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=================== sda6: Location of files loaded by Grub: ===================


 433.8GB: menu.lst

=========================== sda7/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="6"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set f248db2c-8039-40e9-a114-a58450c48ded
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set f248db2c-8039-40e9-a114-a58450c48ded
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f248db2c-8039-40e9-a114-a58450c48ded
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=f248db2c-8039-40e9-a114-a58450c48ded ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f248db2c-8039-40e9-a114-a58450c48ded
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=f248db2c-8039-40e9-a114-a58450c48ded ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f248db2c-8039-40e9-a114-a58450c48ded
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f248db2c-8039-40e9-a114-a58450c48ded ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f248db2c-8039-40e9-a114-a58450c48ded
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f248db2c-8039-40e9-a114-a58450c48ded ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f248db2c-8039-40e9-a114-a58450c48ded
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f248db2c-8039-40e9-a114-a58450c48ded
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 2cca9596ca955d40
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=f248db2c-8039-40e9-a114-a58450c48ded /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=ed9c8987-bc56-4a45-8ccc-c68e250c5529 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


 490.5GB: boot/grub/core.img
 488.9GB: boot/grub/grub.cfg
 491.2GB: boot/initrd.img-2.6.32-24-generic
 491.3GB: boot/initrd.img-2.6.32-25-generic
 490.9GB: boot/vmlinuz-2.6.32-24-generic
 491.3GB: boot/vmlinuz-2.6.32-25-generic
 491.3GB: initrd.img
 491.2GB: initrd.img.old
 491.3GB: vmlinuz
 490.9GB: vmlinuz.old
```

---

### Post by dcstar on 2010-11-07
Do this first and select the Gnome option:
```
sudo dpkg-reconfigure debconf
```
Then:
```
sudo dpkg-reconfigure grub-pc
```

---

### Post by chirag64 on 2010-11-07
The first command worked (I think)

But the second command gave me an error:

```
ubuntu@ubuntu:~$ sudo dpkg-reconfigure grub-pc
Package `grub-pc' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: grub-pc is not installed

```

---

### Post by Quackers on 2010-11-07
Unless dcstar gets back to you with something I will write some commands for you to re-install grub for your particular setup (from drs305's guide).

---

### Post by chirag64 on 2010-11-07
OK...I'll b online from my Live CD till then :)

---

### Post by Quackers on 2010-11-07
I don't think we need to purge grub first, so just copy/paste these lines into a terminal screen - one line at a time and hit enter after each one
```
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

When the second one runs you should get a message saying "completed - no errors" or words like that.
Then reboot and your boot options should be back. If so, check that each of them boots ok.

---

### Post by chirag64 on 2010-11-07
Does this mean it worked correctly?!?

```
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
grub-probe: error: Cannot open `/boot/grub/device.map'
[: 494: =: unexpected operator
    Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda


```

---

### Post by garvinrick4 on 2010-11-07
If you cannot get grub legacy working and booting both Windows and Ubuntu this is grub2 which works.


```
This is going to put lilo in windows to boot from in windows then purge
 grub legacy and install grub2 then update grub2 to add windows to boot config and boot
 menu. Now put Ubuntu install cd in and choose try ubuntu and open a terminal
and copy and paste these in. Applications to Accessories to terminal:
Get your internet connection working in upper right of taskbar:
[CODE]sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```Take out disk should boot into windows: Put disk back in and boot
Choose Try ubuntu and open a terminal and copy and paste these;
    (Make sure you get internet working)


    ```
sudo mkdir /media/sda7
```    ```
sudo mkdir /media/sda7/proc
```    ```
sudo mkdir /media/sda7/dev
```    ```
sudo mkdir /media/sda7/etc
```    ```
sudo mount /dev/sda7 /media/sda7
```    ```
sudo mount -o bind /proc /media/sda7/proc
```    ```
sudo mount -o bind /dev /media/sda7/dev
```    ```
sudo mount -o bind /dev/pts /media/sda7/dev/pts
``````
sudo cp /etc/resolv.conf /media/sda7/etc/resolv.conf
```    ```
sudo chroot /media/sda7
``````
apt-get purge grub grub-common grub-pc
``````
apt-get install grub-common grub-pc
``````
apt-get install-grub --recheck --root-directory=/media/sda7 /dev/sda
``````
 update-grub
``` Hit ctrl/d   ```
sudo umount /media/sda7/dev
```    ```
sudo umount /media/sda7/proc
```    ```
sudo umount /media/sda7/etc
```    ```
sudo umount /media/sda7
```Now boot back into harddrive into Ubuntu and for good measure.



    ```
sudo update-grub
```[/CODE]-
Here is a link about removing grub legacy and installing grub2 when chrooting into your install:
A little different but accomplishs same thing and explained well. Right now yours is in a bit of a mess.
grub legacy and grub2 do not get along real well. I prefer grub2 and it is now Ubuntu's choice of grub.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Quackers on 2010-11-07
Never seen that! Try rebooting and see if it works. If not we can purge then re-install. 
I don't know what the bios query is!

---

### Post by chirag64 on 2010-11-07
I think I had grub2...and I don't think what Quackers said worked, coz now I just get a grub console, no booting options :(

---

### Post by Quackers on 2010-11-07
Oh dear, that's not good. I think that should have worked for you.
garvinrick4 has already written instructions for installing Lilo and purging and re-installing grub2 to your system. It is written for your system. It may be the next move for you.
I have reservations about that bios message (unless it just refers to having a floppy disc in the boot priority - not sure).
Good luck to you :-)

---

### Post by Quackers on 2010-11-07
> **chirag64 said:**
> I think I had grub2...and I don't think what Quackers said worked, coz now I just get a grub console, no booting options :(

You had grub2 boot files on sda5 but you had a grub file in one of the partitions and your original error message was a grub message (not a grub2 message).
On reflection I think purging and re-installing grub2 will work.

I'm not sure about Lilo being necessary though.

---

### Post by chirag64 on 2010-11-07
I tried the instructions on [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) this link and still I keep getting the grub console only :(

---

### Post by garvinrick4 on 2010-11-07
> **Quackers said:**
> You had grub2 boot files on sda5 but you had a grub file in one of the partitions and your original error message was a grub message (not a grub2 message).
On reflection I think purging and re-installing grub2 will work.

I'm not sure about Lilo being necessary though. I like to get Windows on the strait and narrow and booting before I get grub2 installed. Just to clean up Windows a bit.
Either using Windows install disk or lilo. These grub-legacy and grub2 combined are a bit
more touchy for me so I do what has worked for me in past and whats 2 more commands. No mixed grub would pass on the lilo.
Hopefully it works and OP is off and running.

---

### Post by garvinrick4 on 2010-11-07
> **chirag64 said:**
> I tried the instructions on [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099) this link and still I keep getting the grub console only :( Give my code a quick copy and paste nothing to lose do you.

---

### Post by chirag64 on 2010-11-07
OK, I had not tried the commands on that link correctly earlier. I tried them again and voila, it worked!!! :)

Thnx a lot for all ur help, Ubuntu geeks :D

I guess all I had to do was install grub2 on the partition!!!

```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
```

---

### Post by garvinrick4 on 2010-11-07
Grub2 is in a partition of Linux and it is installed in the mbr (master boot record)
from that partition. In sda looking for files in sda7. mbr is always in sda or if second drive sdb or third drive in order sdc.  Do you see what I mean. Pretty simple really if you think about it. Grub2 comes with and os-prober that go's out and looks for other operating systems to put in grub2 so they may get in boot menu and in configurtation files and you can then boot multiple operating systems. It happens when you tell it to. 2 Ways:
```
sudo update-grub
``````
sudo grub-mkconfig
```Everytime you change grub2 or mess with files run one of them. The first is the more
accepted now, so use it.

---

### Post by Quackers on 2010-11-07
> **garvinrick4 said:**
> I like to get Windows on the strait and narrow and booting before I get grub2 installed. Just to clean up Windows a bit.
Either using Windows install disk or lilo. These grub-legacy and grub2 combined are a bit
more touchy for me so I do what has worked for me in past and whats 2 more commands. No mixed grub would pass on the lilo.
Hopefully it works and OP is off and running.

:-) Windows was booting. The OP fixed the mbr - that's where the problems started :-)

Nice result chirag64. Enjoy! :-)

Will you mark the thread as solved please, so that others searching for answers can see. Thanks :-)

---

