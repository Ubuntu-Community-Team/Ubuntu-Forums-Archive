---
title: "Removing Older Versions of Ubuntu"
date: 2011-05-05
forum: General Help
---

### Post by jokwon on 2011-05-05
So I've been trying to install 11.04 on my laptop for a couple days.  I tried the USB install a countless amount of times, and I tried upgrading from 10.04 to 10.10 to 11.04, but it never worked.  I finally installing it from Windows by the wubi installer, and now it works perfectly.

What I want to do now is remove 10.04, as well as GRUB.  GRUB first comes up, and I select my Windows partition.  Then I choose Ubuntu to load, and then another GRUB comes up.

To make my question simple, how do I remove 10.04, as well as make loading Ubuntu more simple?

---

### Post by garvinrick4 on 2011-05-05
Check in Windows command line:
```
bcdedit
```
See if there is 2 entries that say wubildr  or close to that? If so get back.
If not run this in a terminal in Ubuntu: Download this script to desktop and then run the code:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by jokwon on 2011-05-05
I entered bcdedit in the command line, and it says "The boot configuration data store could not be opened.  Access is denied."

What to do?

---

### Post by akand074 on 2011-05-05
> **jokwon said:**
> I entered bcdedit in the command line, and it says "The boot configuration data store could not be opened.  Access is denied."

What to do?

Download the boot info script and run it as explained in post #2 and tell us what it says. By the way incase you aren't aware, an install using Wubi isn't a real install, it's an install within Windows or something I believe. It doesn't perform as well as having it installed on it's own partition. Just fyi.

---

### Post by jokwon on 2011-05-05
> **akand074 said:**
> Download the boot info script and run it as explained in post #2 and tell us what it says. By the way incase you aren't aware, an install using Wubi isn't a real install, it's an install within Windows or something I believe. It doesn't perform as well as having it installed on it's own partition. Just fyi.


Sorry about that.  

```
Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=D:
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
default                 {current}
resumeobject            {05b0640c-26a3-11de-9c9b-eb99ed792b58}
displayorder            {current}
                        {6524e1a1-cd9d-11de-9ec6-0024e89e440d}
toolsdisplayorder       {memdiag}
timeout                 10

Windows Boot Loader
-------------------
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {6524e19f-cd9d-11de-9ec6-0024e89e440d}
recoveryenabled         Yes
osdevice                partition=C:
systemroot              \Windows
resumeobject            {05b0640c-26a3-11de-9c9b-eb99ed792b58}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {6524e1a1-cd9d-11de-9ec6-0024e89e440d}
device                  partition=C:
path                    \ubuntu\winboot\wubildr.mbr
description             Ubuntu
```

All the other installations I have tried do not work.  I upgraded 10.10 to 11.04 beta the week before the release, and it was working fine until one day it wouldn't load.  Recovery mode wouldn't load either, so there was no way I could access Ubuntu at all.  I tried a live USB of 11.04, but it would hang on the boot splash.  I ended up deleting the partition, installing 10.04, and using the methods I first described, and all of them, except for the wubi installer, had the same result.

---

