---
title: "Grub error 15 help"
date: 2010-11-27
forum: General Help
---

### Post by jbruneske on 2010-11-27
Hi all, I'm (somewhat) new to linux and after using a couple distro's i've decided to give Ubuntu a try. Here's my problem- 
I decided to install Ubuntu on my desktop after the setup went well on my laptop and I liked the OS. I already had Windows 7 and Backtrack 9 installed on my HDD, so when I was in setup I took the 200gb partition for BT9 and formatted SDA5 to ext3 with "/" as the root. Then checked "format" and selected SDA5 from dropdown list and continued to install. 
Everything went smooth in the installation and I was prompted to reboot which I did assuming I would soon see a GRUB screen. Instead I got an error saying 
"Grub loading stage1.5.
Grub loading, please wait...
error 15" 
and then the computer just freezes. I've tried to boot from CD but I just get "CD-ROM Boot Priority ...Boot Ready" and then after about 30 seconds it tries to boot from the HDD and I get the same error. 
I've read that I need to configure GRUB somehow but I have no idea how to do that and I can't boot anything from a CD because it just waits and then jumps to the HDD. I guess what i'm asking is if there is a way to configure GRUB from the BIOS menu or make it possible to be able to boot from a CD. Any info would be helpful, I have about $2,000 worth of information on this hard drive and would hate to have to format everything and start over.
Thanks.

---

### Post by Hippytaff on 2010-11-27
Hi and welcome to the forums

