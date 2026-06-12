---
title: "Acer aspire one dual boot problems"
date: 2011-02-14
forum: General Help
---

### Post by glitterbug on 2011-02-14
I installed 10.10 netbook remix and when I try to boot into XP it gives me the acer erecovery management console. I only get the option to restore to factory default. I think it may have noticed the partitions changed but am not sure how to get it working (the xp). any suggestions would greatly be appreciated.

---

### Post by wilee-nilee on 2011-02-14
In the installed Ubuntu terminal run.
sudo update-grub
Look for additional partitions to show.

I have an acer aspire it came with 2 partitions the main C operating system and the recovery partition. When I dual booted it both windows partitions worked so be careful the recovery will overwrite the C partition. If the update grub command doesn't work follow this. 

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by glitterbug on 2011-02-16
It also looks like I have it installed 2 times in grub? The one I have been using is sda7. I was able to get back into xp after updating grub (a new windows option appeared in the list)
```

results from sudo fdisk -l:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638       17010   131510443+   7  HPFS/NTFS
/dev/sda3           17010       19458    19662849    5  Extended
/dev/sda5           18285       19402     8972288   83  Linux
/dev/sda6           19402       19458      449536   82  Linux swap / Solaris
/dev/sda7           17010       18224     9754624   83  Linux
/dev/sda8           18224       18284      483328   82  Linux swap / Solaris


```
Are sda5 and 6 needed and if not how do I add them back to the xp partition? 

Here are the results from the script:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    10,233,404    10,233,342  12 Compaq diagnostics
/dev/sda2    *     10,233,405   273,254,291   263,020,887   7 HPFS/NTFS
/dev/sda3         273,254,398   312,580,095    39,325,698   5 Extended
/dev/sda5         293,734,400   311,678,975    17,944,576  83 Linux
/dev/sda6         311,681,024   312,580,095       899,072  82 Linux swap / Solaris
/dev/sda7         273,254,400   292,763,647    19,509,248  83 Linux
/dev/sda8         292,765,696   293,732,351       966,656  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0159-6699                              vfat       PQSERVICE                     
/dev/sda2        D69CBB449CBB1E45                       ntfs       ACER                          
/dev/sda3: PTTYPE="dos" 
/dev/sda5        5a35b709-978b-4d2c-9d7b-8052dd2cce9b   ext4                                     
/dev/sda6        ed3fecc7-f1c9-49d6-af45-ab6a94ceb828   swap                                     
/dev/sda7        6b404aab-9dad-4c0e-ad94-e8a0188fc53b   ext4                                     
/dev/sda8        ea7d9164-8d3f-4599-911d-514627e98949   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /media/ACER              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

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
UUID=5a35b709-978b-4d2c-9d7b-8052dd2cce9b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ed3fecc7-f1c9-49d6-af45-ab6a94ceb828 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 150.9GB: boot/vmlinuz-2.6.35-22-generic
 150.9GB: vmlinuz

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
search --no-floppy --fs-uuid --set 6b404aab-9dad-4c0e-ad94-e8a0188fc53b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 6b404aab-9dad-4c0e-ad94-e8a0188fc53b
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
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 6b404aab-9dad-4c0e-ad94-e8a0188fc53b
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=6b404aab-9dad-4c0e-ad94-e8a0188fc53b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 6b404aab-9dad-4c0e-ad94-e8a0188fc53b
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=6b404aab-9dad-4c0e-ad94-e8a0188fc53b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 6b404aab-9dad-4c0e-ad94-e8a0188fc53b
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6b404aab-9dad-4c0e-ad94-e8a0188fc53b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 6b404aab-9dad-4c0e-ad94-e8a0188fc53b
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=6b404aab-9dad-4c0e-ad94-e8a0188fc53b ro single 
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
    search --no-floppy --fs-uuid --set 6b404aab-9dad-4c0e-ad94-e8a0188fc53b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 6b404aab-9dad-4c0e-ad94-e8a0188fc53b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0159-6699
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Home Edition (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d69cbb449cbb1e45
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 5a35b709-978b-4d2c-9d7b-8052dd2cce9b
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=6b404aab-9dad-4c0e-ad94-e8a0188fc53b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=ea7d9164-8d3f-4599-911d-514627e98949 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 146.7GB: boot/grub/core.img
 144.6GB: boot/grub/grub.cfg
 141.1GB: boot/initrd.img-2.6.35-22-generic
 141.2GB: boot/initrd.img-2.6.35-25-generic
 146.6GB: boot/vmlinuz-2.6.35-22-generic
 146.6GB: boot/vmlinuz-2.6.35-25-generic
 141.2GB: initrd.img
 141.1GB: initrd.img.old
 146.6GB: vmlinuz
 146.6GB: vmlinuz.old

```

---

