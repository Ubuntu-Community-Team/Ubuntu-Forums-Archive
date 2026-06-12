---
title: "kernel panic .... maverick doesnt seem to boot !!!"
date: 2010-12-23
forum: General Help
---

### Post by rvchari on 2010-12-23
hey guys,
earlier in the evening, when i was in office, something funny happened. my laptop power chord seemed to be disconnected and was running on battery power... i was away from desk and by the time i came back, laptop had gone to sleep may b due to battery getting drained.

i packed up and came home, plugged in and booted but ubuntu seemed to give lots of erros and didnt boot. i went to my win partition, burnt the iso i had earlier downloaded and kept on win partition for safety. i booted off the cd and issued sudo fsck command from terminal. fsck did its job and gave a clean chit for my dev/sda5 (where ubuntu is). when i rebooted to check, it gave the same error.
says kernel panic and lots of blah blah.
now i ve booted off the live cd and am here at the forums.....

what do i do from here ? honestly hope i dont have to go thru the process of re install !!!

---

### Post by PerSeL on 2010-12-23
I think I've a problem close to your
[http://ubuntuforums.org/showthread.php?t=1651021](http://ubuntuforums.org/showthread.php?t=1651021)

---

### Post by amsterdamharu on 2010-12-23
Maybe you could post the results of the boot info script here too and put some code tags around it please so it's easier to read.

And the /var/log/kern.log might help too.

---

### Post by rvchari on 2010-12-23
```

```Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: __________________________________________________  _______________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________  _______________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________  _______________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: __________________________________________________  _______________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: __________________________________________________  _______________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: __________________________________________________  _______________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________  ___

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000   7 HPFS/NTFS
/dev/sda2           3,074,048    48,580,607    45,506,560   7 HPFS/NTFS
/dev/sda3         467,914,752   488,394,751    20,480,000   7 HPFS/NTFS
/dev/sda4          48,595,741   467,903,519   419,307,779   5 Extended
/dev/sda5          48,595,743    97,403,039    48,807,297  83 Linux
/dev/sda6          97,403,103   126,705,599    29,302,497  83 Linux
/dev/sda7         126,705,663   224,365,679    97,660,017  83 Linux
/dev/sda8         224,365,743   322,023,711    97,657,969   7 HPFS/NTFS
/dev/sda9         322,025,823   458,740,799   136,714,977  83 Linux
/dev/sda10        458,740,863   467,903,519     9,162,657  82 Linux swap / Solaris


blkid -c /dev/null: __________________________________________________  __________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       4681a1a3-7a3a-44cb-b629-1eac3fe779b6   swap                                     
/dev/sda1        A24604274603FAB5                       ntfs       SERVICEV003                   
/dev/sda2        38981A009819BCF6                       ntfs                                     
/dev/sda3        2652087E520854C9                       ntfs       Lenovo                        
/dev/sda4: PTTYPE="dos" 
/dev/sda5        bcd52018-9be8-418c-91d1-d03f6a48789a   ext3                                     
/dev/sda6        34637be1-349c-4208-bd7d-6e5442d900a1   ext3                                     
/dev/sda7        202d6fdd-bfb8-4423-b08e-a93d7b2d2376   ext3       linux                         
/dev/sda8        06079E2E33F13F9B                       ntfs       windows                       
/dev/sda9        de3a7712-a05f-4242-ace6-d558f1668626   ext3       LinuxBackup                   
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
search --no-floppy --fs-uuid --set bcd52018-9be8-418c-91d1-d03f6a48789a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set bcd52018-9be8-418c-91d1-d03f6a48789a
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bcd52018-9be8-418c-91d1-d03f6a48789a
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=bcd52018-9be8-418c-91d1-d03f6a48789a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bcd52018-9be8-418c-91d1-d03f6a48789a
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=bcd52018-9be8-418c-91d1-d03f6a48789a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bcd52018-9be8-418c-91d1-d03f6a48789a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set bcd52018-9be8-418c-91d1-d03f6a48789a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a24604274603fab5
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
UUID=bcd52018-9be8-418c-91d1-d03f6a48789a /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=34637be1-349c-4208-bd7d-6e5442d900a1 /home           ext3    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=4681a1a3-7a3a-44cb-b629-1eac3fe779b6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


  35.7GB: boot/grub/core.img
  35.6GB: boot/grub/grub.cfg
  35.7GB: boot/initrd.img-2.6.35-23-generic
  33.6GB: boot/vmlinuz-2.6.35-23-generic
  35.7GB: initrd.img
  33.6GB: vmlinuz

---

### Post by rvchari on 2010-12-23
Dec 23 22:49:44 ubuntu kernel: imklog 4.2.0, log source = /proc/kmsg started.
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Linux version 2.6.35-22-generic (buildd@rothera) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu4) ) #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 (Ubuntu 2.6.35-22.33-generic 2.6.35.4)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bc4a1000 (usable)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bc4a1000 - 00000000bc4a7000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bc4a7000 - 00000000bc5b7000 (usable)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bc5b7000 - 00000000bc60f000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bc60f000 - 00000000bc6c6000 (usable)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bc6c6000 - 00000000bc6d1000 (ACPI NVS)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bc6d1000 - 00000000bc6d4000 (ACPI data)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bc6d4000 - 00000000bc6d8000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bc6d8000 - 00000000bc6dc000 (ACPI NVS)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bc6dc000 - 00000000bc6df000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bc6df000 - 00000000bc706000 (ACPI NVS)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bc706000 - 00000000bc708000 (ACPI data)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bc708000 - 00000000bc90f000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bc90f000 - 00000000bc99f000 (ACPI NVS)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bc99f000 - 00000000bc9ff000 (ACPI data)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bc9ff000 - 00000000bca00000 (usable)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000bcc00000 - 00000000bf000000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Notice: NX (Execute Disable) protection cannot be enabled: non-PAE kernel!
Dec 23 22:49:44 ubuntu kernel: [    0.000000] DMI present.
Dec 23 22:49:44 ubuntu kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000001000 (usable) ==> (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] last_pfn = 0xbca00 max_arch_pfn = 0x100000
Dec 23 22:49:44 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Dec 23 22:49:44 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   C0000-D3FFF write-protect
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   D4000-DBFFF uncachable
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   DC000-FFFFF write-protect
Dec 23 22:49:44 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   0 base 0BD000000 mask FFF000000 uncachable
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   1 base 0BE000000 mask FFE000000 uncachable
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   2 base 000000000 mask F80000000 write-back
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   3 base 080000000 mask FC0000000 write-back
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   4 base 0BCE00000 mask FFFE00000 uncachable
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   5 disabled
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   6 disabled
Dec 23 22:49:44 ubuntu kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 23 22:49:44 ubuntu kernel: [    0.000000] e820 update range: 0000000000002000 - 0000000000010000 (usable) ==> (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Scanning 1 areas for low memory corruption
Dec 23 22:49:44 ubuntu kernel: [    0.000000] modified physical RAM map:
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 0000000000000000 - 0000000000001000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 0000000000001000 - 0000000000002000 (usable)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 0000000000002000 - 0000000000010000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 0000000000010000 - 000000000009ec00 (usable)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 000000000009ec00 - 00000000000a0000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000000dc000 - 0000000000100000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 0000000000100000 - 00000000bc4a1000 (usable)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bc4a1000 - 00000000bc4a7000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bc4a7000 - 00000000bc5b7000 (usable)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bc5b7000 - 00000000bc60f000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bc60f000 - 00000000bc6c6000 (usable)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bc6c6000 - 00000000bc6d1000 (ACPI NVS)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bc6d1000 - 00000000bc6d4000 (ACPI data)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bc6d4000 - 00000000bc6d8000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bc6d8000 - 00000000bc6dc000 (ACPI NVS)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bc6dc000 - 00000000bc6df000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bc6df000 - 00000000bc706000 (ACPI NVS)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bc706000 - 00000000bc708000 (ACPI data)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bc708000 - 00000000bc90f000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bc90f000 - 00000000bc99f000 (ACPI NVS)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bc99f000 - 00000000bc9ff000 (ACPI data)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bc9ff000 - 00000000bca00000 (usable)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000bcc00000 - 00000000bf000000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  modified: 00000000ff800000 - 0000000100000000 (reserved)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] initial memory mapped : 0 - 00c00000
Dec 23 22:49:44 ubuntu kernel: [    0.000000] found SMP MP-table at [c00f6570] f6570
Dec 23 22:49:44 ubuntu kernel: [    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  0000000000 - 0000400000 page 4k
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  0000400000 - 0037400000 page 2M
Dec 23 22:49:44 ubuntu kernel: [    0.000000]  0037400000 - 00377fe000 page 4k
Dec 23 22:49:44 ubuntu kernel: [    0.000000] kernel direct mapping tables up to 377fe000 @ 15000-1a000
Dec 23 22:49:44 ubuntu kernel: [    0.000000] RAMDISK: 7f51e000 - 80000000
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Allocated new RAMDISK: 009a5000 - 0148698f
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Move RAMDISK from 000000007f51e000 - 000000007ffff98e to 009a5000 - 0148698e
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: RSDP 000f6530 00024 (v02 LENOVO)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: XSDT bc96a273 0009C (v01 LENOVO TP-6F    00002160  LTP 00000000)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: FACP bc96a400 000F4 (v03 LENOVO TP-6F    00002160 LNVO 00000001)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: DSDT bc96a7db 0F3FB (v01 LENOVO TP-6F    00002160 MSFT 03000000)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: FACS bc98e000 00040
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: SSDT bc96a5b4 00227 (v01 LENOVO TP-6F    00002160 MSFT 03000000)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: ECDT bc979bd6 00052 (v01 LENOVO TP-6F    00002160 LNVO 00000001)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: APIC bc979c28 00078 (v01 LENOVO TP-6F    00002160 LNVO 00000001)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: MCFG bc979ca0 0003C (v01 LENOVO TP-6F    00002160 LNVO 00000001)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: HPET bc979cdc 00038 (v01 LENOVO TP-6F    00002160 LNVO 00000001)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: SLIC bc979dc2 00176 (v01 LENOVO TP-6F    00002160  LTP 00000000)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: BOOT bc979f38 00028 (v01 LENOVO TP-6F    00002160  LTP 00000001)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: ASF! bc979f60 000A0 (v16 LENOVO TP-6F    00002160 PTL  00000001)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: SSDT bc98d213 0054F (v01 LENOVO TP-6F    00002160 INTL 20050513)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: TCPA bc707000 00032 (v00                 00000000      00000000)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: DMAR bc706000 00120 (v01               ? 00000001      00000000)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: SSDT bc6d3000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: SSDT bc6d2000 00274 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: SSDT bc6d1000 00242 (v01  PmRef    ApTst 00003000 INTL 20050624)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: DMI detected: Lenovo ThinkPad T500
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: Added _OSI(Linux)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 23 22:49:44 ubuntu kernel: [    0.000000] 2130MB HIGHMEM available.
Dec 23 22:49:44 ubuntu kernel: [    0.000000] 887MB LOWMEM available.
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   mapped low ram: 0 - 377fe000
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   low ram: 0 - 377fe000
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Zone PFN ranges:
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   DMA      0x00000001 -> 0x00001000
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   Normal   0x00001000 -> 0x000377fe
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   HighMem  0x000377fe -> 0x000bca00
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Movable zone start PFN for each node
Dec 23 22:49:44 ubuntu kernel: [    0.000000] early_node_map[6] active PFN ranges
Dec 23 22:49:44 ubuntu kernel: [    0.000000]     0: 0x00000001 -> 0x00000002
Dec 23 22:49:44 ubuntu kernel: [    0.000000]     0: 0x00000010 -> 0x0000009e
Dec 23 22:49:44 ubuntu kernel: [    0.000000]     0: 0x00000100 -> 0x000bc4a1
Dec 23 22:49:44 ubuntu kernel: [    0.000000]     0: 0x000bc4a7 -> 0x000bc5b7
Dec 23 22:49:44 ubuntu kernel: [    0.000000]     0: 0x000bc60f -> 0x000bc6c6
Dec 23 22:49:44 ubuntu kernel: [    0.000000]     0: 0x000bc9ff -> 0x000bca00
Dec 23 22:49:44 ubuntu kernel: [    0.000000] On node 0 totalpages: 771576
Dec 23 22:49:44 ubuntu kernel: [    0.000000] free_area_init_node: node 0, pgdat c07ffd40, node_mem_map c1488020
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   DMA zone: 0 pages reserved
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   Normal zone: 1744 pages used for memmap
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   Normal zone: 221486 pages, LIFO batch:31
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   HighMem zone: 4261 pages used for memmap
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   HighMem zone: 540102 pages, LIFO batch:31
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Using APIC driver default
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Dec 23 22:49:44 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 23 22:49:44 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Dec 23 22:49:44 ubuntu kernel: [    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
Dec 23 22:49:44 ubuntu kernel: [    0.000000] nr_irqs_gsi: 40
Dec 23 22:49:44 ubuntu kernel: [    0.000000] early_res array is doubled to 64 at [16000 - 167ff]
Dec 23 22:49:44 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000010000
Dec 23 22:49:44 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
Dec 23 22:49:44 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 23 22:49:44 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Dec 23 22:49:44 ubuntu kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Allocating PCI resources starting at bf000000 (gap: bf000000:21000000)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Dec 23 22:49:44 ubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
Dec 23 22:49:44 ubuntu kernel: [    0.000000] early_res array is doubled to 128 at [16800 - 177ff]
Dec 23 22:49:44 ubuntu kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @c3000000 s36416 r0 d20928 u1048576
Dec 23 22:49:44 ubuntu kernel: [    0.000000] pcpu-alloc: s36416 r0 d20928 u1048576 alloc=1*4194304
Dec 23 22:49:44 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 765539
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
Dec 23 22:49:44 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Enabling fast FPU save and restore... done.
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Initializing CPU#0
Dec 23 22:49:44 ubuntu kernel: [    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
Dec 23 22:49:44 ubuntu kernel: [    0.000000] allocated 15452140 bytes of page_cgroup
Dec 23 22:49:44 ubuntu kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Subtract (71 early reservations)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #1 [0000001000 - 0000002000]   EX TRAMPOLINE
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #2 [0000100000 - 00009a0adc]   TEXT DATA BSS
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #3 [00009a1000 - 00009a4138]             BRK
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #4 [00000f6580 - 0000100000]   BIOS reserved
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #5 [00000f6570 - 00000f6580]    MP-table mpf
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #6 [000009ec00 - 000009f171]   BIOS reserved
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #7 [000009f27d - 00000f6570]   BIOS reserved
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #8 [000009f171 - 000009f27d]    MP-table mpc
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #9 [0000010000 - 0000011000]      TRAMPOLINE
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #10 [0000011000 - 0000015000]     ACPI WAKEUP
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #11 [0000015000 - 0000016000]         PGTABLE
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #12 [00009a5000 - 0001487000]     NEW RAMDISK
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #13 [0001487000 - 0001488000]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #14 [0001488000 - 0002c20000]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #15 [0002c20000 - 0002c20004]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #16 [0002c20040 - 0002c20100]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #17 [0002c20100 - 0002c20154]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #18 [0002c20180 - 0002c23180]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #19 [0002c23180 - 0002c23248]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #20 [0002c23280 - 0002c2f280]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #21 [0002c2f280 - 0002c2f2a5]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #22 [0002c2f2c0 - 0002c2f2e7]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #23 [0002c2f300 - 0002c2f664]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #24 [0002c2f680 - 0002c2f6c0]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #25 [0002c2f6c0 - 0002c2f700]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #26 [0002c2f700 - 0002c2f740]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #27 [0002c2f740 - 0002c2f780]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #28 [0002c2f780 - 0002c2f7c0]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #29 [0002c2f7c0 - 0002c2f800]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #30 [0002c2f800 - 0002c2f840]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #31 [0002c2f840 - 0002c2f880]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #32 [0002c2f880 - 0002c2f8c0]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #33 [0002c2f8c0 - 0002c2f900]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #34 [0002c2f900 - 0002c2f940]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #35 [0002c2f940 - 0002c2f980]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #36 [0002c2f980 - 0002c2f9c0]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #37 [0002c2f9c0 - 0002c2fa00]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #38 [0002c2fa00 - 0002c2fa40]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #39 [0002c2fa40 - 0002c2fa80]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #40 [0002c2fa80 - 0002c2fac0]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #41 [0002c2fac0 - 0002c2fb00]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #42 [0002c2fb00 - 0002c2fb40]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #43 [0002c2fb40 - 0002c2fb80]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #44 [0002c2fb80 - 0002c2fbc0]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #45 [0002c2fbc0 - 0002c2fc00]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #46 [0002c2fc00 - 0002c2fc40]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #47 [0002c2fc40 - 0002c2fc80]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #48 [0002c2fc80 - 0002c2fcc0]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #49 [0002c2fcc0 - 0002c2fd00]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #50 [0002c2fd00 - 0002c2fd40]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #51 [0002c2fd40 - 0002c2fd80]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #52 [0002c2fd80 - 0002c2fd90]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #53 [0002c2fdc0 - 0002c2fdd0]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #54 [0002c2fe00 - 0002c2fe64]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #55 [0002c2fe80 - 0002c2fee4]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #56 [0003000000 - 000300e000]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #57 [0003100000 - 000310e000]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #58 [0003200000 - 000320e000]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #59 [0003300000 - 000330e000]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #60 [0002c31f00 - 0002c31f04]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #61 [0002c31f40 - 0002c31f44]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #62 [0002c31f80 - 0002c31f90]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #63 [0002c31fc0 - 0002c31fd0]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #64 [0002c32000 - 0002c320a0]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #65 [0002c320c0 - 0002c32108]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #66 [0002c32140 - 0002c36140]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #67 [0002c36140 - 0002cb6140]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #68 [0002cb6140 - 0002cf6140]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #69 [0002c2ff00 - 0002c30140]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000]   #70 [000330e000 - 00041ca7ec]         BOOTMEM
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Initializing HighMem for node 0 (000377fe:000bca00)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Memory: 3025940k/3090432k available (4928k kernel code, 60364k reserved, 2336k data, 684k init, 2177452k highmem)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] virtual kernel memory layout:
Dec 23 22:49:44 ubuntu kernel: [    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]       .init : 0xc0819000 - 0xc08c4000   ( 684 kB)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]       .data : 0xc05d029e - 0xc0818668   (2336 kB)
Dec 23 22:49:44 ubuntu kernel: [    0.000000]       .text : 0xc0100000 - 0xc05d029e   (4928 kB)
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Dec 23 22:49:44 ubuntu kernel: [    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Dec 23 22:49:44 ubuntu kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Dec 23 22:49:44 ubuntu kernel: [    0.000000]     RCU-based detection of stalled CPUs is disabled.
Dec 23 22:49:44 ubuntu kernel: [    0.000000]     Verbose stalled-CPUs detection is disabled.
Dec 23 22:49:44 ubuntu kernel: [    0.000000] NR_IRQS:2304 nr_irqs:712
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Extended CMOS year: 2000
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Dec 23 22:49:44 ubuntu kernel: [    0.000000] console [tty0] enabled
Dec 23 22:49:44 ubuntu kernel: [    0.000000] hpet clockevent registered
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Fast TSC calibration using PIT
Dec 23 22:49:44 ubuntu kernel: [    0.000000] Detected 2261.082 MHz processor.
Dec 23 22:49:44 ubuntu kernel: [    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4522.16 BogoMIPS (lpj=9044328)
Dec 23 22:49:44 ubuntu kernel: [    0.004009] pid_max: default: 32768 minimum: 301
Dec 23 22:49:44 ubuntu kernel: [    0.004030] Security Framework initialized
Dec 23 22:49:44 ubuntu kernel: [    0.004044] AppArmor: AppArmor initialized
Dec 23 22:49:44 ubuntu kernel: [    0.004046] Yama: becoming mindful.
Dec 23 22:49:44 ubuntu kernel: [    0.004095] Mount-cache hash table entries: 512
Dec 23 22:49:44 ubuntu kernel: [    0.004211] Initializing cgroup subsys ns
Dec 23 22:49:44 ubuntu kernel: [    0.004215] Initializing cgroup subsys cpuacct
Dec 23 22:49:44 ubuntu kernel: [    0.004219] Initializing cgroup subsys memory
Dec 23 22:49:44 ubuntu kernel: [    0.004227] Initializing cgroup subsys devices
Dec 23 22:49:44 ubuntu kernel: [    0.004229] Initializing cgroup subsys freezer
Dec 23 22:49:44 ubuntu kernel: [    0.004231] Initializing cgroup subsys net_cls
Dec 23 22:49:44 ubuntu kernel: [    0.004257] CPU: Physical Processor ID: 0
Dec 23 22:49:44 ubuntu kernel: [    0.004259] CPU: Processor Core ID: 0
Dec 23 22:49:44 ubuntu kernel: [    0.004261] mce: CPU supports 6 MCE banks
Dec 23 22:49:44 ubuntu kernel: [    0.004269] CPU0: Thermal monitoring enabled (TM2)
Dec 23 22:49:44 ubuntu kernel: [    0.004272] using mwait in idle threads.
Dec 23 22:49:44 ubuntu kernel: [    0.004279] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
Dec 23 22:49:44 ubuntu kernel: [    0.004288] ... version:                2
Dec 23 22:49:44 ubuntu kernel: [    0.004290] ... bit width:              40
Dec 23 22:49:44 ubuntu kernel: [    0.004291] ... generic registers:      2
Dec 23 22:49:44 ubuntu kernel: [    0.004293] ... value mask:             000000ffffffffff
Dec 23 22:49:44 ubuntu kernel: [    0.004295] ... max period:             000000007fffffff
Dec 23 22:49:44 ubuntu kernel: [    0.004297] ... fixed-purpose events:   3
Dec 23 22:49:44 ubuntu kernel: [    0.004298] ... event mask:             0000000700000003
Dec 23 22:49:44 ubuntu kernel: [    0.007012] ACPI: Core revision 20100428
Dec 23 22:49:44 ubuntu kernel: [    0.028010] ftrace: converting mcount calls to 0f 1f 44 00 00
Dec 23 22:49:44 ubuntu kernel: [    0.028015] ftrace: allocating 21758 entries in 43 pages
Dec 23 22:49:44 ubuntu kernel: [    0.032044] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Dec 23 22:49:44 ubuntu kernel: [    0.032392] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 23 22:49:44 ubuntu kernel: [    0.074500] CPU0: Intel(R) Core(TM)2 Duo CPU     P8400  @ 2.26GHz stepping 0a
Dec 23 22:49:44 ubuntu kernel: [    0.076000] Booting Node   0, Processors  #1
Dec 23 22:49:44 ubuntu kernel: [    0.008000] Initializing CPU#1
Dec 23 22:49:44 ubuntu kernel: [    0.164013] Brought up 2 CPUs
Dec 23 22:49:44 ubuntu kernel: [    0.164016] Total of 2 processors activated (9044.13 BogoMIPS).
Dec 23 22:49:44 ubuntu kernel: [    0.164653] devtmpfs: initialized
Dec 23 22:49:44 ubuntu kernel: [    0.164918] regulator: core version 0.5
Dec 23 22:49:44 ubuntu kernel: [    0.164947] Time: 22:48:25  Date: 12/23/10
Dec 23 22:49:44 ubuntu kernel: [    0.164986] NET: Registered protocol family 16
Dec 23 22:49:44 ubuntu kernel: [    0.165006] Trying to unpack rootfs image as initramfs...
Dec 23 22:49:44 ubuntu kernel: [    0.165121] EISA bus registered
Dec 23 22:49:44 ubuntu kernel: [    0.165128] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
Dec 23 22:49:44 ubuntu kernel: [    0.165131] ACPI: bus type pci registered
Dec 23 22:49:44 ubuntu kernel: [    0.165205] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
Dec 23 22:49:44 ubuntu kernel: [    0.165209] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in E820
Dec 23 22:49:44 ubuntu kernel: [    0.165210] PCI: Using MMCONFIG for extended config space
Dec 23 22:49:44 ubuntu kernel: [    0.165212] PCI: Using configuration type 1 for base access
Dec 23 22:49:44 ubuntu kernel: [    1.164147] bio: create slab <bio-0> at 0
Dec 23 22:49:44 ubuntu kernel: [    1.166676] ACPI: EC: EC description table is found, configuring boot EC
Dec 23 22:49:44 ubuntu kernel: [    1.176259] ACPI: BIOS _OSI(Linux) query honored via DMI
Dec 23 22:49:44 ubuntu kernel: [    1.188967] ACPI: SSDT bc6d6c20 002C8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Dec 23 22:49:44 ubuntu kernel: [    1.189603] ACPI: Dynamic OEM Table Load:
Dec 23 22:49:44 ubuntu kernel: [    1.189607] ACPI: SSDT (null) 002C8 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
Dec 23 22:49:44 ubuntu kernel: [    1.189989] ACPI: SSDT bc6d4020 0087A (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Dec 23 22:49:44 ubuntu kernel: [    1.190665] ACPI: Dynamic OEM Table Load:
Dec 23 22:49:44 ubuntu kernel: [    1.190668] ACPI: SSDT (null) 0087A (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
Dec 23 22:49:44 ubuntu kernel: [    1.191215] ACPI: SSDT bc6d5ca0 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
Dec 23 22:49:44 ubuntu kernel: [    1.191877] ACPI: Dynamic OEM Table Load:
Dec 23 22:49:44 ubuntu kernel: [    1.191880] ACPI: SSDT (null) 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
Dec 23 22:49:44 ubuntu kernel: [    1.192067] ACPI: SSDT bc6d5f20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
Dec 23 22:49:44 ubuntu kernel: [    1.192703] ACPI: Dynamic OEM Table Load:
Dec 23 22:49:44 ubuntu kernel: [    1.192706] ACPI: SSDT (null) 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
Dec 23 22:49:44 ubuntu kernel: [    1.192846] ACPI: Interpreter enabled
Dec 23 22:49:44 ubuntu kernel: [    1.192849] ACPI: (supports S0 S3 S4 S5)
Dec 23 22:49:44 ubuntu kernel: [    1.192874] ACPI: Using IOAPIC for interrupt routing
Dec 23 22:49:44 ubuntu kernel: [    1.213266] ACPI: EC: GPE = 0x11, I/O: command/status = 0x66, data = 0x62
Dec 23 22:49:44 ubuntu kernel: [    1.213510] ACPI: Power Resource [PUBS] (on)
Dec 23 22:49:44 ubuntu kernel: [    1.214647] ACPI: ACPI Dock Station Driver: 3 docks/bays found
Dec 23 22:49:44 ubuntu kernel: [    1.214647] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Dec 23 22:49:44 ubuntu kernel: [    1.216056] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Dec 23 22:49:44 ubuntu kernel: [    1.216112] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
Dec 23 22:49:44 ubuntu kernel: [    1.216115] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
Dec 23 22:49:44 ubuntu kernel: [    1.216118] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
Dec 23 22:49:44 ubuntu kernel: [    1.216121] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
Dec 23 22:49:44 ubuntu kernel: [    1.216123] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
Dec 23 22:49:44 ubuntu kernel: [    1.216126] pci_root PNP0A08:00: host bridge window [mem 0xbf000000-0xfebfffff]
Dec 23 22:49:44 ubuntu kernel: [    1.216185] pci 0000:00:02.0: reg 10: [mem 0xf4400000-0xf47fffff 64bit]
Dec 23 22:49:44 ubuntu kernel: [    1.216192] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    1.216197] pci 0000:00:02.0: reg 20: [io  0x1800-0x1807]
Dec 23 22:49:44 ubuntu kernel: [    1.216231] pci 0000:00:02.1: reg 10: [mem 0xf4200000-0xf42fffff 64bit]
Dec 23 22:49:44 ubuntu kernel: [    1.216284] pci 0000:00:03.0: reg 10: [mem 0xfc226800-0xfc22680f 64bit]
Dec 23 22:49:44 ubuntu kernel: [    1.216317] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
Dec 23 22:49:44 ubuntu kernel: [    1.216320] pci 0000:00:03.0: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.216347] pci 0000:00:03.2: reg 10: [io  0x1828-0x182f]
Dec 23 22:49:44 ubuntu kernel: [    1.216353] pci 0000:00:03.2: reg 14: [io  0x180c-0x180f]
Dec 23 22:49:44 ubuntu kernel: [    1.216358] pci 0000:00:03.2: reg 18: [io  0x1820-0x1827]
Dec 23 22:49:44 ubuntu kernel: [    1.216363] pci 0000:00:03.2: reg 1c: [io  0x1808-0x180b]
Dec 23 22:49:44 ubuntu kernel: [    1.216368] pci 0000:00:03.2: reg 20: [io  0x1810-0x181f]
Dec 23 22:49:44 ubuntu kernel: [    1.216415] pci 0000:00:03.3: reg 10: [io  0x1830-0x1837]
Dec 23 22:49:44 ubuntu kernel: [    1.216420] pci 0000:00:03.3: reg 14: [mem 0xfc024000-0xfc024fff]
Dec 23 22:49:44 ubuntu kernel: [    1.216532] pci 0000:00:19.0: reg 10: [mem 0xfc000000-0xfc01ffff]
Dec 23 22:49:44 ubuntu kernel: [    1.216540] pci 0000:00:19.0: reg 14: [mem 0xfc025000-0xfc025fff]
Dec 23 22:49:44 ubuntu kernel: [    1.216548] pci 0000:00:19.0: reg 18: [io  0x1840-0x185f]
Dec 23 22:49:44 ubuntu kernel: [    1.216604] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
Dec 23 22:49:44 ubuntu kernel: [    1.216609] pci 0000:00:19.0: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.216671] pci 0000:00:1a.0: reg 20: [io  0x1860-0x187f]
Dec 23 22:49:44 ubuntu kernel: [    1.216758] pci 0000:00:1a.1: reg 20: [io  0x1880-0x189f]
Dec 23 22:49:44 ubuntu kernel: [    1.216846] pci 0000:00:1a.2: reg 20: [io  0x18a0-0x18bf]
Dec 23 22:49:44 ubuntu kernel: [    1.216931] pci 0000:00:1a.7: reg 10: [mem 0xfc226c00-0xfc226fff]
Dec 23 22:49:44 ubuntu kernel: [    1.216999] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Dec 23 22:49:44 ubuntu kernel: [    1.217004] pci 0000:00:1a.7: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.217051] pci 0000:00:1b.0: reg 10: [mem 0xfc020000-0xfc023fff 64bit]
Dec 23 22:49:44 ubuntu kernel: [    1.217111] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Dec 23 22:49:44 ubuntu kernel: [    1.217116] pci 0000:00:1b.0: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.217214] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Dec 23 22:49:44 ubuntu kernel: [    1.217219] pci 0000:00:1c.0: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.217319] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Dec 23 22:49:44 ubuntu kernel: [    1.217324] pci 0000:00:1c.1: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.217425] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Dec 23 22:49:44 ubuntu kernel: [    1.217430] pci 0000:00:1c.3: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.217529] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
Dec 23 22:49:44 ubuntu kernel: [    1.217534] pci 0000:00:1c.4: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.217606] pci 0000:00:1d.0: reg 20: [io  0x18c0-0x18df]
Dec 23 22:49:44 ubuntu kernel: [    1.217693] pci 0000:00:1d.1: reg 20: [io  0x18e0-0x18ff]
Dec 23 22:49:44 ubuntu kernel: [    1.217781] pci 0000:00:1d.2: reg 20: [io  0x1c00-0x1c1f]
Dec 23 22:49:44 ubuntu kernel: [    1.217865] pci 0000:00:1d.7: reg 10: [mem 0xfc227000-0xfc2273ff]
Dec 23 22:49:44 ubuntu kernel: [    1.217933] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Dec 23 22:49:44 ubuntu kernel: [    1.217939] pci 0000:00:1d.7: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.218174] pci 0000:00:1f.2: reg 10: [io  0x1c48-0x1c4f]
Dec 23 22:49:44 ubuntu kernel: [    1.218182] pci 0000:00:1f.2: reg 14: [io  0x183c-0x183f]
Dec 23 22:49:44 ubuntu kernel: [    1.218190] pci 0000:00:1f.2: reg 18: [io  0x1c40-0x1c47]
Dec 23 22:49:44 ubuntu kernel: [    1.218198] pci 0000:00:1f.2: reg 1c: [io  0x1838-0x183b]
Dec 23 22:49:44 ubuntu kernel: [    1.218205] pci 0000:00:1f.2: reg 20: [io  0x1c20-0x1c3f]
Dec 23 22:49:44 ubuntu kernel: [    1.218213] pci 0000:00:1f.2: reg 24: [mem 0xfc226000-0xfc2267ff]
Dec 23 22:49:44 ubuntu kernel: [    1.218260] pci 0000:00:1f.2: PME# supported from D3hot
Dec 23 22:49:44 ubuntu kernel: [    1.218265] pci 0000:00:1f.2: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.218305] pci 0000:00:1f.3: reg 10: [mem 0xfc227400-0xfc2274ff 64bit]
Dec 23 22:49:44 ubuntu kernel: [    1.218324] pci 0000:00:1f.3: reg 20: [io  0x1c60-0x1c7f]
Dec 23 22:49:44 ubuntu kernel: [    1.218412] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Dec 23 22:49:44 ubuntu kernel: [    1.218417] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
Dec 23 22:49:44 ubuntu kernel: [    1.218423] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
Dec 23 22:49:44 ubuntu kernel: [    1.218431] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Dec 23 22:49:44 ubuntu kernel: [    1.218554] pci 0000:03:00.0: reg 10: [mem 0xf4300000-0xf4301fff 64bit]
Dec 23 22:49:44 ubuntu kernel: [    1.218671] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
Dec 23 22:49:44 ubuntu kernel: [    1.218678] pci 0000:03:00.0: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.218716] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Dec 23 22:49:44 ubuntu kernel: [    1.218721] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
Dec 23 22:49:44 ubuntu kernel: [    1.218726] pci 0000:00:1c.1:   bridge window [mem 0xf4300000-0xf43fffff]
Dec 23 22:49:44 ubuntu kernel: [    1.218734] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
Dec 23 22:49:44 ubuntu kernel: [    1.218794] pci 0000:00:1c.3: PCI bridge to [bus 05-0c]
Dec 23 22:49:44 ubuntu kernel: [    1.218799] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
Dec 23 22:49:44 ubuntu kernel: [    1.218804] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xf9ffffff]
Dec 23 22:49:44 ubuntu kernel: [    1.218812] pci 0000:00:1c.3:   bridge window [mem 0xf4000000-0xf40fffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    1.218873] pci 0000:00:1c.4: PCI bridge to [bus 0d-14]
Dec 23 22:49:44 ubuntu kernel: [    1.218878] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
Dec 23 22:49:44 ubuntu kernel: [    1.218883] pci 0000:00:1c.4:   bridge window [mem 0xfa000000-0xfbffffff]
Dec 23 22:49:44 ubuntu kernel: [    1.218891] pci 0000:00:1c.4:   bridge window [mem 0xf4100000-0xf41fffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    1.218960] pci 0000:15:00.0: proprietary Ricoh MMC controller disabled (via cardbus function)
Dec 23 22:49:44 ubuntu kernel: [    1.218962] pci 0000:15:00.0: MMC cards are now supported by standard SDHCI controller
Dec 23 22:49:44 ubuntu kernel: [    1.218976] pci 0000:15:00.0: reg 10: [mem 0xf4800000-0xf4800fff]
Dec 23 22:49:44 ubuntu kernel: [    1.219005] pci 0000:15:00.0: supports D1 D2
Dec 23 22:49:44 ubuntu kernel: [    1.219007] pci 0000:15:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 23 22:49:44 ubuntu kernel: [    1.219012] pci 0000:15:00.0: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.219056] pci 0000:15:00.1: reg 10: [mem 0xf4801000-0xf48017ff]
Dec 23 22:49:44 ubuntu kernel: [    1.219129] pci 0000:15:00.1: supports D1 D2
Dec 23 22:49:44 ubuntu kernel: [    1.219131] pci 0000:15:00.1: PME# supported from D0 D1 D2 D3hot D3cold
Dec 23 22:49:44 ubuntu kernel: [    1.219136] pci 0000:15:00.1: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.219180] pci 0000:15:00.2: reg 10: [mem 0xf4801800-0xf48018ff]
Dec 23 22:49:44 ubuntu kernel: [    1.219252] pci 0000:15:00.2: supports D1 D2
Dec 23 22:49:44 ubuntu kernel: [    1.219254] pci 0000:15:00.2: PME# supported from D0 D1 D2 D3hot D3cold
Dec 23 22:49:44 ubuntu kernel: [    1.219259] pci 0000:15:00.2: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.219307] pci 0000:15:00.4: reg 10: [mem 0xf4802000-0xf48020ff]
Dec 23 22:49:44 ubuntu kernel: [    1.219379] pci 0000:15:00.4: supports D1 D2
Dec 23 22:49:44 ubuntu kernel: [    1.219381] pci 0000:15:00.4: PME# supported from D0 D1 D2 D3hot D3cold
Dec 23 22:49:44 ubuntu kernel: [    1.219387] pci 0000:15:00.4: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.219430] pci 0000:15:00.5: reg 10: [mem 0xf4802400-0xf48024ff]
Dec 23 22:49:44 ubuntu kernel: [    1.219502] pci 0000:15:00.5: supports D1 D2
Dec 23 22:49:44 ubuntu kernel: [    1.219504] pci 0000:15:00.5: PME# supported from D0 D1 D2 D3hot D3cold
Dec 23 22:49:44 ubuntu kernel: [    1.219509] pci 0000:15:00.5: PME# disabled
Dec 23 22:49:44 ubuntu kernel: [    1.219584] pci 0000:00:1e.0: PCI bridge to [bus 15-18] (subtractive decode)
Dec 23 22:49:44 ubuntu kernel: [    1.219589] pci 0000:00:1e.0:   bridge window [io  0x4000-0x7fff]
Dec 23 22:49:44 ubuntu kernel: [    1.219594] pci 0000:00:1e.0:   bridge window [mem 0xf4800000-0xf7ffffff]
Dec 23 22:49:44 ubuntu kernel: [    1.219602] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xf3ffffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    1.219605] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Dec 23 22:49:44 ubuntu kernel: [    1.219607] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Dec 23 22:49:44 ubuntu kernel: [    1.219610] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Dec 23 22:49:44 ubuntu kernel: [    1.219612] pci 0000:00:1e.0:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
Dec 23 22:49:44 ubuntu kernel: [    1.219614] pci 0000:00:1e.0:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
Dec 23 22:49:44 ubuntu kernel: [    1.219617] pci 0000:00:1e.0:   bridge window [mem 0xbf000000-0xfebfffff] (subtractive decode)
Dec 23 22:49:44 ubuntu kernel: [    1.219701] pci_bus 0000:00: on NUMA node 0
Dec 23 22:49:44 ubuntu kernel: [    1.219706] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 23 22:49:44 ubuntu kernel: [    1.219898] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP0._PRT]
Dec 23 22:49:44 ubuntu kernel: [    1.219970] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
Dec 23 22:49:44 ubuntu kernel: [    1.220058] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
Dec 23 22:49:44 ubuntu kernel: [    1.220138] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
Dec 23 22:49:44 ubuntu kernel: [    1.220218] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Dec 23 22:49:44 ubuntu kernel: [    1.228609] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
Dec 23 22:49:44 ubuntu kernel: [    1.228794] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
Dec 23 22:49:44 ubuntu kernel: [    1.228978] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
Dec 23 22:49:44 ubuntu kernel: [    1.229160] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
Dec 23 22:49:44 ubuntu kernel: [    1.229343] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
Dec 23 22:49:44 ubuntu kernel: [    1.229525] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11)
Dec 23 22:49:44 ubuntu kernel: [    1.229708] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11)
Dec 23 22:49:44 ubuntu kernel: [    1.229890] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11)
Dec 23 22:49:44 ubuntu kernel: [    1.229966] HEST: Table is not found!
Dec 23 22:49:44 ubuntu kernel: [    1.230047] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Dec 23 22:49:44 ubuntu kernel: [    1.230066] vgaarb: loaded
Dec 23 22:49:44 ubuntu kernel: [    1.230233] SCSI subsystem initialized
Dec 23 22:49:44 ubuntu kernel: [    1.230294] libata version 3.00 loaded.
Dec 23 22:49:44 ubuntu kernel: [    1.230349] usbcore: registered new interface driver usbfs
Dec 23 22:49:44 ubuntu kernel: [    1.230364] usbcore: registered new interface driver hub
Dec 23 22:49:44 ubuntu kernel: [    1.230387] usbcore: registered new device driver usb
Dec 23 22:49:44 ubuntu kernel: [    1.230682] ACPI: WMI: Mapper loaded
Dec 23 22:49:44 ubuntu kernel: [    1.230684] PCI: Using ACPI for IRQ routing
Dec 23 22:49:44 ubuntu kernel: [    1.230686] PCI: pci_cache_line_size set to 64 bytes
Dec 23 22:49:44 ubuntu kernel: [    1.230827] reserve RAM buffer: 0000000000002000 - 000000000000ffff 
Dec 23 22:49:44 ubuntu kernel: [    1.230829] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
Dec 23 22:49:44 ubuntu kernel: [    1.230831] reserve RAM buffer: 00000000bc4a1000 - 00000000bfffffff 
Dec 23 22:49:44 ubuntu kernel: [    1.230837] reserve RAM buffer: 00000000bc5b7000 - 00000000bfffffff 
Dec 23 22:49:44 ubuntu kernel: [    1.230842] reserve RAM buffer: 00000000bc6c6000 - 00000000bfffffff 
Dec 23 22:49:44 ubuntu kernel: [    1.230847] reserve RAM buffer: 00000000bca00000 - 00000000bfffffff 
Dec 23 22:49:44 ubuntu kernel: [    1.230937] NetLabel: Initializing
Dec 23 22:49:44 ubuntu kernel: [    1.230939] NetLabel:  domain hash size = 128
Dec 23 22:49:44 ubuntu kernel: [    1.230940] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 23 22:49:44 ubuntu kernel: [    1.230951] NetLabel:  unlabeled traffic allowed by default
Dec 23 22:49:44 ubuntu kernel: [    1.230983] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
Dec 23 22:49:44 ubuntu kernel: [    1.230991] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
Dec 23 22:49:44 ubuntu kernel: [    1.230996] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
Dec 23 22:49:44 ubuntu kernel: [    2.148044] Switching to clocksource tsc
Dec 23 22:49:44 ubuntu kernel: [    2.159081] AppArmor: AppArmor Filesystem Enabled
Dec 23 22:49:44 ubuntu kernel: [    2.159102] pnp: PnP ACPI init
Dec 23 22:49:44 ubuntu kernel: [    2.159125] ACPI: bus type pnp registered
Dec 23 22:49:44 ubuntu kernel: [    2.222242] pnp: PnP ACPI: found 10 devices
Dec 23 22:49:44 ubuntu kernel: [    2.222244] ACPI: ACPI bus type pnp unregistered
Dec 23 22:49:44 ubuntu kernel: [    2.222248] PnPBIOS: Disabled by ACPI PNP
Dec 23 22:49:44 ubuntu kernel: [    2.222264] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222268] system 00:00: [mem 0x000c0000-0x000c3fff] could not be reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222271] system 00:00: [mem 0x000c4000-0x000c7fff] could not be reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222274] system 00:00: [mem 0x000c8000-0x000cbfff] has been reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222276] system 00:00: [mem 0x000cc000-0x000cffff] has been reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222279] system 00:00: [mem 0x000d0000-0x000d3fff] could not be reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222282] system 00:00: [mem 0x000dc000-0x000dffff] could not be reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222284] system 00:00: [mem 0x000e0000-0x000e3fff] could not be reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222287] system 00:00: [mem 0x000e4000-0x000e7fff] could not be reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222290] system 00:00: [mem 0x000e8000-0x000ebfff] could not be reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222292] system 00:00: [mem 0x000ec000-0x000effff] could not be reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222295] system 00:00: [mem 0x000f0000-0x000fffff] could not be reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222298] system 00:00: [mem 0x00100000-0xbeffffff] could not be reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222301] system 00:00: [mem 0xfec00000-0xfed3ffff] could not be reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222304] system 00:00: [mem 0xfed4c000-0xffffffff] could not be reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222311] system 00:02: [io  0x1000-0x107f] has been reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222314] system 00:02: [io  0x1180-0x11ff] has been reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222317] system 00:02: [io  0x0800-0x080f] has been reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222320] system 00:02: [io  0x15e0-0x15ef] has been reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222322] system 00:02: [io  0x1600-0x167f] has been reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222325] system 00:02: [io  0x1680-0x169f] has been reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222328] system 00:02: [mem 0xe0000000-0xefffffff] has been reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222331] system 00:02: [mem 0xfed1c000-0xfed1ffff] has been reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222334] system 00:02: [mem 0xfed10000-0xfed13fff] has been reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222337] system 00:02: [mem 0xfed18000-0xfed18fff] has been reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222339] system 00:02: [mem 0xfed19000-0xfed19fff] has been reserved
Dec 23 22:49:44 ubuntu kernel: [    2.222342] system 00:02: [mem 0xfed45000-0xfed4bfff] has been reserved
Dec 23 22:49:44 ubuntu kernel: [    2.258543] pci 0000:00:1c.0: BAR 14: assigned [mem 0xbf000000-0xbf1fffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258548] pci 0000:00:1c.0: BAR 15: assigned [mem 0xbf200000-0xbf3fffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    2.258552] pci 0000:00:1c.1: BAR 15: assigned [mem 0xbf400000-0xbf5fffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    2.258556] pci 0000:00:1c.0: BAR 13: assigned [io  0x8000-0x8fff]
Dec 23 22:49:44 ubuntu kernel: [    2.258558] pci 0000:00:1c.1: BAR 13: assigned [io  0x9000-0x9fff]
Dec 23 22:49:44 ubuntu kernel: [    2.258561] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
Dec 23 22:49:44 ubuntu kernel: [    2.258565] pci 0000:00:1c.0:   bridge window [io  0x8000-0x8fff]
Dec 23 22:49:44 ubuntu kernel: [    2.258571] pci 0000:00:1c.0:   bridge window [mem 0xbf000000-0xbf1fffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258576] pci 0000:00:1c.0:   bridge window [mem 0xbf200000-0xbf3fffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    2.258584] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
Dec 23 22:49:44 ubuntu kernel: [    2.258588] pci 0000:00:1c.1:   bridge window [io  0x9000-0x9fff]
Dec 23 22:49:44 ubuntu kernel: [    2.258594] pci 0000:00:1c.1:   bridge window [mem 0xf4300000-0xf43fffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258599] pci 0000:00:1c.1:   bridge window [mem 0xbf400000-0xbf5fffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    2.258606] pci 0000:00:1c.3: PCI bridge to [bus 05-0c]
Dec 23 22:49:44 ubuntu kernel: [    2.258610] pci 0000:00:1c.3:   bridge window [io  0x2000-0x2fff]
Dec 23 22:49:44 ubuntu kernel: [    2.258616] pci 0000:00:1c.3:   bridge window [mem 0xf8000000-0xf9ffffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258621] pci 0000:00:1c.3:   bridge window [mem 0xf4000000-0xf40fffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    2.258629] pci 0000:00:1c.4: PCI bridge to [bus 0d-14]
Dec 23 22:49:44 ubuntu kernel: [    2.258632] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
Dec 23 22:49:44 ubuntu kernel: [    2.258638] pci 0000:00:1c.4:   bridge window [mem 0xfa000000-0xfbffffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258643] pci 0000:00:1c.4:   bridge window [mem 0xf4100000-0xf41fffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    2.258653] pci 0000:15:00.0: BAR 15: assigned [mem 0xf0000000-0xf3ffffff pref]
Dec 23 22:49:44 ubuntu kernel: [    2.258656] pci 0000:15:00.0: BAR 16: assigned [mem 0xc0000000-0xc3ffffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258658] pci 0000:15:00.0: BAR 13: assigned [io  0x4000-0x40ff]
Dec 23 22:49:44 ubuntu kernel: [    2.258660] pci 0000:15:00.0: BAR 14: assigned [io  0x4400-0x44ff]
Dec 23 22:49:44 ubuntu kernel: [    2.258663] pci 0000:15:00.0: CardBus bridge to [bus 16-17]
Dec 23 22:49:44 ubuntu kernel: [    2.258665] pci 0000:15:00.0:   bridge window [io  0x4000-0x40ff]
Dec 23 22:49:44 ubuntu kernel: [    2.258670] pci 0000:15:00.0:   bridge window [io  0x4400-0x44ff]
Dec 23 22:49:44 ubuntu kernel: [    2.258676] pci 0000:15:00.0:   bridge window [mem 0xf0000000-0xf3ffffff pref]
Dec 23 22:49:44 ubuntu kernel: [    2.258682] pci 0000:15:00.0:   bridge window [mem 0xc0000000-0xc3ffffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258688] pci 0000:00:1e.0: PCI bridge to [bus 15-18]
Dec 23 22:49:44 ubuntu kernel: [    2.258691] pci 0000:00:1e.0:   bridge window [io  0x4000-0x7fff]
Dec 23 22:49:44 ubuntu kernel: [    2.258698] pci 0000:00:1e.0:   bridge window [mem 0xf4800000-0xf7ffffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258702] pci 0000:00:1e.0:   bridge window [mem 0xf0000000-0xf3ffffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    2.258723]   alloc irq_desc for 20 on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.258725]   alloc kstat_irqs on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.258732] pci 0000:00:1c.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Dec 23 22:49:44 ubuntu kernel: [    2.258737] pci 0000:00:1c.0: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.258748]   alloc irq_desc for 21 on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.258750]   alloc kstat_irqs on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.258753] pci 0000:00:1c.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Dec 23 22:49:44 ubuntu kernel: [    2.258758] pci 0000:00:1c.1: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.258769]   alloc irq_desc for 23 on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.258770]   alloc kstat_irqs on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.258774] pci 0000:00:1c.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Dec 23 22:49:44 ubuntu kernel: [    2.258779] pci 0000:00:1c.3: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.258790] pci 0000:00:1c.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Dec 23 22:49:44 ubuntu kernel: [    2.258795] pci 0000:00:1c.4: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.258804] pci 0000:00:1e.0: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.258821]   alloc irq_desc for 16 on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.258822]   alloc kstat_irqs on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.258826] pci 0000:15:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 23 22:49:44 ubuntu kernel: [    2.258833] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Dec 23 22:49:44 ubuntu kernel: [    2.258835] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258837] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258840] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff]
Dec 23 22:49:44 ubuntu kernel: [    2.258842] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff]
Dec 23 22:49:44 ubuntu kernel: [    2.258844] pci_bus 0000:00: resource 9 [mem 0xbf000000-0xfebfffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258847] pci_bus 0000:02: resource 0 [io  0x8000-0x8fff]
Dec 23 22:49:44 ubuntu kernel: [    2.258849] pci_bus 0000:02: resource 1 [mem 0xbf000000-0xbf1fffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258851] pci_bus 0000:02: resource 2 [mem 0xbf200000-0xbf3fffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    2.258854] pci_bus 0000:03: resource 0 [io  0x9000-0x9fff]
Dec 23 22:49:44 ubuntu kernel: [    2.258856] pci_bus 0000:03: resource 1 [mem 0xf4300000-0xf43fffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258859] pci_bus 0000:03: resource 2 [mem 0xbf400000-0xbf5fffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    2.258861] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
Dec 23 22:49:44 ubuntu kernel: [    2.258863] pci_bus 0000:05: resource 1 [mem 0xf8000000-0xf9ffffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258866] pci_bus 0000:05: resource 2 [mem 0xf4000000-0xf40fffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    2.258868] pci_bus 0000:0d: resource 0 [io  0x3000-0x3fff]
Dec 23 22:49:44 ubuntu kernel: [    2.258870] pci_bus 0000:0d: resource 1 [mem 0xfa000000-0xfbffffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258873] pci_bus 0000:0d: resource 2 [mem 0xf4100000-0xf41fffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    2.258875] pci_bus 0000:15: resource 0 [io  0x4000-0x7fff]
Dec 23 22:49:44 ubuntu kernel: [    2.258877] pci_bus 0000:15: resource 1 [mem 0xf4800000-0xf7ffffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258880] pci_bus 0000:15: resource 2 [mem 0xf0000000-0xf3ffffff 64bit pref]
Dec 23 22:49:44 ubuntu kernel: [    2.258882] pci_bus 0000:15: resource 4 [io  0x0000-0x0cf7]
Dec 23 22:49:44 ubuntu kernel: [    2.258884] pci_bus 0000:15: resource 5 [io  0x0d00-0xffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258886] pci_bus 0000:15: resource 6 [mem 0x000a0000-0x000bffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258888] pci_bus 0000:15: resource 7 [mem 0x000d4000-0x000d7fff]
Dec 23 22:49:44 ubuntu kernel: [    2.258890] pci_bus 0000:15: resource 8 [mem 0x000d8000-0x000dbfff]
Dec 23 22:49:44 ubuntu kernel: [    2.258893] pci_bus 0000:15: resource 9 [mem 0xbf000000-0xfebfffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258895] pci_bus 0000:16: resource 0 [io  0x4000-0x40ff]
Dec 23 22:49:44 ubuntu kernel: [    2.258897] pci_bus 0000:16: resource 1 [io  0x4400-0x44ff]
Dec 23 22:49:44 ubuntu kernel: [    2.258899] pci_bus 0000:16: resource 2 [mem 0xf0000000-0xf3ffffff pref]
Dec 23 22:49:44 ubuntu kernel: [    2.258902] pci_bus 0000:16: resource 3 [mem 0xc0000000-0xc3ffffff]
Dec 23 22:49:44 ubuntu kernel: [    2.258940] NET: Registered protocol family 2
Dec 23 22:49:44 ubuntu kernel: [    2.259009] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Dec 23 22:49:44 ubuntu kernel: [    2.259267] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 23 22:49:44 ubuntu kernel: [    2.259586] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Dec 23 22:49:44 ubuntu kernel: [    2.259730] TCP: Hash tables configured (established 131072 bind 65536)
Dec 23 22:49:44 ubuntu kernel: [    2.259732] TCP reno registered
Dec 23 22:49:44 ubuntu kernel: [    2.259735] UDP hash table entries: 512 (order: 2, 16384 bytes)
Dec 23 22:49:44 ubuntu kernel: [    2.259742] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Dec 23 22:49:44 ubuntu kernel: [    2.259815] NET: Registered protocol family 1
Dec 23 22:49:44 ubuntu kernel: [    2.259828] pci 0000:00:02.0: Boot video device
Dec 23 22:49:44 ubuntu kernel: [    2.260054] PCI: CLS 64 bytes, default 64
Dec 23 22:49:44 ubuntu kernel: [    2.260078] Simple Boot Flag at 0x35 set to 0x1
Dec 23 22:49:44 ubuntu kernel: [    2.260260] cpufreq-nforce2: No nForce2 chipset.
Dec 23 22:49:44 ubuntu kernel: [    2.260292] Scanning for low memory corruption every 60 seconds
Dec 23 22:49:44 ubuntu kernel: [    2.260412] audit: initializing netlink socket (disabled)
Dec 23 22:49:44 ubuntu kernel: [    2.260419] type=2000 audit(1293144507.260:1): initialized
Dec 23 22:49:44 ubuntu kernel: [    2.473589] highmem bounce pool size: 64 pages
Dec 23 22:49:44 ubuntu kernel: [    2.473595] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Dec 23 22:49:44 ubuntu kernel: [    2.475198] VFS: Disk quotas dquot_6.5.2
Dec 23 22:49:44 ubuntu kernel: [    2.475281] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Dec 23 22:49:44 ubuntu kernel: [    2.475915] fuse init (API version 7.14)
Dec 23 22:49:44 ubuntu kernel: [    2.476030] msgmni has been set to 1657
Dec 23 22:49:44 ubuntu kernel: [    2.477762] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
Dec 23 22:49:44 ubuntu kernel: [    2.477766] io scheduler noop registered
Dec 23 22:49:44 ubuntu kernel: [    2.477768] io scheduler deadline registered
Dec 23 22:49:44 ubuntu kernel: [    2.477782] io scheduler cfq registered (default)
Dec 23 22:49:44 ubuntu kernel: [    2.477942] pcieport 0000:00:1c.0: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.477995]   alloc irq_desc for 40 on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.477997]   alloc kstat_irqs on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.478011] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
Dec 23 22:49:44 ubuntu kernel: [    2.478123] pcieport 0000:00:1c.1: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.478172]   alloc irq_desc for 41 on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.478174]   alloc kstat_irqs on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.478183] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
Dec 23 22:49:44 ubuntu kernel: [    2.478293] pcieport 0000:00:1c.3: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.478341]   alloc irq_desc for 42 on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.478342]   alloc kstat_irqs on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.478351] pcieport 0000:00:1c.3: irq 42 for MSI/MSI-X
Dec 23 22:49:44 ubuntu kernel: [    2.478453] pcieport 0000:00:1c.4: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.478501]   alloc irq_desc for 43 on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.478502]   alloc kstat_irqs on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.478511] pcieport 0000:00:1c.4: irq 43 for MSI/MSI-X
Dec 23 22:49:44 ubuntu kernel: [    2.478639] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 23 22:49:44 ubuntu kernel: [    2.479140] pciehp 0000:00:1c.0cie04: HPC vendor_id 8086 device_id 2940 ss_vid 17aa ss_did 20f3
Dec 23 22:49:44 ubuntu kernel: [    2.479181] pciehp 0000:00:1c.0cie04: service driver pciehp loaded
Dec 23 22:49:44 ubuntu kernel: [    2.479198] pciehp 0000:00:1c.1cie04: HPC vendor_id 8086 device_id 2942 ss_vid 17aa ss_did 20f3
Dec 23 22:49:44 ubuntu kernel: [    2.479233] pciehp 0000:00:1c.1cie04: service driver pciehp loaded
Dec 23 22:49:44 ubuntu kernel: [    2.479249] pciehp 0000:00:1c.3cie04: HPC vendor_id 8086 device_id 2946 ss_vid 17aa ss_did 20f3
Dec 23 22:49:44 ubuntu kernel: [    2.479283] pciehp 0000:00:1c.3cie04: service driver pciehp loaded
Dec 23 22:49:44 ubuntu kernel: [    2.479300] pciehp 0000:00:1c.4cie04: HPC vendor_id 8086 device_id 2948 ss_vid 17aa ss_did 20f3
Dec 23 22:49:44 ubuntu kernel: [    2.479334] pciehp 0000:00:1c.4cie04: service driver pciehp loaded
Dec 23 22:49:44 ubuntu kernel: [    2.479344] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 23 22:49:44 ubuntu kernel: [    2.479447] intel_idle: MWAIT substates: 0x3122220
Dec 23 22:49:44 ubuntu kernel: [    2.479449] intel_idle: does not run on family 6 model 23
Dec 23 22:49:44 ubuntu kernel: [    2.479686] ACPI: AC Adapter [AC] (on-line)
Dec 23 22:49:44 ubuntu kernel: [    2.479756] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
Dec 23 22:49:44 ubuntu kernel: [    2.479971] ACPI: Lid Switch [LID]
Dec 23 22:49:44 ubuntu kernel: [    2.480025] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
Dec 23 22:49:44 ubuntu kernel: [    2.480030] ACPI: Sleep Button [SLPB]
Dec 23 22:49:44 ubuntu kernel: [    2.480083] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
Dec 23 22:49:44 ubuntu kernel: [    2.480086] ACPI: Power Button [PWRF]
Dec 23 22:49:44 ubuntu kernel: [    2.480374] ACPI: acpi_idle registered with cpuidle
Dec 23 22:49:44 ubuntu kernel: [    2.481429] Freeing initrd memory: 11144k freed
Dec 23 22:49:44 ubuntu kernel: [    2.483511] Monitor-Mwait will be used to enter C-1 state
Dec 23 22:49:44 ubuntu kernel: [    2.483561] Monitor-Mwait will be used to enter C-2 state
Dec 23 22:49:44 ubuntu kernel: [    2.483584] Monitor-Mwait will be used to enter C-3 state
Dec 23 22:49:44 ubuntu kernel: [    2.483590] Marking TSC unstable due to TSC halts in idle
Dec 23 22:49:44 ubuntu kernel: [    2.484239] Switching to clocksource hpet
Dec 23 22:49:44 ubuntu kernel: [    2.532076] thermal LNXTHERM:01: registered as thermal_zone0
Dec 23 22:49:44 ubuntu kernel: [    2.532085] ACPI: Thermal Zone [THM0] (58 C)
Dec 23 22:49:44 ubuntu kernel: [    2.533593] thermal LNXTHERM:02: registered as thermal_zone1
Dec 23 22:49:44 ubuntu kernel: [    2.533601] ACPI: Thermal Zone [THM1] (58 C)
Dec 23 22:49:44 ubuntu kernel: [    2.533681] ERST: Table is not found!
Dec 23 22:49:44 ubuntu kernel: [    2.533823] isapnp: Scanning for PnP cards...
Dec 23 22:49:44 ubuntu kernel: [    2.533954] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec 23 22:49:44 ubuntu kernel: [    2.534338]   alloc irq_desc for 17 on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.534341]   alloc kstat_irqs on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.534348] serial 0000:00:03.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 23 22:49:44 ubuntu kernel: [    2.534418] 0000:00:03.3: ttyS0 at I/O 0x1830 (irq = 17) is a 16550A
Dec 23 22:49:44 ubuntu kernel: [    2.535569] brd: module loaded
Dec 23 22:49:44 ubuntu kernel: [    2.536109] loop: module loaded
Dec 23 22:49:44 ubuntu kernel: [    2.536327]   alloc irq_desc for 18 on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.536329]   alloc kstat_irqs on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.536333] pata_acpi 0000:00:03.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 23 22:49:44 ubuntu kernel: [    2.536362] pata_acpi 0000:00:03.2: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.536372] pata_acpi 0000:00:03.2: PCI INT C disabled
Dec 23 22:49:44 ubuntu kernel: [    2.536738] Fixed MDIO Bus: probed
Dec 23 22:49:44 ubuntu kernel: [    2.536778] PPP generic driver version 2.4.2
Dec 23 22:49:44 ubuntu kernel: [    2.536816] tun: Universal TUN/TAP device driver, 1.6
Dec 23 22:49:44 ubuntu kernel: [    2.536818] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Dec 23 22:49:44 ubuntu kernel: [    2.536897] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 23 22:49:44 ubuntu kernel: [    2.539522] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
Dec 23 22:49:44 ubuntu kernel: [    2.539693] ehci_hcd 0000:00:1a.7: power state changed by ACPI to D0
Dec 23 22:49:44 ubuntu kernel: [    2.539701] ehci_hcd 0000:00:1a.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Dec 23 22:49:44 ubuntu kernel: [    2.539712] ehci_hcd 0000:00:1a.7: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.539716] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Dec 23 22:49:44 ubuntu kernel: [    2.539750] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
Dec 23 22:49:44 ubuntu kernel: [    2.539782] ehci_hcd 0000:00:1a.7: debug port 1
Dec 23 22:49:44 ubuntu kernel: [    2.543660] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
Dec 23 22:49:44 ubuntu kernel: [    2.543679] ehci_hcd 0000:00:1a.7: irq 23, io mem 0xfc226c00
Dec 23 22:49:44 ubuntu kernel: [    2.556532] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
Dec 23 22:49:44 ubuntu kernel: [    2.556704] hub 1-0:1.0: USB hub found
Dec 23 22:49:44 ubuntu kernel: [    2.556709] hub 1-0:1.0: 6 ports detected
Dec 23 22:49:44 ubuntu kernel: [    2.562415] ACPI: Battery Slot [BAT0] (battery present)
Dec 23 22:49:44 ubuntu kernel: [    2.562571] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Dec 23 22:49:44 ubuntu kernel: [    2.562746] ehci_hcd 0000:00:1d.7: power state changed by ACPI to D0
Dec 23 22:49:44 ubuntu kernel: [    2.562753]   alloc irq_desc for 19 on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.562754]   alloc kstat_irqs on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.562759] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 19 (level, low) -> IRQ 19
Dec 23 22:49:44 ubuntu kernel: [    2.562770] ehci_hcd 0000:00:1d.7: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.562773] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Dec 23 22:49:44 ubuntu kernel: [    2.562807] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
Dec 23 22:49:44 ubuntu kernel: [    2.562833] ehci_hcd 0000:00:1d.7: debug port 1
Dec 23 22:49:44 ubuntu kernel: [    2.566702] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
Dec 23 22:49:44 ubuntu kernel: [    2.566716] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfc227000
Dec 23 22:49:44 ubuntu kernel: [    2.580512] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Dec 23 22:49:44 ubuntu kernel: [    2.580608] hub 2-0:1.0: USB hub found
Dec 23 22:49:44 ubuntu kernel: [    2.580612] hub 2-0:1.0: 6 ports detected
Dec 23 22:49:44 ubuntu kernel: [    2.580688] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 23 22:49:44 ubuntu kernel: [    2.580705] uhci_hcd: USB Universal Host Controller Interface driver
Dec 23 22:49:44 ubuntu kernel: [    2.580885] uhci_hcd 0000:00:1a.0: power state changed by ACPI to D0
Dec 23 22:49:44 ubuntu kernel: [    2.581046] uhci_hcd 0000:00:1a.0: power state changed by ACPI to D0
Dec 23 22:49:44 ubuntu kernel: [    2.581051] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Dec 23 22:49:44 ubuntu kernel: [    2.581058] uhci_hcd 0000:00:1a.0: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.581061] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Dec 23 22:49:44 ubuntu kernel: [    2.581096] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
Dec 23 22:49:44 ubuntu kernel: [    2.581131] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
Dec 23 22:49:44 ubuntu kernel: [    2.581242] hub 3-0:1.0: USB hub found
Dec 23 22:49:44 ubuntu kernel: [    2.581246] hub 3-0:1.0: 2 ports detected
Dec 23 22:49:44 ubuntu kernel: [    2.581311] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Dec 23 22:49:44 ubuntu kernel: [    2.581317] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.581321] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Dec 23 22:49:44 ubuntu kernel: [    2.581351] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
Dec 23 22:49:44 ubuntu kernel: [    2.581386] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
Dec 23 22:49:44 ubuntu kernel: [    2.581501] hub 4-0:1.0: USB hub found
Dec 23 22:49:44 ubuntu kernel: [    2.581505] hub 4-0:1.0: 2 ports detected
Dec 23 22:49:44 ubuntu kernel: [    2.581783] uhci_hcd 0000:00:1a.2: power state changed by ACPI to D0
Dec 23 22:49:44 ubuntu kernel: [    2.581954] uhci_hcd 0000:00:1a.2: power state changed by ACPI to D0
Dec 23 22:49:44 ubuntu kernel: [    2.581959]   alloc irq_desc for 22 on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.581961]   alloc kstat_irqs on node -1
Dec 23 22:49:44 ubuntu kernel: [    2.581965] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Dec 23 22:49:44 ubuntu kernel: [    2.581971] uhci_hcd 0000:00:1a.2: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.581975] uhci_hcd 0000:00:1a.2: UHCI Host Controller
Dec 23 22:49:44 ubuntu kernel: [    2.582007] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
Dec 23 22:49:44 ubuntu kernel: [    2.582042] uhci_hcd 0000:00:1a.2: irq 22, io base 0x000018a0
Dec 23 22:49:44 ubuntu kernel: [    2.582157] hub 5-0:1.0: USB hub found
Dec 23 22:49:44 ubuntu kernel: [    2.582161] hub 5-0:1.0: 2 ports detected
Dec 23 22:49:44 ubuntu kernel: [    2.582410] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Dec 23 22:49:44 ubuntu kernel: [    2.582577] uhci_hcd 0000:00:1d.0: power state changed by ACPI to D0
Dec 23 22:49:44 ubuntu kernel: [    2.582582] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 23 22:49:44 ubuntu kernel: [    2.582589] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.582592] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Dec 23 22:49:44 ubuntu kernel: [    2.582627] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
Dec 23 22:49:44 ubuntu kernel: [    2.582661] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018c0
Dec 23 22:49:44 ubuntu kernel: [    2.582772] hub 6-0:1.0: USB hub found
Dec 23 22:49:44 ubuntu kernel: [    2.582776] hub 6-0:1.0: 2 ports detected
Dec 23 22:49:44 ubuntu kernel: [    2.582845] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 23 22:49:44 ubuntu kernel: [    2.582851] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.582855] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Dec 23 22:49:44 ubuntu kernel: [    2.582890] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
Dec 23 22:49:44 ubuntu kernel: [    2.582924] uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018e0
Dec 23 22:49:44 ubuntu kernel: [    2.583038] hub 7-0:1.0: USB hub found
Dec 23 22:49:44 ubuntu kernel: [    2.583042] hub 7-0:1.0: 2 ports detected
Dec 23 22:49:44 ubuntu kernel: [    2.583104] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 23 22:49:44 ubuntu kernel: [    2.583110] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    2.583114] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Dec 23 22:49:44 ubuntu kernel: [    2.583146] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
Dec 23 22:49:44 ubuntu kernel: [    2.583180] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001c00
Dec 23 22:49:44 ubuntu kernel: [    2.583292] hub 8-0:1.0: USB hub found
Dec 23 22:49:44 ubuntu kernel: [    2.583295] hub 8-0:1.0: 2 ports detected
Dec 23 22:49:44 ubuntu kernel: [    2.583419] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
Dec 23 22:49:44 ubuntu kernel: [    2.591901] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 23 22:49:44 ubuntu kernel: [    2.591906] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 23 22:49:44 ubuntu kernel: [    2.592009] mice: PS/2 mouse device common for all mice
Dec 23 22:49:44 ubuntu kernel: [    2.592155] rtc_cmos 00:07: RTC can wake from S4
Dec 23 22:49:44 ubuntu kernel: [    2.592191] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
Dec 23 22:49:44 ubuntu kernel: [    2.592219] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Dec 23 22:49:44 ubuntu kernel: [    2.592313] device-mapper: uevent: version 1.0.3
Dec 23 22:49:44 ubuntu kernel: [    2.592413] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Dec 23 22:49:44 ubuntu kernel: [    2.592470] device-mapper: multipath: version 1.1.1 loaded
Dec 23 22:49:44 ubuntu kernel: [    2.592473] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec 23 22:49:44 ubuntu kernel: [    2.592597] EISA: Probing bus 0 at eisa.0
Dec 23 22:49:44 ubuntu kernel: [    2.592601] EISA: Cannot allocate resource for mainboard
Dec 23 22:49:44 ubuntu kernel: [    2.592604] Cannot allocate resource for EISA slot 1
Dec 23 22:49:44 ubuntu kernel: [    2.592606] Cannot allocate resource for EISA slot 2
Dec 23 22:49:44 ubuntu kernel: [    2.592608] Cannot allocate resource for EISA slot 3
Dec 23 22:49:44 ubuntu kernel: [    2.592610] Cannot allocate resource for EISA slot 4
Dec 23 22:49:44 ubuntu kernel: [    2.592612] Cannot allocate resource for EISA slot 5
Dec 23 22:49:44 ubuntu kernel: [    2.592614] Cannot allocate resource for EISA slot 6
Dec 23 22:49:44 ubuntu kernel: [    2.592616] Cannot allocate resource for EISA slot 7
Dec 23 22:49:44 ubuntu kernel: [    2.592618] Cannot allocate resource for EISA slot 8
Dec 23 22:49:44 ubuntu kernel: [    2.592620] EISA: Detected 0 cards.
Dec 23 22:49:44 ubuntu kernel: [    2.592754] cpuidle: using governor ladder
Dec 23 22:49:44 ubuntu kernel: [    2.592873] cpuidle: using governor menu
Dec 23 22:49:44 ubuntu kernel: [    2.593163] TCP cubic registered
Dec 23 22:49:44 ubuntu kernel: [    2.593290] NET: Registered protocol family 10
Dec 23 22:49:44 ubuntu kernel: [    2.593654] lo: Disabled Privacy Extensions
Dec 23 22:49:44 ubuntu kernel: [    2.593874] NET: Registered protocol family 17
Dec 23 22:49:44 ubuntu kernel: [    2.596820] Using IPI No-Shortcut mode
Dec 23 22:49:44 ubuntu kernel: [    2.596894] PM: Resume from disk failed.
Dec 23 22:49:44 ubuntu kernel: [    2.596905] registered taskstats version 1
Dec 23 22:49:44 ubuntu kernel: [    2.597295]   Magic number: 6:887:856
Dec 23 22:49:44 ubuntu kernel: [    2.597371] rtc_cmos 00:07: setting system clock to 2010-12-23 22:48:28 UTC (129314450
Dec 23 22:49:44 ubuntu kernel: [    2.597374] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 23 22:49:44 ubuntu kernel: [    2.597375] EDD information not available.
Dec 23 22:49:44 ubuntu kernel: [    2.599578] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
Dec 23 22:49:44 ubuntu kernel: [    2.868539] usb 1-6: new high speed USB device using ehci_hcd and address 2
Dec 23 22:49:44 ubuntu kernel: [    2.889408] isapnp: No Plug & Play device found
Dec 23 22:49:44 ubuntu kernel: [    2.889465] Freeing unused kernel memory: 684k freed
Dec 23 22:49:44 ubuntu kernel: [    2.889842] Write protecting the kernel text: 4932k
Dec 23 22:49:44 ubuntu kernel: [    2.889896] Write protecting the kernel read-only data: 1976k
Dec 23 22:49:44 ubuntu kernel: [    2.908680] udev[89]: starting version 163
Dec 23 22:49:44 ubuntu kernel: [    2.991819] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k4
Dec 23 22:49:44 ubuntu kernel: [    2.991822] e1000e: Copyright (c) 1999 - 2009 Intel Corporation.
Dec 23 22:49:44 ubuntu kernel: [    2.991854] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Dec 23 22:49:44 ubuntu kernel: [    2.991866] e1000e 0000:00:19.0: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    3.002548] Linux agpgart interface v0.103
Dec 23 22:49:44 ubuntu kernel: [    3.019489] sdhci: Secure Digital Host Controller Interface driver
Dec 23 22:49:44 ubuntu kernel: [    3.019492] sdhci: Copyright(c) Pierre Ossman
Dec 23 22:49:44 ubuntu kernel: [    3.030411]   alloc irq_desc for 44 on node -1
Dec 23 22:49:44 ubuntu kernel: [    3.030415]   alloc kstat_irqs on node -1
Dec 23 22:49:44 ubuntu kernel: [    3.030429] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
Dec 23 22:49:44 ubuntu kernel: [    3.046228] sdhci-pci 0000:15:00.2: SDHCI controller found [1180:0822] (rev 21)
Dec 23 22:49:44 ubuntu kernel: [    3.046250] sdhci-pci 0000:15:00.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 23 22:49:44 ubuntu kernel: [    3.047271] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
Dec 23 22:49:44 ubuntu kernel: [    3.048352] Registered led device: mmc0::
Dec 23 22:49:44 ubuntu kernel: [    3.049376] mmc0: SDHCI controller on PCI [0000:15:00.2] using DMA
Dec 23 22:49:44 ubuntu kernel: [    3.051373] firewire_ohci 0000:15:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 23 22:49:44 ubuntu kernel: [    3.148058] firewire_ohci: Added fw-ohci device 0000:15:00.1, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x0
Dec 23 22:49:44 ubuntu kernel: [    3.304490] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:24:7e:6d:22:14
Dec 23 22:49:44 ubuntu kernel: [    3.304493] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
Dec 23 22:49:44 ubuntu kernel: [    3.304533] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: 1008ff-0ff
Dec 23 22:49:44 ubuntu kernel: [    3.304644] agpgart-intel 0000:00:00.0: Intel GM45 Chipset
Dec 23 22:49:44 ubuntu kernel: [    3.306169] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
Dec 23 22:49:44 ubuntu kernel: [    3.326614] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Dec 23 22:49:44 ubuntu kernel: [    3.326653] ahci 0000:00:1f.2: version 3.0
Dec 23 22:49:44 ubuntu kernel: [    3.326670] ahci 0000:00:1f.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Dec 23 22:49:44 ubuntu kernel: [    3.326709]   alloc irq_desc for 45 on node -1
Dec 23 22:49:44 ubuntu kernel: [    3.326710]   alloc kstat_irqs on node -1
Dec 23 22:49:44 ubuntu kernel: [    3.326721] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
Dec 23 22:49:44 ubuntu kernel: [    3.326763] ahci: SSS flag set, parallel bus scan disabled
Dec 23 22:49:44 ubuntu kernel: [    3.326793] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x3 impl SATA mode
Dec 23 22:49:44 ubuntu kernel: [    3.326796] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc sxs 
Dec 23 22:49:44 ubuntu kernel: [    3.326802] ahci 0000:00:1f.2: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    3.327045] scsi0 : ahci
Dec 23 22:49:44 ubuntu kernel: [    3.327195] scsi1 : ahci
Dec 23 22:49:44 ubuntu kernel: [    3.327351] scsi2 : ahci
Dec 23 22:49:44 ubuntu kernel: [    3.327441] scsi3 : ahci
Dec 23 22:49:44 ubuntu kernel: [    3.328177] ata1: SATA max UDMA/133 abar m2048@0xfc226000 port 0xfc226100 irq 45
Dec 23 22:49:44 ubuntu kernel: [    3.328181] ata2: SATA max UDMA/133 abar m2048@0xfc226000 port 0xfc226180 irq 45
Dec 23 22:49:44 ubuntu kernel: [    3.328183] ata3: DUMMY
Dec 23 22:49:44 ubuntu kernel: [    3.328184] ata4: DUMMY
Dec 23 22:49:44 ubuntu kernel: [    3.428077] [drm] Initialized drm 1.1.0 20060810
Dec 23 22:49:44 ubuntu kernel: [    3.640156] firewire_core: created device fw0: GUID 00061b032a406806, S400
Dec 23 22:49:44 ubuntu kernel: [    3.648079] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Dec 23 22:49:44 ubuntu kernel: [    3.649314] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
Dec 23 22:49:44 ubuntu kernel: [    3.649319] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Dec 23 22:49:44 ubuntu kernel: [    3.649534] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
Dec 23 22:49:44 ubuntu kernel: [    3.649540] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Dec 23 22:49:44 ubuntu kernel: [    3.650674] ata1.00: ATA-8: HITACHI HTS545025B9A300, PB2ZC61H, max UDMA/100
Dec 23 22:49:44 ubuntu kernel: [    3.650678] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Dec 23 22:49:44 ubuntu kernel: [    3.652100] ata1.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
Dec 23 22:49:44 ubuntu kernel: [    3.652105] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
Dec 23 22:49:44 ubuntu kernel: [    3.652301] ata1.00: ACPI cmd ef/5f:00:00:00:00:a0 (SET FEATURES) succeeded
Dec 23 22:49:44 ubuntu kernel: [    3.652305] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Dec 23 22:49:44 ubuntu kernel: [    3.653468] ata1.00: configured for UDMA/100
Dec 23 22:49:44 ubuntu kernel: [    3.671158] ata1.00: configured for UDMA/100
Dec 23 22:49:44 ubuntu kernel: [    3.671162] ata1: EH complete
Dec 23 22:49:44 ubuntu kernel: [    3.671358] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS54502 PB2Z PQ: 0 ANSI: 5
Dec 23 22:49:44 ubuntu kernel: [    3.671500] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 23 22:49:44 ubuntu kernel: [    3.671585] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
Dec 23 22:49:44 ubuntu kernel: [    3.671633] sd 0:0:0:0: [sda] Write Protect is off
Dec 23 22:49:44 ubuntu kernel: [    3.671636] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 23 22:49:44 ubuntu kernel: [    3.671656] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 23 22:49:44 ubuntu kernel: [    3.671786]  sda:
Dec 23 22:49:44 ubuntu kernel: [    3.988114] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 23 22:49:44 ubuntu kernel: [    3.990551] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
Dec 23 22:49:44 ubuntu kernel: [    3.991193] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
Dec 23 22:49:44 ubuntu kernel: [    3.992449] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE MU10N, 1.05, max UDMA/33
Dec 23 22:49:44 ubuntu kernel: [    3.996739] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
Dec 23 22:49:44 ubuntu kernel: [    3.997093] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
Dec 23 22:49:44 ubuntu kernel: [    3.998168] ata2.00: configured for UDMA/33
Dec 23 22:49:44 ubuntu kernel: [    4.005720]  sda1 sda2 sda3 sda4 <
Dec 23 22:49:44 ubuntu kernel: [    4.020438] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD MU10N     1.05 PQ: 0 ANSI: 5
Dec 23 22:49:44 ubuntu kernel: [    4.021934] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
Dec 23 22:49:44 ubuntu kernel: [    4.021938] Uniform CD-ROM driver Revision: 3.20
Dec 23 22:49:44 ubuntu kernel: [    4.022067] sr 1:0:0:0: Attached scsi CD-ROM sr0
Dec 23 22:49:44 ubuntu kernel: [    4.022133] sr 1:0:0:0: Attached scsi generic sg1 type 5
Dec 23 22:49:44 ubuntu kernel: [    4.052943]  sda5 sda6 sda7 sda8 sda9 sda10 >
Dec 23 22:49:44 ubuntu kernel: [    4.158035] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 23 22:49:44 ubuntu kernel: [    4.181030] i915 0000:00:02.0: power state changed by ACPI to D0
Dec 23 22:49:44 ubuntu kernel: [    4.181068] i915 0000:00:02.0: power state changed by ACPI to D0
Dec 23 22:49:44 ubuntu kernel: [    4.181075] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 23 22:49:44 ubuntu kernel: [    4.181079] i915 0000:00:02.0: setting latency timer to 64
Dec 23 22:49:44 ubuntu kernel: [    4.216203]   alloc irq_desc for 46 on node -1
Dec 23 22:49:44 ubuntu kernel: [    4.216207]   alloc kstat_irqs on node -1
Dec 23 22:49:44 ubuntu kernel: [    4.216215] i915 0000:00:02.0: irq 46 for MSI/MSI-X
Dec 23 22:49:44 ubuntu kernel: [    4.216227] [drm] set up 31M of stolen space
Dec 23 22:49:44 ubuntu kernel: [    4.346277] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Dec 23 22:49:44 ubuntu kernel: [    4.700102] Skipping EDID probe due to cached edid
Dec 23 22:49:44 ubuntu kernel: [    4.892093] Console: switching to colour frame buffer device 160x50
Dec 23 22:49:44 ubuntu kernel: [    4.895586] fb0: inteldrmfb frame buffer device
Dec 23 22:49:44 ubuntu kernel: [    4.895588] drm: registered panic notifier
Dec 23 22:49:44 ubuntu kernel: [    4.895591] Slow work thread pool: Starting up
Dec 23 22:49:44 ubuntu kernel: [    4.895687] Slow work thread pool: Ready
Dec 23 22:49:44 ubuntu kernel: [    4.899153] acpi device:01: registered as cooling_device2
Dec 23 22:49:44 ubuntu kernel: [    4.899433] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input4
Dec 23 22:49:44 ubuntu kernel: [    4.899471] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
Dec 23 22:49:44 ubuntu kernel: [    4.899512] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Dec 23 22:49:44 ubuntu kernel: [    6.276109] Skipping EDID probe due to cached edid
Dec 23 22:49:44 ubuntu kernel: [    6.413640] Btrfs loaded
Dec 23 22:49:44 ubuntu kernel: [    6.418502] xor: automatically using best checksumming function: pIII_sse
Dec 23 22:49:44 ubuntu kernel: [    6.436021]    pIII_sse  :  9072.000 MB/sec
Dec 23 22:49:44 ubuntu kernel: [    6.436023] xor: using function: pIII_sse (9072.000 MB/sec)
Dec 23 22:49:44 ubuntu kernel: [    6.438374] device-mapper: dm-raid45: initialized v0.2594b
Dec 23 22:49:44 ubuntu kernel: [    8.114825] EXT3-fs: barriers not enabled
Dec 23 22:49:44 ubuntu kernel: [    8.124570] kjournald starting.  Commit interval 5 seconds
Dec 23 22:49:44 ubuntu kernel: [    8.124621] EXT3-fs (sda5): mounted filesystem with ordered data mode
Dec 23 22:49:44 ubuntu kernel: [    8.224560] EXT3-fs: barriers not enabled
Dec 23 22:49:44 ubuntu kernel: [    8.303302] kjournald starting.  Commit interval 5 seconds
Dec 23 22:49:44 ubuntu kernel: [    8.303351] EXT3-fs (sda6): mounted filesystem with ordered data mode
Dec 23 22:49:44 ubuntu kernel: [    8.465747] EXT3-fs: barriers not enabled
Dec 23 22:49:44 ubuntu kernel: [    8.477862] kjournald starting.  Commit interval 5 seconds
Dec 23 22:49:44 ubuntu kernel: [    8.477924] EXT3-fs (sda7): mounted filesystem with ordered data mode
Dec 23 22:49:44 ubuntu kernel: [    9.018346] EXT3-fs: barriers not enabled
Dec 23 22:49:44 ubuntu kernel: [    9.030787] kjournald starting.  Commit interval 5 seconds
Dec 23 22:49:44 ubuntu kernel: [    9.030857] EXT3-fs (sda9): mounted filesystem with ordered data mode
Dec 23 22:49:44 ubuntu kernel: [   10.030593] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 23 22:49:44 ubuntu kernel: [   10.030599] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Dec 23 22:49:44 ubuntu kernel: [   10.030605] Info fld=0x56ae6, ILI
Dec 23 22:49:44 ubuntu kernel: [   10.030607] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Dec 23 22:49:44 ubuntu kernel: [   10.030614] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
Dec 23 22:49:44 ubuntu kernel: [   10.030627] end_request: I/O error, dev sr0, sector 1420184
Dec 23 22:49:44 ubuntu kernel: [   10.030630] Buffer I/O error on device sr0, logical block 177523
Dec 23 22:49:44 ubuntu kernel: [   10.033832] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 23 22:49:44 ubuntu kernel: [   10.033836] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Dec 23 22:49:44 ubuntu kernel: [   10.033841] Info fld=0x56ae6, ILI
Dec 23 22:49:44 ubuntu kernel: [   10.033843] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Dec 23 22:49:44 ubuntu kernel: [   10.033849] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
Dec 23 22:49:44 ubuntu kernel: [   10.033860] end_request: I/O error, dev sr0, sector 1420184
Dec 23 22:49:44 ubuntu kernel: [   10.033863] Buffer I/O error on device sr0, logical block 177523
Dec 23 22:49:44 ubuntu kernel: [   10.036022] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 23 22:49:44 ubuntu kernel: [   10.036026] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Dec 23 22:49:44 ubuntu kernel: [   10.036031] Info fld=0x56ae6, ILI
Dec 23 22:49:44 ubuntu kernel: [   10.036033] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Dec 23 22:49:44 ubuntu kernel: [   10.036039] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
Dec 23 22:49:44 ubuntu kernel: [   10.036051] end_request: I/O error, dev sr0, sector 1420184
Dec 23 22:49:44 ubuntu kernel: [   10.036054] Buffer I/O error on device sr0, logical block 177523
Dec 23 22:49:44 ubuntu kernel: [   10.038181] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 23 22:49:44 ubuntu kernel: [   10.038186] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Dec 23 22:49:44 ubuntu kernel: [   10.038191] Info fld=0x56ae6, ILI
Dec 23 22:49:44 ubuntu kernel: [   10.038193] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Dec 23 22:49:44 ubuntu kernel: [   10.038200] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
Dec 23 22:49:44 ubuntu kernel: [   10.038211] end_request: I/O error, dev sr0, sector 1420184
Dec 23 22:49:44 ubuntu kernel: [   10.038214] Buffer I/O error on device sr0, logical block 177523
Dec 23 22:49:44 ubuntu kernel: [   10.039946] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 23 22:49:44 ubuntu kernel: [   10.039951] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Dec 23 22:49:44 ubuntu kernel: [   10.039956] Info fld=0x56ae6, ILI
Dec 23 22:49:44 ubuntu kernel: [   10.039958] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Dec 23 22:49:44 ubuntu kernel: [   10.039964] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
Dec 23 22:49:44 ubuntu kernel: [   10.039975] end_request: I/O error, dev sr0, sector 1420184
Dec 23 22:49:44 ubuntu kernel: [   10.039978] Buffer I/O error on device sr0, logical block 177523
Dec 23 22:49:44 ubuntu kernel: [   10.042165] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 23 22:49:44 ubuntu kernel: [   10.042169] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Dec 23 22:49:44 ubuntu kernel: [   10.042174] Info fld=0x56ae6, ILI
Dec 23 22:49:44 ubuntu kernel: [   10.042176] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Dec 23 22:49:44 ubuntu kernel: [   10.042183] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
Dec 23 22:49:44 ubuntu kernel: [   10.042194] end_request: I/O error, dev sr0, sector 1420184
Dec 23 22:49:44 ubuntu kernel: [   10.042197] Buffer I/O error on device sr0, logical block 177523
Dec 23 22:49:44 ubuntu kernel: [   10.044220] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 23 22:49:44 ubuntu kernel: [   10.044225] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Dec 23 22:49:44 ubuntu kernel: [   10.044230] Info fld=0x56ae6, ILI
Dec 23 22:49:44 ubuntu kernel: [   10.044232] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Dec 23 22:49:44 ubuntu kernel: [   10.044243] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
Dec 23 22:49:44 ubuntu kernel: [   10.044251] end_request: I/O error, dev sr0, sector 1420184
Dec 23 22:49:44 ubuntu kernel: [   10.044254] Buffer I/O error on device sr0, logical block 177523
Dec 23 22:49:44 ubuntu kernel: [   10.141057] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 23 22:49:44 ubuntu kernel: [   10.141062] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Dec 23 22:49:44 ubuntu kernel: [   10.141067] Info fld=0x56ae6, ILI
Dec 23 22:49:44 ubuntu kernel: [   10.141069] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Dec 23 22:49:44 ubuntu kernel: [   10.141075] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
Dec 23 22:49:44 ubuntu kernel: [   10.141087] end_request: I/O error, dev sr0, sector 1420184
Dec 23 22:49:44 ubuntu kernel: [   10.141090] Buffer I/O error on device sr0, logical block 177523
Dec 23 22:49:44 ubuntu kernel: [   10.144278] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 23 22:49:44 ubuntu kernel: [   10.144282] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Dec 23 22:49:44 ubuntu kernel: [   10.144288] Info fld=0x56ae6, ILI
Dec 23 22:49:44 ubuntu kernel: [   10.144290] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Dec 23 22:49:44 ubuntu kernel: [   10.144296] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
Dec 23 22:49:44 ubuntu kernel: [   10.144307] end_request: I/O error, dev sr0, sector 1420184
Dec 23 22:49:44 ubuntu kernel: [   10.144310] Buffer I/O error on device sr0, logical block 177523
Dec 23 22:49:44 ubuntu kernel: [   10.146391] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Dec 23 22:49:44 ubuntu kernel: [   10.146396] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
Dec 23 22:49:44 ubuntu kernel: [   10.146401] Info fld=0x56ae6, ILI
Dec 23 22:49:44 ubuntu kernel: [   10.146403] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
Dec 23 22:49:44 ubuntu kernel: [   10.146410] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 05 6a e6 00 00 02 00
Dec 23 22:49:44 ubuntu kernel: [   10.146421] end_request: I/O error, dev sr0, sector 1420184
Dec 23 22:49:44 ubuntu kernel: [   10.146424] Buffer I/O error on device sr0, logical block 177523
Dec 23 22:49:44 ubuntu kernel: [   10.733403] ISO 9660 Extensions: Microsoft Joliet Level 3
Dec 23 22:49:44 ubuntu kernel: [   10.763368] ISO 9660 Extensions: RRIP_1991A
Dec 23 22:49:44 ubuntu kernel: [   10.905128] aufs 2-standalone.tree-35-rcN-20100705
Dec 23 22:49:44 ubuntu kernel: [   10.973425] squashfs: version 4.0 (2009/01/31) Phillip Lougher
Dec 23 22:49:44 ubuntu kernel: [   78.524189] Adding 4581324k swap on /dev/sda10.  Priority:-1 extents:1 across:4581324k 
Dec 23 22:49:46 ubuntu kernel: [   80.915030] udev[1509]: starting version 163
Dec 23 22:49:52 ubuntu kernel: [   86.873569] cfg80211: Calling CRDA to update world regulatory domain
Dec 23 22:49:52 ubuntu kernel: [   86.989779] Synaptics Touchpad, model: 1, fw: 7.0, id: 0x1c0b1, caps: 0xd04791/0xb00000/0x20000
Dec 23 22:49:52 ubuntu kernel: [   86.989783] Synaptics: Clickpad mode enabled
Dec 23 22:49:52 ubuntu kernel: [   86.989787] serio: Synaptics pass-through port at isa0060/serio1/input0
Dec 23 22:49:52 ubuntu kernel: [   87.033203] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
Dec 23 22:49:53 ubuntu kernel: [   87.384094] Linux video capture interface: v2.00
Dec 23 22:49:53 ubuntu kernel: [   88.090622] uvcvideo: Found UVC 1.00 device <unnamed> (17ef:4807)
Dec 23 22:49:53 ubuntu kernel: [   88.094756] input: UVC Camera (17ef:4807) as /devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input6
Dec 23 22:49:53 ubuntu kernel: [   88.094881] usbcore: registered new interface driver uvcvideo
Dec 23 22:49:53 ubuntu kernel: [   88.094884] USB Video Class driver (v0.1.0)
Dec 23 22:49:55 ubuntu kernel: [   89.663467] psmouse serio2: ID: 10 00 64
Dec 23 22:49:55 ubuntu kernel: [   89.848753] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
Dec 23 22:49:55 ubuntu kernel: [   89.904578] e1000e 0000:00:19.0: irq 44 for MSI/MSI-X
Dec 23 22:49:55 ubuntu kernel: [   89.904835] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 23 22:49:55 ubuntu kernel: [   89.998020] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Dec 23 22:49:55 ubuntu kernel: [   89.998024] iwlagn: Copyright(c) 2003-2010 Intel Corporation
Dec 23 22:49:55 ubuntu kernel: [   89.998125] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 23 22:49:55 ubuntu kernel: [   89.998134] iwlagn 0000:03:00.0: setting latency timer to 64
Dec 23 22:49:55 ubuntu kernel: [   89.998326] iwlagn 0000:03:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
Dec 23 22:49:55 ubuntu kernel: [   90.017957] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
Dec 23 22:49:55 ubuntu kernel: [   90.018113]   alloc irq_desc for 47 on node -1
Dec 23 22:49:55 ubuntu kernel: [   90.018115]   alloc kstat_irqs on node -1
Dec 23 22:49:55 ubuntu kernel: [   90.018168] iwlagn 0000:03:00.0: irq 47 for MSI/MSI-X
Dec 23 22:49:56 ubuntu kernel: [   90.216517] yenta_cardbus 0000:15:00.0: CardBus bridge found [17aa:20c6]
Dec 23 22:49:56 ubuntu kernel: [   90.344868] yenta_cardbus 0000:15:00.0: ISA IRQ mask 0x0cb8, PCI irq 16
Dec 23 22:49:56 ubuntu kernel: [   90.344873] yenta_cardbus 0000:15:00.0: Socket status: 30000006
Dec 23 22:49:56 ubuntu kernel: [   90.344884] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [io  0x4000-0x7fff]
Dec 23 22:49:56 ubuntu kernel: [   90.344887] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x4000-0x7fff: excluding 0x4000-0x40ff 0x4400-0x44ff
Dec 23 22:49:56 ubuntu kernel: [   90.365857] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [mem 0xf4800000-0xf7ffffff]
Dec 23 22:49:56 ubuntu kernel: [   90.365860] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf4800000-0xf7ffffff: excluding 0xf4800000-0xf4b7ffff
Dec 23 22:49:56 ubuntu kernel: [   90.365874] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [mem 0xf0000000-0xf3ffffff 64bit pref]
Dec 23 22:49:56 ubuntu kernel: [   90.365876] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf0000000-0xf3ffffff: excluding 0xf0000000-0xf3ffffff
Dec 23 22:49:56 ubuntu kernel: [   90.637410] Non-volatile memory driver v1.3
Dec 23 22:49:57 ubuntu kernel: [   91.652593] thinkpad_acpi: ThinkPad ACPI Extras v0.24
Dec 23 22:49:57 ubuntu kernel: [   91.652596] thinkpad_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
Dec 23 22:49:57 ubuntu kernel: [   91.652598] thinkpad_acpi: ThinkPad BIOS 6FET66WW (2.16 ), EC 7VHT12WW-1.01
Dec 23 22:49:57 ubuntu kernel: [   91.652600] thinkpad_acpi: Lenovo ThinkPad T500, model 2242CTO
Dec 23 22:49:57 ubuntu kernel: [   91.653923] thinkpad_acpi: detected a 16-level brightness capable ThinkPad
Dec 23 22:49:57 ubuntu kernel: [   91.654200] thinkpad_acpi: radio switch found; radios are enabled
Dec 23 22:49:57 ubuntu kernel: [   91.654223] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
Dec 23 22:49:57 ubuntu kernel: [   91.654226] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
Dec 23 22:49:57 ubuntu kernel: [   91.657549] Registered led device: tpacpi::thinklight
Dec 23 22:49:57 ubuntu kernel: [   91.657877] Registered led device: tpacpi::power
Dec 23 22:49:57 ubuntu kernel: [   91.658117] Registered led device: tpacpi::standby
Dec 23 22:49:57 ubuntu kernel: [   91.658367] Registered led device: tpacpi::thinkvantage
Dec 23 22:49:57 ubuntu kernel: [   91.661068] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one.
Dec 23 22:49:57 ubuntu kernel: [   91.661182] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
Dec 23 22:49:57 ubuntu kernel: [   91.664113] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input7
Dec 23 22:49:57 ubuntu kernel: [   91.754687] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
Dec 23 22:49:57 ubuntu kernel: [   91.890938] r852 0000:15:00.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Dec 23 22:49:57 ubuntu kernel: [   91.891014] r852: driver loaded succesfully
Dec 23 22:49:58 ubuntu kernel: [   92.782007] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
Dec 23 22:49:58 ubuntu kernel: [   92.783988] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
Dec 23 22:49:58 ubuntu kernel: [   92.789619] cfg80211: World regulatory domain updated:
Dec 23 22:49:58 ubuntu kernel: [   92.789622]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec 23 22:49:58 ubuntu kernel: [   92.789625]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 23 22:49:58 ubuntu kernel: [   92.789628]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 23 22:49:58 ubuntu kernel: [   92.789630]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Dec 23 22:49:58 ubuntu kernel: [   92.789633]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 23 22:49:58 ubuntu kernel: [   92.789635]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Dec 23 22:49:58 ubuntu kernel: [   92.798464]  excluding 0x4d0-0x4d7
Dec 23 22:49:58 ubuntu kernel: [   92.798613] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
Dec 23 22:49:58 ubuntu kernel: [   92.799354] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
Dec 23 22:49:58 ubuntu kernel: [   92.800121] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xd3fff 0xdc000-0xfffff
Dec 23 22:49:58 ubuntu kernel: [   92.800181] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
Dec 23 22:49:58 ubuntu kernel: [   92.800240] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
Dec 23 22:49:58 ubuntu kernel: [   92.800301] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
Dec 23 22:49:59 ubuntu kernel: [   93.368265] IBM TrackPoint firmware: 0x0e, buttons: 3/3
Dec 23 22:49:59 ubuntu kernel: [   93.604795] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input8
Dec 23 22:49:59 ubuntu kernel: [   93.684332] phy0: Selected rate control algorithm 'iwl-agn-rs'
Dec 23 22:49:59 ubuntu kernel: [   94.009068] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec 23 22:50:00 ubuntu kernel: [   94.849154] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Dec 23 22:50:00 ubuntu kernel: [   94.849214]   alloc irq_desc for 48 on node -1
Dec 23 22:50:00 ubuntu kernel: [   94.849216]   alloc kstat_irqs on node -1
Dec 23 22:50:00 ubuntu kernel: [   94.849228] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
Dec 23 22:50:00 ubuntu kernel: [   94.849263] HDA Intel 0000:00:1b.0: setting latency timer to 64
Dec 23 22:50:01 ubuntu kernel: [   95.280628] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Dec 23 22:50:01 ubuntu kernel: [   95.280874] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Dec 23 22:50:01 ubuntu kernel: [   95.281314] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
Dec 23 22:50:01 ubuntu kernel: [   95.281416] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
Dec 23 22:50:03 ubuntu kernel: [   97.585749] lp: driver loaded but no devices found
Dec 23 22:50:04 ubuntu kernel: [   98.543702] ppdev: user-space parallel port driver
Dec 23 22:50:13 ubuntu kernel: [  107.568621] Skipping EDID probe due to cached edid
Dec 23 22:50:13 ubuntu kernel: [  107.612643] Skipping EDID probe due to cached edid
Dec 23 22:50:28 ubuntu kernel: [  122.824107] Skipping EDID probe due to cached edid
Dec 23 22:50:28 ubuntu kernel: [  122.868036] Skipping EDID probe due to cached edid
Dec 23 22:50:28 ubuntu kernel: [  123.076629] Skipping EDID probe due to cached edid
Dec 23 22:50:29 ubuntu kernel: [  123.116042] Skipping EDID probe due to cached edid
Dec 23 22:51:27 ubuntu kernel: [  181.396672] Skipping EDID probe due to cached edid
Dec 23 22:52:21 ubuntu kernel: [  235.201402] JFS: nTxBlock = 8192, nTxLock = 65536
Dec 23 22:52:21 ubuntu kernel: [  235.627255] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Dec 23 22:52:21 ubuntu kernel: [  235.629085] SGI XFS Quota Management subsystem
Dec 23 22:52:39 ubuntu kernel: [  253.136695] NTFS driver 2.1.29 [Flags: R/O MODULE].
Dec 23 22:52:39 ubuntu kernel: [  253.613535] QNX4 filesystem 0.2.3 registered.
Dec 23 22:52:40 ubuntu kernel: [  255.054530] EXT3-fs: barriers not enabled
Dec 23 22:52:40 ubuntu kernel: [  255.064298] kjournald starting.  Commit interval 5 seconds
Dec 23 22:52:40 ubuntu kernel: [  255.064324] EXT3-fs (sda5): mounted filesystem with ordered data mode
Dec 23 22:52:41 ubuntu kernel: [  255.264377] EXT3-fs: barriers not enabled
Dec 23 22:52:41 ubuntu kernel: [  255.309702] kjournald starting.  Commit interval 5 seconds
Dec 23 22:52:41 ubuntu kernel: [  255.309736] EXT3-fs (sda6): mounted filesystem with ordered data mode
Dec 23 22:52:41 ubuntu kernel: [  255.505494] EXT3-fs: barriers not enabled
Dec 23 22:52:41 ubuntu kernel: [  255.517672] kjournald starting.  Commit interval 5 seconds
Dec 23 22:52:41 ubuntu kernel: [  255.517776] EXT3-fs (sda7): mounted filesystem with ordered data mode
Dec 23 22:52:41 ubuntu kernel: [  256.058093] EXT3-fs: barriers not enabled
Dec 23 22:52:41 ubuntu kernel: [  256.070529] kjournald starting.  Commit interval 5 seconds
Dec 23 22:52:41 ubuntu kernel: [  256.070584] EXT3-fs (sda9): mounted filesystem with ordered data mode
Dec 23 22:53:08 ubuntu kernel: [  282.252747] Skipping EDID probe due to cached edid
Dec 23 22:53:08 ubuntu kernel: [  282.296253] Skipping EDID probe due to cached edid
Dec 23 22:53:10 ubuntu kernel: [  284.660051] Skipping EDID probe due to cached edid
Dec 23 22:53:10 ubuntu kernel: [  284.704033] Skipping EDID probe due to cached edid
Dec 23 22:53:10 ubuntu kernel: [  284.760652] Skipping EDID probe due to cached edid
Dec 23 22:53:10 ubuntu kernel: [  284.801099] Skipping EDID probe due to cached edid
Dec 23 22:53:16 ubuntu kernel: [  290.868580] Skipping EDID probe due to cached edid
Dec 23 22:53:18 ubuntu kernel: [  292.748589] Skipping EDID probe due to cached edid
Dec 23 22:57:43 ubuntu kernel: [  557.600823] wlan0: authenticate with 00:25:5e:13:78:78 (try 1)
Dec 23 22:57:43 ubuntu kernel: [  557.602964] wlan0: authenticated
Dec 23 22:57:43 ubuntu kernel: [  557.603013] wlan0: associate with 00:25:5e:13:78:78 (try 1)
Dec 23 22:57:43 ubuntu kernel: [  557.605365] wlan0: RX AssocResp from 00:25:5e:13:78:78 (capab=0x411 status=0 aid=1)
Dec 23 22:57:43 ubuntu kernel: [  557.605373] wlan0: associated
Dec 23 22:57:43 ubuntu kernel: [  557.607479] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 23 17:27:54 ubuntu kernel: [  568.242415] wlan0: no IPv6 routers present