if you can post the results.txt of this script [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
then the geniouses here can help you out :-D

---

### Post by jbruneske on 2010-11-27
Sorry about the late reply, I had work till 10:30. Ok so I hooked up my laptop's harddrive to my desktop and booted up from there; so i think i ran a scan on my main 1TB HDD. If I didn't well just let me know what I did wrong.

---

### Post by jbruneske on 2010-11-27
SDA5 Is the sector I installed Ubuntu on, and I noticed it said "Grub 2 is installed in the boot sector of sda5 and looks at sector 1851179474 of the same hard drive for core.img, but core.img can not be found at this location." 
for boot sector info, so i'm guessing I need to put core.img at that location? I have no idea how to do that.. Haha.

---

### Post by jbruneske on 2010-11-28
bump

---

### Post by wilee-nilee on 2010-11-28
> **jbruneske said:**
> bump


First you have several problems probably fixable but the script needs to be put in code tags to be easier read. Could you take a look in my signature and do this.

---

### Post by jbruneske on 2010-11-28
> **wilee-nilee said:**
> First you have several problems probably fixable but the script needs to be put in code tags to be easier read. Could you take a look in my signature and do this.

Like so??

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

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
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 1851179474 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    16,912,383    16,830,464   7 HPFS/NTFS
/dev/sda3          16,912,384 1,533,022,836 1,516,110,453   7 HPFS/NTFS
/dev/sda4       1,533,034,816 1,953,520,064   420,485,249   5 Extended
/dev/sda5       1,533,034,818 1,936,394,774   403,359,957  83 Linux
/dev/sda6       1,936,394,838 1,953,520,064    17,125,227  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders, total 153356490 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   147,017,727   147,015,680  83 Linux
/dev/sdb2         147,019,774   153,356,287     6,336,514   5 Extended
/dev/sdb5         147,019,776   153,356,287     6,336,512  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        F616559516555827                       ntfs       RECOVERY                      
/dev/sda3        186657CC6657A8F0                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        8d8affb0-3f83-4831-a7f5-437965455aee   ext3                                     
/dev/sda6        36465fe5-8370-4d10-a0aa-d93429b5aabd   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7336191c-fd4d-429c-949d-54d7a637b4e9   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        3be74561-c8b1-4f4b-af7e-31decf3ee737   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sr0         /media/Ubuntu 10.10 i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda5        /media/8d8affb0-3f83-4831-a7f5-437965455aee ext3       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set 8d8affb0-3f83-4831-a7f5-437965455aee
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 8d8affb0-3f83-4831-a7f5-437965455aee
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8d8affb0-3f83-4831-a7f5-437965455aee
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=8d8affb0-3f83-4831-a7f5-437965455aee ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8d8affb0-3f83-4831-a7f5-437965455aee
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=8d8affb0-3f83-4831-a7f5-437965455aee ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8d8affb0-3f83-4831-a7f5-437965455aee
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8d8affb0-3f83-4831-a7f5-437965455aee
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set f616559516555827
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
UUID=8d8affb0-3f83-4831-a7f5-437965455aee /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=36465fe5-8370-4d10-a0aa-d93429b5aabd none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 947.8GB: boot/grub/core.img
 947.7GB: boot/grub/grub.cfg
 947.8GB: boot/initrd.img-2.6.35-23-generic-pae
 947.8GB: boot/vmlinuz-2.6.35-23-generic-pae
 947.8GB: initrd.img
 947.8GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7336191c-fd4d-429c-949d-54d7a637b4e9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7336191c-fd4d-429c-949d-54d7a637b4e9
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7336191c-fd4d-429c-949d-54d7a637b4e9
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=7336191c-fd4d-429c-949d-54d7a637b4e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7336191c-fd4d-429c-949d-54d7a637b4e9
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=7336191c-fd4d-429c-949d-54d7a637b4e9 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7336191c-fd4d-429c-949d-54d7a637b4e9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7336191c-fd4d-429c-949d-54d7a637b4e9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3be74561-c8b1-4f4b-af7e-31decf3ee737 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  30.2GB: boot/grub/core.img
  47.4GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-23-generic-pae
  30.2GB: boot/vmlinuz-2.6.35-23-generic-pae
   1.0GB: initrd.img
  30.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  5a 50 48 b7 6a 50 48 b7  7a 50 48 b7 8a 50 48 b7  |ZPH.jPH.zPH..PH.|
00000010  9a 50 48 b7 aa 50 48 b7  80 ce e9 b7 ca 50 48 b7  |.PH..PH......PH.|
00000020  da 50 48 b7 ea 50 48 b7  fa 50 48 b7 0a 51 48 b7  |.PH..PH..PH..QH.|
00000030  1a 51 48 b7 2a 51 48 b7  3a 51 48 b7 70 df 4e b7  |.QH.*QH.:QH.p.N.|
00000040  5a 51 48 b7 6a 51 48 b7  7a 51 48 b7 8a 51 48 b7  |ZQH.jQH.zQH..QH.|
00000050  9a 51 48 b7 b0 f0 48 b7  70 fd d2 b7 ca 51 48 b7  |.QH...H.p....QH.|
00000060  da 51 48 b7 ea 51 48 b7  fa 51 48 b7 0a 52 48 b7  |.QH..QH..QH..RH.|
00000070  1a 52 48 b7 2a 52 48 b7  3a 52 48 b7 4a 52 48 b7  |.RH.*RH.:RH.JRH.|
00000080  5a 52 48 b7 6a 52 48 b7  7a 52 48 b7 8a 52 48 b7  |ZRH.jRH.zRH..RH.|
00000090  9a 52 48 b7 90 f7 48 b7  ba 52 48 b7 ca 52 48 b7  |.RH...H..RH..RH.|
000000a0  50 5c da b7 ea 52 48 b7  fa 52 48 b7 0a 53 48 b7  |P\...RH..RH..SH.|
000000b0  1a 53 48 b7 2a 53 48 b7  3a 53 48 b7 4a 53 48 b7  |.SH.*SH.:SH.JSH.|
000000c0  5a 53 48 b7 6a 53 48 b7  7a 53 48 b7 8a 53 48 b7  |ZSH.jSH.zSH..SH.|
000000d0  9a 53 48 b7 aa 53 48 b7  ba 53 48 b7 ca 53 48 b7  |.SH..SH..SH..SH.|
000000e0  da 53 48 b7 ea 53 48 b7  fa 53 48 b7 0a 54 48 b7  |.SH..SH..SH..TH.|
000000f0  30 d6 4e b7 2a 54 48 b7  3a 54 48 b7 4a 54 48 b7  |0.N.*TH.:TH.JTH.|
00000100  5a 54 48 b7 6a 54 48 b7  7a 54 48 b7 8a 54 48 b7  |ZTH.jTH.zTH..TH.|
00000110  9a 54 48 b7 aa 54 48 b7  ba 54 48 b7 ca 54 48 b7  |.TH..TH..TH..TH.|
00000120  da 54 48 b7 ea 54 48 b7  fa 54 48 b7 0a 55 48 b7  |.TH..TH..TH..UH.|
00000130  1a 55 48 b7 2a 55 48 b7  3a 55 48 b7 10 0b 49 b7  |.UH.*UH.:UH...I.|
00000140  5a 55 48 b7 6a 55 48 b7  7a 55 48 b7 8a 55 48 b7  |ZUH.jUH.zUH..UH.|
00000150  9a 55 48 b7 aa 55 48 b7  10 cf d9 b7 e0 a9 de b7  |.UH..UH.........|
00000160  da 55 48 b7 ea 55 48 b7  fa 55 48 b7 0a 56 48 b7  |.UH..UH..UH..VH.|
00000170  1a 56 48 b7 2a 56 48 b7  3a 56 48 b7 4a 56 48 b7  |.VH.*VH.:VH.JVH.|
00000180  5a 56 48 b7 6a 56 48 b7  7a 56 48 b7 8a 56 48 b7  |ZVH.jVH.zVH..VH.|
00000190  9a 56 48 b7 aa 56 48 b7  ba 56 48 b7 ca 56 48 b7  |.VH..VH..VH..VH.|
000001a0  da 56 48 b7 ea 56 48 b7  fa 56 48 b7 0a 57 48 b7  |.VH..VH..VH..WH.|
000001b0  1a 57 48 b7 2a 57 48 b7  3a 57 48 b7 4a 57 00 fe  |.WH.*WH.:WH.JW..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 b0 60 00 00 00  |............`...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```(yay it worked!)

---

### Post by wilee-nilee on 2010-11-28
Thanks that just makes things easier.;)

