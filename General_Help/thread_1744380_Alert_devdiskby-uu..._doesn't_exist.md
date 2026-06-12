---
title: "Alert /dev/disk/by-uu... doesn't exist"
date: 2011-04-30
forum: General Help
---

### Post by hnasiet on 2011-04-30
long story, I upgraded my system from maverick to natty, didn't like it so restored my system with a backup that I had done recently. after it rebooted I used gparted live CD to expand my partition, moving swap to the end of the HD, then when I rebooted grub didn't work so I booted with ubuntu live cd and reinstalled grub. then I booted normally but nautilus didn't work and had lots of problems. So I installed ubuntu again with ubuntu live cd, formating the partition and expanding it, no problems at all.
But, I wanted my files back, so restored the system again, now the message that I get is
>  Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
  -Check rootdelay= (did the system wait for the right device?)
  -Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
Alert! /dev/disk/by-uuid/3f34bf19-5c9b-4452-8f666-75ad578d743b does not exist.
Dropping to a shell
BusyBox v1.15.3 (ubuntu1:1.15.3-1ubuntu5) built-in shell (ash)Note:If it helps the live cd installed the kernel linux 2.6.35-22, restoring the system gave me 3.6.35-27 and 3.6.35-28.

PS:i did the backup and restoring following [this tutorial]("http://ubuntuforums.org/showthread.php?t=35087")

---

### Post by Rubi1200 on 2011-04-30
Hi,

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by hnasiet on 2011-04-30
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /GRLDR /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/winboot/wubildr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
224 heads, 19 sectors/track, 344254 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *        206,848   204,799,999   204,593,152   7 HPFS/NTFS
/dev/sda2         204,800,000   544,710,832   339,910,833   7 HPFS/NTFS
/dev/sda3         544,712,702   955,673,641   410,960,940   5 Extended
/dev/sda5         544,712,704   955,673,641   410,960,938  83 Linux
/dev/sda4       1,461,567,488 1,465,147,391     3,579,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D2BE55FDBE55DA95                       ntfs                                     
/dev/sda2        0CAAC56FAAC555BC                       ntfs       Disco2                        
/dev/sda3: PTTYPE="dos" 
/dev/sda4        6de5aca3-f598-44f0-9ee7-6ac1bd39e0d9   swap                                     
/dev/sda5        8bda5f0d-97e9-4409-b5d2-0f7b59ebe4c9   ext4                                     
/dev/sda: PTTYPE="dos" 

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
search --no-floppy --fs-uuid --set 3f34bf19-5c9b-4452-8f66-75ad578d743b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 3f34bf19-5c9b-4452-8f66-75ad578d743b
set locale_dir=($root)/boot/grub/locale
set lang=pt
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3f34bf19-5c9b-4452-8f66-75ad578d743b
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=3f34bf19-5c9b-4452-8f66-75ad578d743b ro   quiet splash ipv6.disable=1
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3f34bf19-5c9b-4452-8f66-75ad578d743b
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=3f34bf19-5c9b-4452-8f66-75ad578d743b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3f34bf19-5c9b-4452-8f66-75ad578d743b
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=3f34bf19-5c9b-4452-8f66-75ad578d743b ro   quiet splash ipv6.disable=1
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3f34bf19-5c9b-4452-8f66-75ad578d743b
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=3f34bf19-5c9b-4452-8f66-75ad578d743b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3f34bf19-5c9b-4452-8f66-75ad578d743b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 3f34bf19-5c9b-4452-8f66-75ad578d743b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d2be55fdbe55da95
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
UUID=3f34bf19-5c9b-4452-8f66-75ad578d743b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8575839f-3c76-454d-9e78-f3e47d4d47a6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 446.5GB: boot/grub/core.img
 446.5GB: boot/grub/grub.cfg
 280.0GB: boot/initrd.img-2.6.35-22-generic
 290.7GB: boot/initrd.img-2.6.35-27-generic
 290.7GB: boot/initrd.img-2.6.35-28-generic
 446.5GB: boot/vmlinuz-2.6.35-22-generic
 446.5GB: boot/vmlinuz-2.6.35-27-generic
 446.5GB: boot/vmlinuz-2.6.35-28-generic
 290.7GB: initrd.img
 290.7GB: initrd.img.old
 446.5GB: vmlinuz
 446.5GB: vmlinuz.old
```

---

### Post by Rubi1200 on 2011-04-30
Are you able to boot into your Ubuntu install at all? If yes, run the script there. If not, use the LiveCD.

Instructions from desktop part onwards remain the same.

---

### Post by hnasiet on 2011-04-30
> **Rubi1200 said:**
> Are you able to boot into your Ubuntu install at all? If yes, run the script there. If not, use the LiveCD.

Instructions from desktop part onwards remain the same.
 
Sorry, stupid question, I edited the post and put the results there

---

### Post by Rubi1200 on 2011-04-30
The problem seems to be that with all the changes the UUID (unique identifier) for the partition changed.

Therefore, the next time you boot and see the GRUB menu and the Ubuntu entry press "c" and do this at the prompt:

```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod linux
linux /vmlinuz root=/dev/sda5
initrd /initrd.img 
boot
```If this gets you back in run this:
```
sudo update-grub
```Let me know if this resolves the problem.

---

### Post by hnasiet on 2011-04-30
well, now I have another problem I can't enter "=" because the keyboard config is different in grub.
My keyboard is portuguese, by the way.

---

### Post by Rubi1200 on 2011-04-30
> **hnasiet said:**
> well, now I have another problem I can't enter "=" because the keyboard config is different in grub.
My keyboard is portuguese, by the way.
Aha! Well, now I have a problem too because I do not know what to tell you.

Perhaps try using Ctrl or Shift or Alt with = and see if that works (or a combination maybe?).

---

### Post by hnasiet on 2011-04-30
Thanks, problem solved, I was able to find = and the code worked.
Once again, thank you very much for your time and effort and sorry for any trouble I caused you.

---

### Post by Rubi1200 on 2011-04-30
No trouble at all. I am glad you got things sorted out :-)

---