---

### Post by rvchari on 2010-12-23
when i boot to ubuntu using recovery mode, it stops at syscall something like that and a few lines b4 it says kernel pani, can sync !!! ? now what that means ? hope i dont have to install fresh and loose the softwares that i had downloaded earlier !!! (i ll have to start all over aain getting my desktop feel and the apps back !
now i ve gota take to bed and get some sleep, hopefully my morning will dawn with some useful hints to recover my gud ol' buntu !!!

---

### Post by amsterdamharu on 2010-12-23
Sorry but the kernel log you posted is from the live CD session, I meant you should post the one from your normal boot, the one that is on your harddisk (/dev/sda5).

And please wrap them in code tags (select the text and press the # button on this forum).

```
Something like this
```

---

### Post by rvchari on 2010-12-23
whats the command line for that ?

---

### Post by amsterdamharu on 2010-12-23
I don't understand you, the command line for what?

Wrapping your post in code tags is easy, go to your prefious post and  select edit. in the beginning of the post type &#91;code] at the end  type &#91;/code].

To see the kernel log of the system that booted from harddisk you can do the following:
Boot from the live cd (you posted the kernel log from this one but this isn't failing)
Press alt + F2 and type gnome-terminal and click run
Copy and paste the following in the terminal (that black window you've just opened):
```
cd /media/
sudo mkdir sda5
sudo mount /dev/sda5 sda5
gedit sda5/var/log/kern.log
```A white window should open now with  lots of text, can you copy and paste that text to this forum or if any  error occurs can you copy these errors from terminal? 
And please wrap it in code tags when you post it so it's easier to read.

---

### Post by rvchari on 2010-12-23
thanks buddy, but now if i do that command i dont think u ll get that log. i had lots of pending work to do so i went for an over write of the / files on my dev/sda5. it did install and when i was asked to create user name, i created a fresh user name lest i dont land into trouble when fresh config takes place. now i m in that fresh user id and i can see my home folder too. i can access using sudo but can u guide me how to log on to my id ? it saiys uid does not exist even when i m able to browse the files using nautilus from the new user window.
i think if i can log on to my user account things will fall into place with just a few tweaks and add ons whose deb and installer lies in my folder

---

### Post by amsterdamharu on 2010-12-24
You did a fresh install and mounted /dev/sda6 as /home?

You could change ownership for your home directory to the user you are now using "lest" is it?

I guess you need to rename the directory "your_old_user_name" to "lest" and then change ownership. What directories are there in /home?

---

### Post by rvchari on 2010-12-25
i had posted a reply to this earlier too, donno where it got lost !!
nyways, here i repeat. i created a new user (as i was prompted to create one and i didnt give my old id lest i loose something from there) then from that user, i accessed my folder, transfered the data and then issued a userdel for my old id and then i re-created it. now everything seems to fall in place.

perhaps some start up scripts or some .files got corrupted? wud love to learn more on what went wrong !!!

---

### Post by dino99 on 2010-12-25
add on the boot line: noacpi and/or nomodeset (you can remove "quiet splash" too, that way you can read more comments and know whats wrong)

---