So I see the remnants of a wubi install in sda3 this your not using correct?

I ask this first as you have a bit of a convoluted set up and you have grub-legacy and grub2 both installed, with grub-legacy now as the bootloader in the sda drive.

Also how backed up are you?

---

### Post by jbruneske on 2010-11-28
No problem. 
Yes the wubi installer i'm not using and i'm not really sure how I got on there. (Perhaps when I used the boot helper option on the ISO i burned).
TBH I'm not really sure why I have 2 GRUB's on my HDD.. I bought the computer prebuilt with windows 7 already installed.
Afterwards I partitioned 200GB on my harddrive to use with Backtrack 4, so mabe that's what installed GRUB Legacy.
Actually my Ext HDD died on me about 2 months ago so i'm screwed as far as being backed up.. I only have a 60gb HDD that I could back files up to.

---

### Post by wilee-nilee on 2010-11-28
Just another question, I see grub-legacy in the sda boot=.97 but not really otherwise in the script, did you try and reload grub from a Live cd? 

It may be that we just have to load grub2 to the mbr and your set, but there is also a purge all grub option, and then reinstall grub2 I'm just trying to error on the side of caution here.

So sda5 was your last install?

---

### Post by jbruneske on 2010-11-28
> **wilee-nilee said:**
> Just another question, I see grub-legacy in the sda boot=.97 but not really otherwise in the script, did you try and reload grub from a Live cd? 

It may be that we just have to load grub2 to the mbr and your set, but there is also a purge all grub option, and then reinstall grub2 I'm just trying to error on the side of caution here.

So sda5 was your last install?

Nope, never tried to reload grub (at least knowingly).
I also was thinking I could just 'reinstall' grub2, but just a word of caution the only way I can get past the bios menu on my desktop is to plug in my laptop's HDD and boot off of it. Idk how I could per-say select which drive I want to install it on. 
And yes SDA5 was my last install, Ubuntu.

p.s. I'm an ex-Windows Baby still Googling half the things we're talking about so if something i'm saying just makes you scratch your head, feel free to correct me.

---

### Post by wilee-nilee on 2010-11-28
Lets just try to reload grub2 to the sda mbr using a live Ubuntu CD maverick would be best here.

Boot the live cd and in the terminal run these two commands.

```
sudo mount /dev/sda5 /mnt
```

then in the same terminal

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot to the sda drive choose the sda5 install and if you get in run this command
```
sudo update-grub
```

---

