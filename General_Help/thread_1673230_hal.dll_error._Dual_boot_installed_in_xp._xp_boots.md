---
title: "hal.dll error. Dual boot installed in xp. xp boots ubuntu won't"
date: 2011-01-22
forum: General Help
---

### Post by harshalizee on 2011-01-22
I had installed Ubuntu 9.10 inside Windows. It was working fine until a couple of days ago. I now get an error message saying hal.dll is missing/corrupted. But WinXP boots just fine, only ubuntu gives me this error. Please help!

---

### Post by Rubi1200 on 2011-01-23
Hi and welcome to the forums :)

Are you able to boot into Ubuntu?

The error you describe is normally associated with not being able to boot Windows?

Please provide us with more information.

---

### Post by harshalizee on 2011-01-23
The other way around actually. Windows boots fine with no problem. The error occurs only when I select Ubuntu.It does not boot into Ubuntu, but gives me the hal.dll error. I'm new to using ubuntu. Can you please specify exactly what information you will need to help me.
 Thank You!

---

### Post by Rubi1200 on 2011-01-23
I understood from your first post what you meant. I am just a bit surprised since this kind of error normally means you are unable to boot into Windows rather than Ubuntu having a problem.

Okay, so here is what I suggest:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

The results will hopefully show us where there is a problem.

---

### Post by harshalizee on 2011-01-24
Here you go...
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

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
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda7/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d281d27

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sda2          81,915,435   625,137,344   543,221,910   f W95 Ext d (LBA)
/dev/sda5          81,915,498   163,830,869    81,915,372   7 HPFS/NTFS
/dev/sda6         163,830,933   389,110,364   225,279,432   7 HPFS/NTFS
/dev/sda7         389,110,428   625,137,344   236,026,917   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       b8e507ef-0673-435e-842c-53c8917480d1   ext4                                     
/dev/sda1        F6A8B5BAA8B57A27                       ntfs                                     
/dev/sda5        B6F0A24DF0A213A1                       ntfs       Programs                      
/dev/sda6        9A6CAAC56CAA9B8F                       ntfs       Games                         
/dev/sda7        3400B02F00AFF650                       ntfs       MyStuff                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda5        /media/Programs          fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

======================== sda7/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
    insmod ntfs
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 3400b02f00aff650
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-22-generic root=/dev/sda7 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 3400b02f00aff650
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-22-generic root=/dev/sda7 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod ntfs
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 3400b02f00aff650
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda7 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod ntfs
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 3400b02f00aff650
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda7 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f6a8b5baa8b57a27
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda7/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sda7/Wubi: Location of files loaded by Grub: =================


   1.2GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.31-14-generic
   3.7GB: boot/initrd.img-2.6.31-22-generic
   2.3GB: boot/vmlinuz-2.6.31-14-generic
   1.7GB: boot/vmlinuz-2.6.31-22-generic
   3.7GB: initrd.img
    .8GB: initrd.img.old
   1.7GB: vmlinuz
   2.3GB: vmlinuz.old

```

Ubuntu is installed in the F: drive inside windows.
Is there anything else you need. Thank You, I appreciate the help.

---

### Post by Rubi1200 on 2011-01-24
Hi and thanks for the results.

So, this is what we need to know:
do you have the /wubildr and /wubildr.mbr files on C? They should be at the root of the C drive (sda1 in the script)

If not, then do this:
Just copy these from /dev/sda7 (which appears to be the F drive you mentioned) over to C:\

If it's 9.10 and you need the wubildr file, you can get it from here: [http://sourceforge.net/apps/mediawik...lems:Wubi_9.10]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10")

---

### Post by harshalizee on 2011-01-24
Thank You Rubi1200! You're awesome!  It was missing the wubildr files from C:\ and is apparently quite a frequent problem for wubi installed ubuntu. Thanks for all the help. Any idea why this occurs and how I can prevent this.

---

### Post by Rubi1200 on 2011-01-24
You are more than welcome :)

Really glad you got it sorted out.

As to the exact reason, I am not sure. Just make sure that those 2 files always stay on C:\ and it should be all good.

Also, full credit goes to forum member bcbc who pointed me in the right direction with this issue.

Please mark this thread Solved using the Thread Tools near the top of the page. This way, other users in a similar situation will have a working solution to assist them.

---

