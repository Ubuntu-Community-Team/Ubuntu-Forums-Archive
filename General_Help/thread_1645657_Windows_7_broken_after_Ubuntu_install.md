---
title: "Windows 7 broken after Ubuntu install"
date: 2010-12-14
forum: General Help
---

### Post by Toktikweb on 2010-12-14
I have installed Grub2 over /dev/sda1 (Windows 7). At this moment from Grub Menu Ubuntu boots normally, but as I understand Windows 7 bootloader is dead.

I have reinstalled Grub2 from LiveCD to /dev/sda. But problem with still Windows 7 exist.

As I understand I need to enter Windows 7 Recovery Console mode and run following commands
```
bootrec.exe /fixboot
```and
```
bootrec.exe /fixmbr
```Any alternative method to do this from Ubuntu? And please tell me what does fixboot and what does fixmbr.

---

### Post by Quackers on 2010-12-14
Those are commands to be run from the command prompt in the recovery environment of the Windows repair disc.
If you have a Windows repair disc you should be able to fix your boot problem by running the "repair my system" and running "startup repair". It can take up to 3 runs to fix it.

---

### Post by wilee-nilee on 2010-12-14
> **Quackers said:**
> Those are commands to be run from the command prompt in the recovery environment of the Windows repair disc.
If you have a Windows repair disc you should be able to fix your boot problem by running the "repair my system" and running "startup repair". It can take up to 3 runs to fix it.

Walks like a duck, talks like a duck whatta think about the bootscript here.;)

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

### Post by Toktikweb on 2010-12-14
@Quackers, I don't want to replace grub with Windows loader. So, /fixmbr is needed? As I know it is sets Master Boot Loader.

I'm newbie in Ubuntu and sorry for my english :)