### Post by jbruneske on 2010-11-28
Ok, um the disk I used to install Ubuntu won't boot now for some reason. Most bootable disks are hit-or-miss when it comes to using them. At the moment all I get when I try to boot is:
"CD-ROM Boot Priority 35_" 
and then
"CD-ROM Boot Priority ...Boot Ready"
then it just sits there before moving on to my HDD.
I'm using Dynex DVD+R 16x 4.7GB  burned at 8x using PowerISO.
Idk if any of that info helps.

---

### Post by wilee-nilee on 2010-11-28
> **jbruneske said:**
> Ok, um the disk I used to install Ubuntu won't boot now for some reason. Most bootable disks are hit-or-miss when it comes to using them. At the moment all I get when I try to boot is:
"CD-ROM Boot Priority 35_" 
and then
"CD-ROM Boot Priority ...Boot Ready"
then it just sits there before moving on to my HDD.
I'm using Dynex DVD+R 16x 4.7GB  burned at 8x using PowerISO.
Idk if any of that info helps.


Try the f12 key prompt on powering up there is a post bios boot from menu that can be helpful. Might be another key but for a Ubuntu disc that is the usual.

We have to be using a disc with Grub2 so it may be that backtrack is grub-legacy so don't use their disc but a Maverick one. I suggest Maverick even though Lucid and Karmic have grub2, but I ran into problems with using a earlier disc myself.

---

### Post by jbruneske on 2010-11-28
Ok i'll give it a shot.. Post back in a few with the results.

---

### Post by jbruneske on 2010-11-28
No luck, still get the same ordeal. Is there a way I can use my laptop's HDD to my advantage? Say do sudo grub-install and then specify my other drive's name and proceed from there? Idk my computer's been giving me dead-end after dead-end. Always another error message somewhere. >.>

---

### Post by wilee-nilee on 2010-11-28
> **jbruneske said:**
> No luck, still get the same ordeal. Is there a way I can use my laptop's HDD to my advantage? Say do sudo grub-install and then specify my other drive's name and proceed from there? Idk my computer's been giving me dead-end after dead-end. Always another error message somewhere. >.>

If you could get into sda5 say with a super grub disc you probably could. Problem I see here is that sda5 grub is at about 750Gigs pretty deep onto the HD, it may just be your bios is to old to reach that far. I would run another script and post it to see what if any changes were made.

---

### Post by jbruneske on 2010-11-28
ok I shall do that. brb

---

### Post by jbruneske on 2010-11-28
Here you go:

