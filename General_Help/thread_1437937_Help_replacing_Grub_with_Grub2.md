---
title: "Help replacing Grub with Grub2"
date: 2010-03-24
forum: General Help
---

### Post by whalogreg on 2010-03-24
I recently decided to try out Fedora 12 (which uses Grub, not Grub2) along side my Ubuntu 9.10 which does use Grub2, and Windows 7 (yuck). I would like to use Grub2 to boot (Fedora's Grub does not recognise my 9.10 install). I've searched for a way to simply remove Grub, but have only found ways to remove it by using "the Windows fix" (fdisk /mbr or something similar) which I do not want to do, and I do not want to modify Grub's menu.lst, I just want it gone and to install Grub2. I am most likely going to remove Fedora soon anyway. Any help?

---

### Post by oldfred on 2010-03-24
You just need to restore the 9.10 grub bootloader just like when windows overwrites the MBR. Besure to follow the direction for grub2 and know which partition is your Ubuntu install.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by 2hot6ft2 on 2010-03-24
Using Ubuntu 9.10 livecd

Here assuming the Ubuntu partition is sda8,and /boot partition is sda6 (if you have a separate /boot partition).

Boot up ubuntu from the livecd, open a terminal and run:

```
sudo -i
```
To find out what your partitions are run
```
fdisk -l
```
then using that info run these using the 9.10 installs partition, don't even bother mounting Fedoras partition
```
mount /dev/sda8 /mnt
```
```
mount /dev/sda6 /mnt/boot  #skip this one if not have a separate /boot partition
```
```
grub-install --root-directory=/mnt/ /dev/sda
```
Reboot into 9.10 and run
```
sudo update-grub
```

From the Grub 2 Guide link in my sig.

---

### Post by whalogreg on 2010-03-24
I tried both. Both got me to a grub prompt, not the Boot Menu.. 

this was my output from fdisk -l...

"Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1447fed5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
/dev/sda2            1306       28695   220001203    7  HPFS/NTFS
/dev/sda3           28696       60801   257891445    5  Extended
/dev/sda5           28696       43736   120814592   83  Linux
/dev/sda6           59496       60801    10490413+  82  Linux swap / Solaris
/dev/sda7   *       43736       43762      204799+  83  Linux
/dev/sda8           43762       57529   110584831+  8e  Linux LVM

Partition table entries are not in disk order"


this means my Ubuntu partition is sda5 and my boot partition is sda7, correct?

---

### Post by andrewthomas on 2010-03-24
> **whalogreg said:**
> 
this was my output from fdisk -l...

"Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1447fed5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1306    10485760   27  Unknown
/dev/sda2            1306       28695   220001203    7  HPFS/NTFS
/dev/sda3           28696       60801   257891445    5  Extended
/dev/sda5           28696       43736   120814592   83  Linux
/dev/sda6           59496       60801    10490413+  82  Linux swap / Solaris
/dev/sda7   *       43736       43762      204799+  83  Linux
/dev/sda8           43762       57529   110584831+  8e  Linux LVM

Partition table entries are not in disk order"


this means my Ubuntu partition is sda5 and my boot partition is sda7, correct?
Which did you install first Ubuntu or Fedora?  It seems to me that
/dev/sda5 is probably your Ubuntu /  
/dev/sda7 is your Fedora /boot 
/dev/sda8 is your Fedora /

---

### Post by whalogreg on 2010-03-24
I installed Ubuntu first. Would that mean that Fedora's boot partition is like you said, sda7 and Ubuntu's is on it's same partition? That might have been my mistake...

---

### Post by andrewthomas on 2010-03-24
> **whalogreg said:**
> I installed Ubuntu first. Would that mean that Fedora's boot partition is like you said, sda7 and Ubuntu's is on it's same partition? That might have been my mistake...
If you just did a default install of Ubuntu, then the /boot is on the /.

---

### Post by oldfred on 2010-03-24
If you do not know what is where post this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by whalogreg on 2010-03-24
> **andrewthomas said:**
> If you just did a default install of Ubuntu, then the /boot is on the /.

I ran what 2hot6ft2 suggested with that in mind, and I got Grub2 to work properly, but unfortunately when I choose to load Ubuntu, it brings me to the user login screen (without showing the splash screen before). The login screen appears to load without the default karmic theme, and when I try to login, it reloads the login screen...  


> **oldfred said:**
> If you do not know what is where post this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.


Here is the output of the Boot Info Script

#                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub is installed in the boot sector of sda1 and looks 
                       at sector 489397311 of the same hard drive for the 
                       stage2 file, but no stage2 files can be found at this 
                       location.
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda5 and 
                       looks at sector 697701782 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf /grub/core.img 
                       /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1447fed5

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2          20,973,568   460,975,973   440,002,406   7 HPFS/NTFS
/dev/sda3         460,985,175   976,768,064   515,782,890   5 Extended
/dev/sda5         460,985,238   702,614,421   241,629,184  83 Linux
/dev/sda6         955,787,238   976,768,064    20,980,827  82 Linux swap / Solaris
/dev/sda7    *    702,614,423   703,024,021       409,599  83 Linux
/dev/sda8         703,024,023   924,193,685   221,169,663  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        5CC67E52C67E2D00                       ntfs       OS                            
/dev/sda5        956cce0d-c0a3-43e9-902b-682b5e2a70e8   ext4                                     
/dev/sda6        a639e263-6f41-4d1a-81c5-adbd09eceec8   swap                                     
/dev/sda7        12888dd2-cc87-45a9-92f2-a2069693fc97   ext4                                     
/dev/sda8        ljjrP7-0OMk-KSQH-esBT-sUit-0EuT-hbPyy3 LVM2_member                               

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="0"
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 956cce0d-c0a3-43e9-902b-682b5e2a70e8
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 956cce0d-c0a3-43e9-902b-682b5e2a70e8
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-16-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 956cce0d-c0a3-43e9-902b-682b5e2a70e8
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=956cce0d-c0a3-43e9-902b-682b5e2a70e8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.32-16-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 956cce0d-c0a3-43e9-902b-682b5e2a70e8
	echo	Loading Linux 2.6.32-16-generic ...
	linux	/boot/vmlinuz-2.6.32-16-generic root=UUID=956cce0d-c0a3-43e9-902b-682b5e2a70e8 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.32-16-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 956cce0d-c0a3-43e9-902b-682b5e2a70e8
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=956cce0d-c0a3-43e9-902b-682b5e2a70e8 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 956cce0d-c0a3-43e9-902b-682b5e2a70e8
	echo	Loading Linux 2.6.31-20-generic ...
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=956cce0d-c0a3-43e9-902b-682b5e2a70e8 ro single 
	echo	Loading initial ramdisk ...
	initrd	/boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 956cce0d-c0a3-43e9-902b-682b5e2a70e8
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 956cce0d-c0a3-43e9-902b-682b5e2a70e8
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 5cc67e52c67e2d00
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=956cce0d-c0a3-43e9-902b-682b5e2a70e8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a639e263-6f41-4d1a-81c5-adbd09eceec8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 238.3GB: boot/grub/core.img
 261.4GB: boot/grub/grub.cfg
 357.2GB: boot/grub/stage2
 237.4GB: boot/initrd.img-2.6.31-20-generic
 237.6GB: boot/initrd.img-2.6.32-16-generic
 246.8GB: boot/vmlinuz-2.6.31-20-generic
 237.4GB: boot/vmlinuz-2.6.32-16-generic
 237.6GB: initrd.img
 237.4GB: initrd.img.old
 237.4GB: vmlinuz
 246.8GB: vmlinuz.old

============================= sda7/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,6)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_greg-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=15
splashimage=(hd0,6)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.31.5-127.fc12.x86_64)
	root (hd0,6)
	kernel /vmlinuz-2.6.31.5-127.fc12.x86_64 ro root=/dev/mapper/vg_greg-lv_root  LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
	initrd /initramfs-2.6.31.5-127.fc12.x86_64.img
title Other
	rootnoverify (hd0,1)
	chainloader +1

=================== sda7: Location of files loaded by Grub: ===================


 359.7GB: boot/grub/core.img
 359.7GB: grub/core.img
 359.7GB: grub/grub.conf
 359.7GB: grub/menu.lst
 359.7GB: grub/stage2
 359.7GB: initramfs-2.6.31.5-127.fc12.x86_64.img
 359.7GB: vmlinuz-2.6.31.5-127.fc12.x86_64
#

---

### Post by oldfred on 2010-03-24
The script says you are using grub2 to boot sda5 which is lucid, the beta which may have issues and is for testing. Is that what you want and have you checked to see if your problem with the beta is a common one.

---