### Post by jokwon on 2011-05-05
And sorry if I seem stupid.  I haven't slept for 2 days because of finals, and all this nonsense is just adding on to my delirium.

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       369,494       369,432  de Dell Utility
/dev/sda2    *        370,688     4,564,991     4,194,304   7 HPFS/NTFS
/dev/sda3           4,564,992   451,278,324   446,713,333   7 HPFS/NTFS
/dev/sda4         451,278,846   488,396,799    37,117,954   5 Extended
/dev/sda5         451,278,848   486,754,303    35,475,456  83 Linux
/dev/sda6         486,756,352   488,396,799     1,640,448  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       156b3b2a-45cd-400a-abfc-5520cb2602f0   ext4                                     
/dev/sda1        07D9-0706                              vfat       DellUtility                   
/dev/sda2        ACA4E31EA4E2E9B2                       ntfs       RECOVERY                      
/dev/sda3        56FEE60EFEE5E5E9                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        f4885bc0-73d0-468c-b2f9-d23b12f0a21e   ext4                                     
/dev/sda6        4e9f76f0-3a3a-473b-bbda-c49dc7269b06   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
/dev/sda5        /media/f4885bc0-73d0-468c-b2f9-d23b12f0a21e ext4       (rw,nosuid,nodev,uhelper=udisks)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root 56FEE60EFEE5E5E9
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-8-generic-pae" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 56FEE60EFEE5E5E9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=56FEE60EFEE5E5E9 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, Linux 2.6.38-8-generic-pae (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 56FEE60EFEE5E5E9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=56FEE60EFEE5E5E9 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root ACA4E31EA4E2E9B2
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f4885bc0-73d0-468c-b2f9-d23b12f0a21e
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=f4885bc0-73d0-468c-b2f9-d23b12f0a21e ro quiet splash
    initrd /boot/initrd.img-2.6.32-28-generic
}
menuentry "Ubuntu, with Linux 2.6.32-28-generic (recovery mode) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root f4885bc0-73d0-468c-b2f9-d23b12f0a21e
    linux /boot/vmlinuz-2.6.32-28-generic root=UUID=f4885bc0-73d0-468c-b2f9-d23b12f0a21e ro single
    initrd /boot/initrd.img-2.6.32-28-generic
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

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


   9.5GB: boot/grub/grub.cfg
   1.2GB: boot/initrd.img-2.6.38-8-generic-pae
    .7GB: boot/vmlinuz-2.6.38-8-generic-pae
   1.2GB: initrd.img
    .7GB: vmlinuz

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
search --no-floppy --fs-uuid --set f4885bc0-73d0-468c-b2f9-d23b12f0a21e
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
search --no-floppy --fs-uuid --set f4885bc0-73d0-468c-b2f9-d23b12f0a21e
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
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f4885bc0-73d0-468c-b2f9-d23b12f0a21e
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=f4885bc0-73d0-468c-b2f9-d23b12f0a21e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f4885bc0-73d0-468c-b2f9-d23b12f0a21e
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=f4885bc0-73d0-468c-b2f9-d23b12f0a21e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f4885bc0-73d0-468c-b2f9-d23b12f0a21e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set f4885bc0-73d0-468c-b2f9-d23b12f0a21e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set aca4e31ea4e2e9b2
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f4885bc0-73d0-468c-b2f9-d23b12f0a21e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4e9f76f0-3a3a-473b-bbda-c49dc7269b06 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 237.7GB: boot/grub/core.img
 235.8GB: boot/grub/grub.cfg
 237.7GB: boot/initrd.img-2.6.32-28-generic
 237.7GB: boot/vmlinuz-2.6.32-28-generic
 237.7GB: initrd.img
 237.7GB: vmlinuz
```

---

### Post by Duncan Williams on 2011-05-06
same sorta thing here, 3 versions of linux (maverick, natty, peppermint).
They all boot to blank screen. windows works ok, setup natty in 40gig partition, but that won't go past grub and other 2 live cds wont boot to gui.

---

### Post by garvinrick4 on 2011-05-06
A: Bcd looks good
B: You are now booting off of sda5 and then when you choose Windows or Ubuntu I imagine it gives you the
windows or Ubuntu choice in wubildr the Wubi boot loader. So you got 3 of them going on grub2, Windows and wubildr. I know if you take delete the sda5 partition there would be nothing in the mbr (master boot record) of your drive sda to boot off of. If you then reinstalled
your the Windows 7 bootloader does overwrite the wubildr for booting your WUBI install.
I would have to say so and you wind up having to uninstall Wubi which is easy and reinstall
Wubi to get the capablilities to boot both 7 and Ubuntu Wubi. 
 So if you have your Windows 7 recovery Cd handy Here is link for that:
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

#You also need a Ubuntu install cd to use under Try Ubuntu (live Cd);

1. In windows go to add and remove programs and uninstall Wubi: Or in Ubuntu folder in C: drive right next to Users has Ubuntu folder to uninstall from. Take your choice.
2. Take Ubuntu Cd in Live Cd mode and open gparted and format sda5 to say NTFS (right click on sda5 and go to format choose NTFS and the hit apply arrow)
Will now come up in Windows as a Letter like G: or F: just and empty partition for data for you.
3. Take Windows recovery Cd and use the link given only 2 commands: To install Windows boot (real easy)
4.  Now boot into Windows and  slip ubuntu disk in tray and choose Wubi click on and install.
5. Now will have just 7 and Ubuntu to boot from.
## This is one mans suggestion on how to get back in shape:
#There is a user named Rubi1200 that is excellent in WUBI around,  this will bump it up front if you believe simpler way around this:
#If you have the 2 disks handy will take 30 minutes start to finish:

---