```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

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
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 1851179474 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    16,912,383    16,830,464   7 HPFS/NTFS
/dev/sda3          16,912,384 1,533,022,836 1,516,110,453   7 HPFS/NTFS
/dev/sda4       1,533,034,816 1,953,520,064   420,485,249   5 Extended
/dev/sda5       1,533,034,818 1,936,394,774   403,359,957  83 Linux
/dev/sda6       1,936,394,838 1,953,520,064    17,125,227  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders, total 153356490 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   147,017,727   147,015,680  83 Linux
/dev/sdb2         147,019,774   153,356,287     6,336,514   5 Extended
/dev/sdb5         147,019,776   153,356,287     6,336,512  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        F616559516555827                       ntfs       RECOVERY                      
/dev/sda3        186657CC6657A8F0                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        8d8affb0-3f83-4831-a7f5-437965455aee   ext3                                     
/dev/sda6        36465fe5-8370-4d10-a0aa-d93429b5aabd   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7336191c-fd4d-429c-949d-54d7a637b4e9   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        3be74561-c8b1-4f4b-af7e-31decf3ee737   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro,commit=0)


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
search --no-floppy --fs-uuid --set 8d8affb0-3f83-4831-a7f5-437965455aee
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 8d8affb0-3f83-4831-a7f5-437965455aee
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8d8affb0-3f83-4831-a7f5-437965455aee
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=8d8affb0-3f83-4831-a7f5-437965455aee ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8d8affb0-3f83-4831-a7f5-437965455aee
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=8d8affb0-3f83-4831-a7f5-437965455aee ro single 
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
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8d8affb0-3f83-4831-a7f5-437965455aee
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8d8affb0-3f83-4831-a7f5-437965455aee
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set f616559516555827
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
UUID=8d8affb0-3f83-4831-a7f5-437965455aee /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=36465fe5-8370-4d10-a0aa-d93429b5aabd none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 947.8GB: boot/grub/core.img
 947.7GB: boot/grub/grub.cfg
 947.8GB: boot/initrd.img-2.6.35-23-generic-pae
 947.8GB: boot/vmlinuz-2.6.35-23-generic-pae
 947.8GB: initrd.img
 947.8GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7336191c-fd4d-429c-949d-54d7a637b4e9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 7336191c-fd4d-429c-949d-54d7a637b4e9
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7336191c-fd4d-429c-949d-54d7a637b4e9
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=7336191c-fd4d-429c-949d-54d7a637b4e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7336191c-fd4d-429c-949d-54d7a637b4e9
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=7336191c-fd4d-429c-949d-54d7a637b4e9 ro single 
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
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7336191c-fd4d-429c-949d-54d7a637b4e9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 7336191c-fd4d-429c-949d-54d7a637b4e9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3be74561-c8b1-4f4b-af7e-31decf3ee737 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  30.2GB: boot/grub/core.img
  47.4GB: boot/grub/grub.cfg
   1.0GB: boot/initrd.img-2.6.35-23-generic-pae
  30.2GB: boot/vmlinuz-2.6.35-23-generic-pae
   1.0GB: initrd.img
  30.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  5a 50 48 b7 6a 50 48 b7  7a 50 48 b7 8a 50 48 b7  |ZPH.jPH.zPH..PH.|
00000010  9a 50 48 b7 aa 50 48 b7  80 ce e9 b7 ca 50 48 b7  |.PH..PH......PH.|
00000020  da 50 48 b7 ea 50 48 b7  fa 50 48 b7 0a 51 48 b7  |.PH..PH..PH..QH.|
00000030  1a 51 48 b7 2a 51 48 b7  3a 51 48 b7 70 df 4e b7  |.QH.*QH.:QH.p.N.|
00000040  5a 51 48 b7 6a 51 48 b7  7a 51 48 b7 8a 51 48 b7  |ZQH.jQH.zQH..QH.|
00000050  9a 51 48 b7 b0 f0 48 b7  70 fd d2 b7 ca 51 48 b7  |.QH...H.p....QH.|
00000060  da 51 48 b7 ea 51 48 b7  fa 51 48 b7 0a 52 48 b7  |.QH..QH..QH..RH.|
00000070  1a 52 48 b7 2a 52 48 b7  3a 52 48 b7 4a 52 48 b7  |.RH.*RH.:RH.JRH.|
00000080  5a 52 48 b7 6a 52 48 b7  7a 52 48 b7 8a 52 48 b7  |ZRH.jRH.zRH..RH.|
00000090  9a 52 48 b7 90 f7 48 b7  ba 52 48 b7 ca 52 48 b7  |.RH...H..RH..RH.|
000000a0  50 5c da b7 ea 52 48 b7  fa 52 48 b7 0a 53 48 b7  |P\...RH..RH..SH.|
000000b0  1a 53 48 b7 2a 53 48 b7  3a 53 48 b7 4a 53 48 b7  |.SH.*SH.:SH.JSH.|
000000c0  5a 53 48 b7 6a 53 48 b7  7a 53 48 b7 8a 53 48 b7  |ZSH.jSH.zSH..SH.|
000000d0  9a 53 48 b7 aa 53 48 b7  ba 53 48 b7 ca 53 48 b7  |.SH..SH..SH..SH.|
000000e0  da 53 48 b7 ea 53 48 b7  fa 53 48 b7 0a 54 48 b7  |.SH..SH..SH..TH.|
000000f0  30 d6 4e b7 2a 54 48 b7  3a 54 48 b7 4a 54 48 b7  |0.N.*TH.:TH.JTH.|
00000100  5a 54 48 b7 6a 54 48 b7  7a 54 48 b7 8a 54 48 b7  |ZTH.jTH.zTH..TH.|
00000110  9a 54 48 b7 aa 54 48 b7  ba 54 48 b7 ca 54 48 b7  |.TH..TH..TH..TH.|
00000120  da 54 48 b7 ea 54 48 b7  fa 54 48 b7 0a 55 48 b7  |.TH..TH..TH..UH.|
00000130  1a 55 48 b7 2a 55 48 b7  3a 55 48 b7 10 0b 49 b7  |.UH.*UH.:UH...I.|
00000140  5a 55 48 b7 6a 55 48 b7  7a 55 48 b7 8a 55 48 b7  |ZUH.jUH.zUH..UH.|
00000150  9a 55 48 b7 aa 55 48 b7  10 cf d9 b7 e0 a9 de b7  |.UH..UH.........|
00000160  da 55 48 b7 ea 55 48 b7  fa 55 48 b7 0a 56 48 b7  |.UH..UH..UH..VH.|
00000170  1a 56 48 b7 2a 56 48 b7  3a 56 48 b7 4a 56 48 b7  |.VH.*VH.:VH.JVH.|
00000180  5a 56 48 b7 6a 56 48 b7  7a 56 48 b7 8a 56 48 b7  |ZVH.jVH.zVH..VH.|
00000190  9a 56 48 b7 aa 56 48 b7  ba 56 48 b7 ca 56 48 b7  |.VH..VH..VH..VH.|
000001a0  da 56 48 b7 ea 56 48 b7  fa 56 48 b7 0a 57 48 b7  |.VH..VH..VH..WH.|
000001b0  1a 57 48 b7 2a 57 48 b7  3a 57 48 b7 4a 57 00 fe  |.WH.*WH.:WH.JW..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 b0 60 00 00 00  |............`...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2010-11-28
Lets go to the purge all grub and reinstall.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