Here is  Boot Info Script generated RESULTS.txt
```

                Boot Info Script 0.55    dated February 15th, 2010                     
 
============================= Boot Info Summary: ============================== 
 
 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 505377176  
    of the same hard drive for core.img, but core.img can not be found at this  
    location. 
 
sda1: _________________________________________________________________________ 
 
    File system:       ntfs 
    Boot sector type:  Windows Vista/7 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:  Windows 7 
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr 
 
sda2: _________________________________________________________________________ 
 
    File system:       Extended Partition 
    Boot sector type:  Unknown 
    Boot sector info:   
 
sda5: _________________________________________________________________________ 
 
    File system:       ntfs 
    Boot sector type:  Windows XP 
    Boot sector info:  According to the info in the boot sector, sda5 starts  
                       at sector 10. But according to the info from fdisk,  
                       sda5 starts at sector 204799750. 
    Operating System:   
    Boot files/dirs:    
 
sda6: _________________________________________________________________________ 
 
    File system:       ntfs 
    Boot sector type:  Windows XP 
    Boot sector info:  According to the info in the boot sector, sda6 starts  
                       at sector 10. But according to the info from fdisk,  
                       sda6 starts at sector 511999360. 
    Operating System:   
    Boot files/dirs:    
 
sda7: _________________________________________________________________________ 
 
    File system:       swap 
    Boot sector type:  - 
    Boot sector info:   
 
sda8: _________________________________________________________________________ 
 
    File system:       ext4 
    Boot sector type:  - 
    Boot sector info:   
    Operating System:  Ubuntu 10.10 
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img 
 
=========================== Drive/Partition Info: ============================= 
 
Drive: sda ___________________ _____________________________________________________ 
 
Disk /dev/sda: 500.1 GB, 500107862016 bytes 
87 heads, 10 sectors/track, 1122727 cylinders, total 976773168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
 
Partition  Boot         Start           End          Size  Id System 
 
/dev/sda1    *             10   204,799,739   204,799,730   7 HPFS/NTFS 
/dev/sda2         204,799,748   976,770,749   771,971,002   f W95 Ext d (LBA) 
/dev/sda5         204,799,750   478,868,879   274,069,130   7 HPFS/NTFS 
/dev/sda6         511,999,360   976,770,749   464,771,390   7 HPFS/NTFS 
/dev/sda7         478,869,504   479,868,927       999,424  82 Linux swap / Solaris 
/dev/sda8         479,870,976   511,997,951    32,126,976  83 Linux 
 
 
blkid -c /dev/null: ____________________________________________________________ 
 
Device           UUID                                   TYPE       LABEL                          
 
/dev/sda1        5CB62892B6286EA8                       ntfs                                      
/dev/sda2: PTTYPE="dos"  
/dev/sda5        A21885E51885B935                       ntfs                                      
/dev/sda6        DE687E84687E5B6B                       ntfs                                      
/dev/sda7        1fc9bb7b-0370-498e-9a9a-98392870533a   swap                                      
/dev/sda8        c3cd4700-940d-49bc-a573-15453002f55d   ext4                                      
/dev/sda: PTTYPE="dos"  
 
============================ "mount | grep ^/dev  output: =========================== 
 
Device           Mount_Point              Type       Options 
 
/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=0) 
/dev/sda6        /media/DE687E84687E5B6B  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) 
 
 
=========================== sda8/boot/grub/grub.cfg: =========================== 
 
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
set root='(hd0,msdos8)' 
search --no-floppy --fs-uuid --set c3cd4700-940d-49bc-a573-15453002f55d 
if loadfont /usr/share/grub/unicode.pf2 ; then 
  set gfxmode=640x480 
  load_video 
  insmod gfxterm 
fi 
terminal_output gfxterm 
insmod part_msdos 
insmod ext2 
set root='(hd0,msdos8)' 
search --no-floppy --fs-uuid --set c3cd4700-940d-49bc-a573-15453002f55d 
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os { 
    recordfail 
    insmod part_msdos 
    insmod ext2 
    set root='(hd0,msdos8)' 
    search --no-floppy --fs-uuid --set c3cd4700-940d-49bc-a573-15453002f55d 
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=c3cd4700-940d-49bc-a573-15453002f55d ro   quiet splash 
    initrd    /boot/initrd.img-2.6.35-23-generic-pae 
} 
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { 
    recordfail 
    insmod part_msdos 
    insmod ext2 
    set root='(hd0,msdos8)' 
    search --no-floppy --fs-uuid --set c3cd4700-940d-49bc-a573-15453002f55d 
    echo    'Loading Linux 2.6.35-23-generic-pae ...' 
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=c3cd4700-940d-49bc-a573-15453002f55d ro single  
    echo    'Loading initial ramdisk ...' 
    initrd    /boot/initrd.img-2.6.35-23-generic-pae 
} 
### END /etc/grub.d/10_linux ### 
 
### BEGIN /etc/grub.d/20_linux_xen ### 
### END /etc/grub.d/20_linux_xen ### 
 
### BEGIN /etc/grub.d/20_memtest86+ ### 
menuentry "Memory test (memtest86+)" { 
    insmod part_msdos 
    insmod ext2 
    set root='(hd0,msdos8)' 
    search --no-floppy --fs-uuid --set c3cd4700-940d-49bc-a573-15453002f55d 
    linux16    /boot/memtest86+.bin 
} 
menuentry "Memory test (memtest86+, serial console 115200)" { 
    insmod part_msdos 
    insmod ext2 
    set root='(hd0,msdos8)' 
    search --no-floppy --fs-uuid --set c3cd4700-940d-49bc-a573-15453002f55d 
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8 
} 
### END /etc/grub.d/20_memtest86+ ### 
 
### BEGIN /etc/grub.d/30_os-prober ### 
menuentry "Windows 7 (loader) (on /dev/sda1)" { 
    insmod part_msdos 
    insmod ntfs 
    set root='(hd0,msdos1)' 
    search --no-floppy --fs-uuid --set 5cb62892b6286ea8 
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
 
=============================== sda8/etc/fstab: =============================== 
 
# /etc/fstab: static file system information. 
# 
# Use 'blkid -o value -s UUID' to print the universally unique identifier 
# for a device; this may be used with UUID= as a more robust way to name 
# devices that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
proc            /proc           proc    nodev,noexec,nosuid 0       0 
# / was on /dev/sda8 during installation 
UUID=c3cd4700-940d-49bc-a573-15453002f55d /               ext4    errors=remount-ro 0       1 
# swap was on /dev/sda7 during installation 
UUID=1fc9bb7b-0370-498e-9a9a-98392870533a none            swap    sw              0       0 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 
 
=================== sda8: Location of files loaded by Grub: =================== 
 
 
 258.7GB: boot/grub/core.img 
 257.3GB: boot/grub/grub.cfg 
 246.5GB: boot/initrd.img-2.6.35-23-generic-pae 
 258.9GB: boot/vmlinuz-2.6.35-23-generic-pae 
 246.5GB: initrd.img 
 258.9GB: vmlinuz 
=========================== Unknown MBRs/Boot Sectors/etc ======================= 
 
Unknown BootLoader  on sda2 
 
00000000  f8 b0 db 7c 15 08 19 f9  f0 dc 04 a2 02 31 cc f9  |...|.........1..| 
00000010  c0 9c 5b 06 65 f9 40 dd  04 a1 02 31 07 7c 17 01  |..[.e.@....1.|..| 
00000020  a8 02 31 e6 7c 43 5d 00  e8 dc 00 09 f6 f8 c0 dc  |..1.|C].........| 
00000030  04 af 02 31 f3 f7 90 db  7c 4a 01 b6 f7 50 db 7c  |...1....|J...P.|| 
00000040  53 01 b1 f6 20 da 7d 00  b3 7c 00 04 c1 02 31 30  |S... .}..|....10| 
00000050  f5 70 d8 7d 45 0e 7c 2b  5c 45 01 f1 f4 20 d8 7c  |.p.}E.|+\E... .|| 
00000060  3f 01 8f f5 d0 d8 7c 64  7c 8a f4 8e 01 6a cf 6e  |?.....|d|....j.n| 
00000070  87 28 d4 11 00 2e 03 8d  0d 38 b3 4b 31 a6 03 83  |.(.......8.K1...| 
00000080  0d 38 d8 4a b1 a3 03 73  0d 38 5c 49 51 9f 03 72  |.8.J...s.8\IQ..r| 
00000090  0d 38 4a 49 21 9f 03 74  0d 38 80 49 c1 9f 03 6f  |.8JI!..t.8.I...o| 
000000a0  0d 38 12 49 81 9e 03 78  0d 38 f3 49 11 a1 03 90  |.8.I...x.8.I....| 
000000b0  0d 38 22 4c 71 a7 7c 07  00 4a d6 4b 91 a6 03 82  |.8"Lq.|..J.K....| 
000000c0  0d 38 ea 4a e1 a3 03 88  0d 38 72 4b 71 a5 03 a7  |.8.J.....8rKq...| 
000000d0  0d 38 53 4e e1 ad 03 a5  0d 38 23 4e 51 ad 03 ab  |.8SN.....8#NQ...| 
000000e0  0d 38 bb 4e 11 af 03 b2  0d 38 56 4f e1 b0 03 bb  |.8.N.....8VO....| 
000000f0  0d 38 3e 50 81 b3 03 be  0d 38 86 50 51 b4 03 b9  |.8>P.....8.PQ...| 
00000100  0d 38 0d 50 f1 b2 03 bc  0d 38 60 50 e1 b3 03 bd  |.8.P.....8`P....| 
00000110  0d 38 75 50 21 b4 7f 04  48 50 a1 9c 01 0e 71 50  |.8uP!...HP....qP| 
00000120  11 b4 03 c0 0d 38 bd 50  01 b5 03 b8 0d 38 0c 7c  |.....8.P.....8.|| 
00000130  05 04 bb 0d 38 4c 50 b1  b3 7c 07 00 42 21 50 31  |....8LP..|..B!P1| 
00000140  b3 03 b4 0d 38 af 4f e1  b1 03 ac 0d 38 f4 4e c1  |....8.O.....8.N.| 
00000150  af 03 a6 0d 38 6d 4e 31  ae 03 a9 0d 38 b9 4e 11  |....8mN1....8.N.| 
00000160  af 03 9b 0d 38 5d 4d 11  ab 03 84 0d 38 57 4b 21  |....8]M.....8WK!| 
00000170  a5 03 87 0d 38 98 4b e1  a5 03 99 0d 38 31 4d 91  |....8.K.....81M.| 
00000180  aa 03 98 0d 38 1c 4d 61  aa 03 92 0d 38 9e 4c e1  |....8.Ma....8.L.| 
00000190  a8 7c 1f 09 d8 49 c1 a0  03 75 0d 38 f7 49 21 a1  |.|...I...u.8.I!.| 
000001a0  7c 05 09 9c 4b f1 a5 03  7a 0d 38 6a 4a 71 a2 7c  ||...K...z.8jJq.|| 
000001b0  00 00 0a 63 4a 61 a2 03  7b 0d 38 87 4a c1 00 56  |...cJa..{.8.J..V| 
000001c0  ca ff 07 56 ca ff 02 00  00 00 8a f6 55 10 00 56  |...V........U..V| 
000001d0  ca ff 05 56 ca ff 72 7e  4f 12 48 d9 b3 1b 00 00  |...V..r~O.H.....| 
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................| 
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.| 
00000200

```

---

### Post by wilee-nilee on 2010-12-14
cool.;)

---

### Post by wilee-nilee on 2010-12-14
I have been informed in the past that grldr in the windows boot may indicate a non legal windows set up is this the case, just asking.

sda1: _________________________________________________________________________ 
 
    File system:       ntfs 
    Boot sector type:  Windows Vista/7 
    Boot sector info:  No errors found in the Boot Parameter Block. 
    Operating System:  Windows 7 
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /**grldr**

---

### Post by Toktikweb on 2010-12-14
Sorry? Why?

**Edit**: I just read about this. ok.

---

### Post by wilee-nilee on 2010-12-14
> **Toktikweb said:**
> Sorry? Why?

A succinct answer is needed.

---

### Post by Mark Phelps on 2010-12-15
Unless I missed it, OP didn't really clarify what "dead" means regarding Win7.

That grldr directory is created as a byproduct of installing via Wubi because it needs a place in the Windows OS directory to save GRUB4DOS and its files.

There have been LOTS of reports that having some remnant of GRUB in the Win7 (or Vista) boot partition will prevent Windows from booting -- so that may be the case here.

However, if the OP gets a boot menu that includes Win7, and all that is happening is that selecting the WIn7 entry sends them back to the boot menu, removing the grldr directory from /sda1 should clear that up.

---

### Post by Toktikweb on 2010-12-15
This was fixed by running bootrec.exe /fixboot from Windows 7 Recovery Disc.

---

### Post by wilee-nilee on 2010-12-15
> **Mark Phelps said:**
> Unless I missed it, OP didn't really clarify what "dead" means regarding Win7.

That grldr directory is created as a byproduct of installing via Wubi because it needs a place in the Windows OS directory to save GRUB4DOS and its files.

There have been LOTS of reports that having some remnant of GRUB in the Win7 (or Vista) boot partition will prevent Windows from booting -- so that may be the case here.

However, if the OP gets a boot menu that includes Win7, and all that is happening is that selecting the WIn7 entry sends them back to the boot menu, removing the grldr directory from /sda1 should clear that up.

I captain but a answer which indicates a pirate version I had not reported this thread so far.

---

