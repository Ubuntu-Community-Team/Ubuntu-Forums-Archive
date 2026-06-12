---
title: "Messed up MBR/GRUB"
date: 2010-12-19
forum: General Help
---

### Post by Howy on 2010-12-19
I'll put this short: I messed up the MBR or GRUB completely.
This is what I did: I was trying to make my Windows-partition work, and it most probably erased my MBR for Linux.
The bootloader said: "Error in master boot record"
Then, I followed a guide to restore the MBR for GRUB2. (I use GRUB2, BTW.)
And now... I get a flashing underline only. It flashes abnormally, though.
Sooo... any advice for what I should do?
I really don't have any idea what I can do about it. I have a liveDVD for Ubuntu 10.04 inside now, while my main OS is using 10.10.
I would only consider reinstalling as the last option, and I guess i won't have to if  I listen to some professionals, and I consider you as the professionals.
What should I do?:confused:

---

### Post by sikander3786 on 2010-12-19
Boot an Ubuntu Live CD/USB and post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It would give us a complete overview of your setup and Grub and thus help diagnose the problem.

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by Howy on 2010-12-19
Here's the RESULTS.TXT-file:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => HP/Gateway is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   493,629,254   493,629,192  83 Linux
/dev/sda2         493,631,486 1,953,523,711 1,459,892,226   5 Extended
/dev/sda5         976,762,880 1,943,758,847   966,995,968  83 Linux
/dev/sda6       1,943,760,896 1,953,523,711     9,762,816  82 Linux swap / Solaris
/dev/sda7    *    493,631,488   957,100,031   463,468,544  83 Linux
/dev/sda8         957,102,080   976,752,639    19,650,560  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   377,061,614   377,061,552   7 HPFS/NTFS
/dev/sdb2         377,077,680   390,716,864    13,639,185   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b3e7fc6a-d673-4267-ba60-d8285551b832   ext4       Backup                        
/dev/sda2: PTTYPE="dos" 
/dev/sda5        bd3d1b40-04cf-4eab-9a40-8a43793a4e1c   ext4       Lagring                       
/dev/sda6        aa1b84e3-2859-4842-939d-2d773b057883   swap                                     
/dev/sda7        05042069-be03-441a-adaf-07c61f0f579b   ext4                                     
/dev/sda8        c6874d5e-24fe-4d38-b45c-c3cc131fa556   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2BA95E1E14F9018F                       ntfs       PRESARIO                      
/dev/sdb2        4B6E-6BC0                              vfat       PRESARIO_RP                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda7        /media/05042069-be03-441a-adaf-07c61f0f579b ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /media/Lagring           ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/Backup            ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
set locale_dir=($root)/boot/grub/locale
set lang=nb
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=05042069-be03-441a-adaf-07c61f0f579b ro  vga=792 splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=05042069-be03-441a-adaf-07c61f0f579b ro single  vga=792 splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=05042069-be03-441a-adaf-07c61f0f579b ro  vga=792 splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=05042069-be03-441a-adaf-07c61f0f579b ro single  vga=792 splash
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 05042069-be03-441a-adaf-07c61f0f579b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 2ba95e1e14f9018f
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sdb2)" {
    insmod part_msdos
    insmod fat
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 4b6e-6bc0
    drivemap -s (hd0) ${root}
    chainloader +1
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda7 during installation
UUID=05042069-be03-441a-adaf-07c61f0f579b  /               ext4  errors=remount-ro    0  1  
# swap was on /dev/sda8 during installation
UUID=c6874d5e-24fe-4d38-b45c-c3cc131fa556  none            swap  sw                   0  0  
/dev/sda1                                  /media/Backup   ext4  defaults             0  0  
/dev/sda5                                  /media/Lagring  ext4  defaults             0  0  

=================== sda7: Location of files loaded by Grub: ===================


 476.2GB: boot/grub/core.img
 259.5GB: boot/grub/grub.cfg
 253.8GB: boot/initrd.img-2.6.35-22-generic
 301.1GB: boot/initrd.img-2.6.35-23-generic
 476.9GB: boot/vmlinuz-2.6.35-22-generic
 477.4GB: boot/vmlinuz-2.6.35-23-generic
 301.1GB: initrd.img
 253.8GB: initrd.img.old
 477.4GB: vmlinuz
 476.9GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=3 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /noguiboot 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

================================ sdb2/boot.ini: ================================

[boot loader] 
timeout=15 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
```I consider taking out that Windows-HDD after this is over...

---

### Post by sikander3786 on 2010-12-19
Everything seems fine. Go to your Bios menu and make your sda i.e, Ubuntu Drive, the first boot device. Once you boot successfully from that drive, Grub menu should also give you an option to boot Windows XP from the other HDD as grub.cfg has got entries for Windows.

Check the boot order and let us know how that goes.

Good Luck!

---

### Post by Howy on 2010-12-19
It still won't show up... :(
I set the boot-order to have the HDD first, but it's still that flashing underline. It doesn't seem like i can communicate with it, either.

I have a little idea... my computer made a backup of itself just this night. Could i possibly use it for anything? It backed up /boot.

Is there be a possibility that i can reinstall GRUB?

Darn... i just realized something... i did the instructions for reinstalling the MBR incorrectly: it needed a chroot, not to be run from the liveDVD...
When i did as i should have, GRUB was back.

Thanks for the help anyway. You were right all the way. ;)

---

### Post by sikander3786 on 2010-12-19
> I set the boot-order to have the HDD first,

I still am pretty sure that the HDD order is not properly set in your Bios. You not only need to have the HDD as first boot device, but also bring your Ubuntu HDD to the top of the list under HDD menu.

You Bios might not be the same but for an idea, see the picture in the link below.

[http://ubuntuforums.org/album.php?albumid=2139&pictureid=7126](http://ubuntuforums.org/album.php?albumid=2139&pictureid=7126)

Under Hard Disk Boot Priority, your Ubuntu HDD should be on the top of that list as Grub is installed to the MBR of same disk.

You can definitely re-install Grub and we would definitely guide you there. But first, we need to make sure that we are not re-inventing the wheel :D

Your Grub seems pretty in tact in that boot script output thats why I am insisting to check the HDD boot order. Hope you don't get me wrong :-)

---