the sda drive is still showing grub-legacy=.97 generally the commands should have put grub2 there. Try the chroot method in the link.

Make sure you are using a maverick cd

---

### Post by jbruneske on 2010-11-28
Ok i'll try and follow the instructions..
quick question, what's a 'maverick cd'?

---

### Post by wilee-nilee on 2010-11-28
> **jbruneske said:**
> Ok i'll try and follow the instructions..
quick question, what's a 'maverick cd'?

[http://www.ubuntu.com/](http://www.ubuntu.com/)
The Live cd for the latest release of Ubuntu, if you weren't using this before what ever DVD you were using has grub-legacy probably.

I think backtrack uses grub legacy the two don't mix to say the least. That is grub-legacy=.97 grub2=1.98 or so, both are grub bootloaders but mixed up are a mess.

I would download that Maverick cd burn it to  cd or load a thumb and boot it and just try my original 2 commands with the reboot to sda5 and the sudo-update-grub.

I think you may not understand that these are 2 different bootloaders in the sda master boot record=first 512Mib of sda you have grub-legacy, but the script shows grub2 installed everywhere else does this make sense sort of.

---

### Post by jbruneske on 2010-11-28
You sir, are a lifesaver! I managed to follow (most) of what that post said. I purged all grub from my HDD, and now i'm posting to you from my cleanly partitioned and running desktop!
Got some 
error: no such device
grub rescue> 
message on my laptop but no worries, i'll just install a fresh copy of Ubuntu tomorrow. Thank you so much! I'm very relived about not losing all my work! Definitely a great community you guys have created here.

---

### Post by wilee-nilee on 2010-11-28
> **jbruneske said:**
> You sir, are a lifesaver! I managed to follow (most) of what that post said. I purged all grub from my HDD, and now i'm posting to you from my cleanly partitioned and running desktop!
Got some 
error: no such device
grub rescue> 
message on my laptop but no worries, i'll just install a fresh copy of Ubuntu tomorrow. Thank you so much! I'm very relived about not losing all my work! Definitely a great community you guys have created here.

I saw your setup earlier today and just kind said to my self I hope somebody can figure that out. I think we were lucky here with the tutorials it saves all out booties.

For some reason I came across it again and just looked closer and suggested, thank goodness for everybody involved especially drs305 they are the hero here.;)

Hippytaff as well for getting the script online.

---

### Post by jbruneske on 2010-11-28
> **wilee-nilee said:**
> I saw your setup earlier today and just kind said to my self I hope somebody can figure that out. I think we were lucky here with the tutorials it saves all out booties.

For some reason I came across it again and just looked closer and suggested, thank goodness for everybody involved especially drs305 they are the hero here.;)

Hippytaff as well for getting the script online.

:D Yes, thanks to everyone! I've learned alot today, and am definitely excited about discovering linux and the open-source community it has. Hope to be helping other people with their problems soon. Well, its almost 3am so i'm off to bed.
Cheers!

---

