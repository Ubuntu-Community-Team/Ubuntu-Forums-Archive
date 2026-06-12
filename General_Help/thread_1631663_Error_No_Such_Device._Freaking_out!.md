---
title: "Error: No Such Device. Freaking out!"
date: 2010-11-26
forum: General Help
---

### Post by breeze_posey on 2010-11-26
I did some updates and restarted my computer. When it restarted a message came up saying:  
 
error: no such device: fb67efb0-7380-43cb-b187-d89b42719710.
grub rescue>
 
What do I do? My friend partitioned my HD for me with Vista and Ubuntu. So, I'm really new to Ubuntu and have no clue whats going on! HELP!!

---

### Post by Rubi1200 on 2010-11-27
Hi and welcome to the forums :)

Firstly, and most important, remain calm.

Second, please use a LiveCD to boot the computer and choose to try Ubuntu not install.

Then, click on the link at the bottom of my post and run the boot info script (instructions included).

Post the results back here and we will try and help you resolve this.

Thanks.

---

### Post by breeze_posey on 2010-12-07
Sorry it took so long to reply. Here were my results:

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    36,869,174    36,869,112  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     36,869,175   211,656,537   174,787,363   7 HPFS/NTFS
/dev/sda3         349,445,941   625,141,759   275,695,819   5 Extended
/dev/sda5         349,445,943   506,450,694   157,004,752   7 HPFS/NTFS
/dev/sda6         506,451,968   620,204,031   113,752,064  83 Linux
/dev/sda7         620,206,080   625,141,759     4,935,680  82 Linux swap / Solaris
/dev/sda4         211,672,440   349,445,879   137,773,440   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       fb67efb0-7380-43cb-b187-d89b42719710   ext4                                     
/dev/sda1        D476-EF15                              vfat       RECOVERY                      
/dev/sda2        788AC4988AC453F2                       ntfs       Vista64                       
/dev/sda3: PTTYPE="dos" 
/dev/sda4        59C01AB83C641511                       ntfs       storage                       
/dev/sda5        44B8C6CDB8C6BCA4                       ntfs       DATA                          
/dev/sda6        0353C6CF0D149FDD                       ntfs       storage                       
/dev/sda7        0b552b81-169e-4c00-8591-0245698529ff   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda5/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d476-ef15
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 788ac4988ac453f2
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda5/Wubi/etc/fstab: =============================

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

================= sda5/Wubi: Location of files loaded by Grub: =================


  11.0GB: boot/grub/core.img
   9.1GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.32-24-generic
   2.9GB: boot/initrd.img-2.6.32-25-generic
   3.5GB: boot/initrd.img-2.6.32-26-generic
  11.4GB: boot/vmlinuz-2.6.32-24-generic
   1.8GB: boot/vmlinuz-2.6.32-25-generic
  11.9GB: boot/vmlinuz-2.6.32-26-generic
   3.5GB: initrd.img
   2.9GB: initrd.img.old
  11.9GB: vmlinuz
   1.8GB: vmlinuz.old

Inline Attachment Follows: RESULTS.txt
&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Boot Info Script 0.55&nbsp; &nbsp; dated February 15th, 2010&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <BR><BR>============================= Boot Info Summary: ==============================<BR><BR> =&gt; Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in <BR>&nbsp; &nbsp; partition #256 for /boot/grub.<BR><BR>sda1: _________________________________________________________________________<BR><BR>&nbsp; &nbsp; File system:&nbsp; &nbsp; &nbsp; vfat<BR>&nbsp; &nbsp; Boot sector type:&nbsp; Vista: Fat 32<BR>&nbsp; &nbsp; Boot sector info:&nbsp; No errors found in the Boot Parameter Block.<BR>&nbsp; &nbsp; Operating System:&nbsp; <BR>&nbsp; &nbsp; Boot files/dirs:&nbsp; /bootmgr /boot/bcd<BR><BR>sda2: _________________________________________________________________________<BR><BR>&nbsp; &nbsp; File system:&nbsp; &nbsp; &nbsp; ntfs<BR>&nbsp; &nbsp; Boot sector type:&nbsp; Windows Vista/7<BR>&nbsp; &nbsp; Boot sector info:&nbsp; No errors found in the Boot Parameter Block.<BR>&nbsp; &nbsp; Operating System:&nbsp; Windows Vista<BR>&nbsp; &nbsp; Boot files/dirs:&nbsp; /bootmgr /Boot/BCD /Windows/System32/winload.exe <BR>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /wubildr.mbr /wubildr<BR><BR>sda3: _________________________________________________________________________<BR><BR>&nbsp; &nbsp; File system:&nbsp; &nbsp; &nbsp; Extended Partition<BR>&nbsp; &nbsp; Boot sector type:&nbsp; -<BR>&nbsp; &nbsp; Boot sector info:&nbsp; <BR><BR>sda5: _________________________________________________________________________<BR><BR>&nbsp; &nbsp; File system:&nbsp; &nbsp; &nbsp; ntfs<BR>&nbsp; &nbsp; Boot sector type:&nbsp; Windows Vista/7<BR>&nbsp; &nbsp; Boot sector info:&nbsp; According to the info in the boot sector, sda5 starts <BR>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; at sector 63.<BR>&nbsp; &nbsp; Operating System:&nbsp; <BR>&nbsp; &nbsp; Boot files/dirs:&nbsp; /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr <BR>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /ubuntu/disks/root.disk /ubuntu/disks/swap.disk<BR><BR>sda5/Wubi: _________________________________________________________________________<BR><BR>&nbsp; &nbsp; File system:&nbsp; &nbsp; &nbsp; ext4<BR>&nbsp; &nbsp; Boot sector type:&nbsp; -<BR>&nbsp; &nbsp; Boot sector info:&nbsp; <BR>&nbsp; &nbsp; Operating System:&nbsp; Ubuntu 10.04.1 LTS<BR>&nbsp; &nbsp; Boot files/dirs:&nbsp; /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img<BR><BR>sda6: _________________________________________________________________________<BR><BR>&nbsp; &nbsp; File system:&nbsp; &nbsp; &nbsp; ntfs<BR>&nbsp; &nbsp; Boot sector type:&nbsp; Windows Vista/7<BR>&nbsp; &nbsp; Boot sector info:&nbsp; No errors found in the Boot Parameter Block.<BR>&nbsp; &nbsp; Operating System:&nbsp; <BR>&nbsp; &nbsp; Boot files/dirs:&nbsp; <BR><BR>sda7: _________________________________________________________________________<BR><BR>&nbsp; &nbsp; File system:&nbsp; &nbsp; &nbsp; swap<BR>&nbsp; &nbsp; Boot sector type:&nbsp; -<BR>&nbsp; &nbsp; Boot sector info:&nbsp; <BR><BR>sda4: _________________________________________________________________________<BR><BR>&nbsp; &nbsp; File system:&nbsp; &nbsp; &nbsp; ntfs<BR>&nbsp; &nbsp; Boot sector type:&nbsp; Windows Vista/7<BR>&nbsp; &nbsp; Boot sector info:&nbsp; No errors found in the Boot Parameter Block.<BR>&nbsp; &nbsp; Operating System:&nbsp; <BR>&nbsp; &nbsp; Boot files/dirs:&nbsp; <BR><BR>=========================== Drive/Partition Info: =============================<BR><BR>Drive: sda ___________________ _____________________________________________________<BR><BR>Disk /dev/sda: 320.1 GB, 320072933376 bytes<BR>255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors<BR>Units = sectors of 1 * 512 = 512 bytes<BR>Sector size (logical/physical): 512 bytes / 512 bytes<BR><BR>Partition&nbsp; Boot&nbsp; &nbsp; &nbsp; &nbsp; Start&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; End&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Size&nbsp; Id System<BR><BR>/dev/sda1&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; 63&nbsp; &nbsp; 36,869,174&nbsp; &nbsp; 36,869,112&nbsp; 1c Hidden W95 FAT32 (LBA)<BR>/dev/sda2&nbsp; &nbsp; *&nbsp; &nbsp; 36,869,175&nbsp; 211,656,537&nbsp; 174,787,363&nbsp; 7 HPFS/NTFS<BR>/dev/sda3&nbsp; &nbsp; &nbsp; &nbsp; 349,445,941&nbsp; 625,141,759&nbsp; 275,695,819&nbsp; 5 Extended<BR>/dev/sda5&nbsp; &nbsp; &nbsp; &nbsp; 349,445,943&nbsp; 506,450,694&nbsp; 157,004,752&nbsp; 7 HPFS/NTFS<BR>/dev/sda6&nbsp; &nbsp; &nbsp; &nbsp; 506,451,968&nbsp; 620,204,031&nbsp; 113,752,064&nbsp; 83 Linux<BR>/dev/sda7&nbsp; &nbsp; &nbsp; &nbsp; 620,206,080&nbsp; 625,141,759&nbsp; &nbsp; 4,935,680&nbsp; 82 Linux swap / Solaris<BR>/dev/sda4&nbsp; &nbsp; &nbsp; &nbsp; 211,672,440&nbsp; 349,445,879&nbsp; 137,773,440&nbsp; 7 HPFS/NTFS<BR><BR><BR>blkid -c /dev/null: ____________________________________________________________<BR><BR>Device&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; UUID&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; TYPE&nbsp; &nbsp; &nbsp; LABEL&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <BR><BR>/dev/loop0&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; squashfs&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <BR>/dev/loop1&nbsp; &nbsp; &nbsp; fb67efb0-7380-43cb-b187-d89b42719710&nbsp; ext4&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <BR>/dev/sda1&nbsp; &nbsp; &nbsp; &nbsp; D476-EF15&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; vfat&nbsp; &nbsp; &nbsp; RECOVERY&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <BR>/dev/sda2&nbsp; &nbsp; &nbsp; &nbsp; 788AC4988AC453F2&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ntfs&nbsp; &nbsp; &nbsp; Vista64&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <BR>/dev/sda3: PTTYPE="dos" <BR>/dev/sda4&nbsp; &nbsp; &nbsp; &nbsp; 59C01AB83C641511&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ntfs&nbsp; &nbsp; &nbsp; storage&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <BR>/dev/sda5&nbsp; &nbsp; &nbsp; &nbsp; 44B8C6CDB8C6BCA4&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ntfs&nbsp; &nbsp; &nbsp; DATA&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <BR>/dev/sda6&nbsp; &nbsp; &nbsp; &nbsp; 0353C6CF0D149FDD&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ntfs&nbsp; &nbsp; &nbsp; storage&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <BR>/dev/sda7&nbsp; &nbsp; &nbsp; &nbsp; 0b552b81-169e-4c00-8591-0245698529ff&nbsp; swap&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; <BR>/dev/sda: PTTYPE="dos" <BR><BR>============================ "mount | grep ^/dev&nbsp; output: ===========================<BR><BR>Device&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Mount_Point&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Type&nbsp; &nbsp; &nbsp; Options<BR><BR>aufs&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; aufs&nbsp; &nbsp; &nbsp; (rw)<BR>/dev/sr0&nbsp; &nbsp; &nbsp; &nbsp; /cdrom&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; iso9660&nbsp; &nbsp; (ro,noatime)<BR>/dev/loop0&nbsp; &nbsp; &nbsp; /rofs&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; squashfs&nbsp; (ro,noatime)<BR><BR><BR>======================== sda5/Wubi/boot/grub/grub.cfg: ========================<BR><BR>#<BR># DO NOT EDIT THIS FILE<BR>#<BR># It is automatically generated by /usr/sbin/grub-mkconfig using templates<BR># from /etc/grub.d and settings from /etc/default/grub<BR>#<BR><BR>### BEGIN /etc/grub.d/00_header ###<BR>if [ -s $prefix/grubenv ]; then<BR>&nbsp; load_env<BR>fi<BR>set default="0"<BR>if [ ${prev_saved_entry} ]; then<BR>&nbsp; set saved_entry=${prev_saved_entry}<BR>&nbsp; save_env saved_entry<BR>&nbsp; set prev_saved_entry=<BR>&nbsp; save_env prev_saved_entry<BR>&nbsp; set boot_once=true<BR>fi<BR><BR>function savedefault {<BR>&nbsp; if [ -z ${boot_once} ]; then<BR>&nbsp; &nbsp; saved_entry=${chosen}<BR>&nbsp; &nbsp; save_env saved_entry<BR>&nbsp; fi<BR>}<BR><BR>function recordfail {<BR>&nbsp; set recordfail=1<BR>&nbsp; if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi<BR>}<BR>insmod ntfs<BR>set root='(hd0,5)'<BR>search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4<BR>loopback loop0 /ubuntu/disks/root.disk<BR>set root=(loop0)<BR>if loadfont /usr/share/grub/unicode.pf2 ; then<BR>&nbsp; set gfxmode=640x480<BR>&nbsp; insmod gfxterm<BR>&nbsp; insmod vbe<BR>&nbsp; if terminal_output gfxterm ; then true ; else<BR>&nbsp; &nbsp; # For backward compatibility with versions of terminal.mod that don't<BR>&nbsp; &nbsp; # understand terminal_output<BR>&nbsp; &nbsp; terminal gfxterm<BR>&nbsp; fi<BR>fi<BR>insmod ntfs<BR>set root='(hd0,5)'<BR>search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4<BR>loopback loop0 /ubuntu/disks/root.disk<BR>set root=(loop0)<BR>set locale_dir=($root)/boot/grub/locale<BR>set lang=en<BR>insmod gettext<BR>if [ ${recordfail} = 1 ]; then<BR>&nbsp; set timeout=-1<BR>else<BR>&nbsp; set timeout=10<BR>fi<BR>### END /etc/grub.d/00_header ###<BR><BR>### BEGIN /etc/grub.d/05_debian_theme ###<BR>set menu_color_normal=white/black<BR>set menu_color_highlight=black/light-gray<BR>### END /etc/grub.d/05_debian_theme ###<BR><BR>### BEGIN /etc/grub.d/10_linux ###<BR>### END /etc/grub.d/10_linux ###<BR><BR>### BEGIN /etc/grub.d/10_lupin ###<BR>menuentry "Ubuntu, Linux 2.6.32-26-generic" {<BR>&nbsp;&nbsp;&nbsp; insmod ntfs<BR>&nbsp;&nbsp;&nbsp; set root='(hd0,5)'<BR>&nbsp;&nbsp;&nbsp; search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4<BR>&nbsp;&nbsp;&nbsp; loopback loop0 /ubuntu/disks/root.disk<BR>&nbsp;&nbsp;&nbsp; set root=(loop0)<BR>&nbsp;&nbsp;&nbsp; linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro&nbsp; quiet splash<BR>&nbsp;&nbsp;&nbsp; initrd /boot/initrd.img-2.6.32-26-generic<BR>}<BR>menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {<BR>&nbsp;&nbsp;&nbsp; insmod ntfs<BR>&nbsp;&nbsp;&nbsp; set root='(hd0,5)'<BR>&nbsp;&nbsp;&nbsp; search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4<BR>&nbsp;&nbsp;&nbsp; loopback loop0 /ubuntu/disks/root.disk<BR>&nbsp;&nbsp;&nbsp; set root=(loop0)<BR>&nbsp;&nbsp;&nbsp; linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single <BR>&nbsp;&nbsp;&nbsp; initrd /boot/initrd.img-2.6.32-26-generic<BR>}<BR>menuentry "Ubuntu, Linux 2.6.32-25-generic" {<BR>&nbsp;&nbsp;&nbsp; insmod ntfs<BR>&nbsp;&nbsp;&nbsp; set root='(hd0,5)'<BR>&nbsp;&nbsp;&nbsp; search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4<BR>&nbsp;&nbsp;&nbsp; loopback loop0 /ubuntu/disks/root.disk<BR>&nbsp;&nbsp;&nbsp; set root=(loop0)<BR>&nbsp;&nbsp;&nbsp; linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro&nbsp; quiet splash<BR>&nbsp;&nbsp;&nbsp; initrd /boot/initrd.img-2.6.32-25-generic<BR>}<BR>menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {<BR>&nbsp;&nbsp;&nbsp; insmod ntfs<BR>&nbsp;&nbsp;&nbsp; set root='(hd0,5)'<BR>&nbsp;&nbsp;&nbsp; search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4<BR>&nbsp;&nbsp;&nbsp; loopback loop0 /ubuntu/disks/root.disk<BR>&nbsp;&nbsp;&nbsp; set root=(loop0)<BR>&nbsp;&nbsp;&nbsp; linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single <BR>&nbsp;&nbsp;&nbsp; initrd /boot/initrd.img-2.6.32-25-generic<BR>}<BR>menuentry "Ubuntu, Linux 2.6.32-24-generic" {<BR>&nbsp;&nbsp;&nbsp; insmod ntfs<BR>&nbsp;&nbsp;&nbsp; set root='(hd0,5)'<BR>&nbsp;&nbsp;&nbsp; search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4<BR>&nbsp;&nbsp;&nbsp; loopback loop0 /ubuntu/disks/root.disk<BR>&nbsp;&nbsp;&nbsp; set root=(loop0)<BR>&nbsp;&nbsp;&nbsp; linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro&nbsp; quiet splash<BR>&nbsp;&nbsp;&nbsp; initrd /boot/initrd.img-2.6.32-24-generic<BR>}<BR>menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {<BR>&nbsp;&nbsp;&nbsp; insmod ntfs<BR>&nbsp;&nbsp;&nbsp; set root='(hd0,5)'<BR>&nbsp;&nbsp;&nbsp; search --no-floppy --fs-uuid --set 44b8c6cdb8c6bca4<BR>&nbsp;&nbsp;&nbsp; loopback loop0 /ubuntu/disks/root.disk<BR>&nbsp;&nbsp;&nbsp; set root=(loop0)<BR>&nbsp;&nbsp;&nbsp; linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single <BR>&nbsp;&nbsp;&nbsp; initrd /boot/initrd.img-2.6.32-24-generic<BR>}<BR>### END /etc/grub.d/10_lupin ###<BR><BR>### BEGIN /etc/grub.d/20_memtest86+ ###<BR>### END /etc/grub.d/20_memtest86+ ###<BR><BR>### BEGIN /etc/grub.d/30_os-prober ###<BR>menuentry "Windows Vista (loader) (on /dev/sda1)" {<BR>&nbsp;&nbsp;&nbsp; insmod fat<BR>&nbsp;&nbsp;&nbsp; set root='(hd0,1)'<BR>&nbsp;&nbsp;&nbsp; search --no-floppy --fs-uuid --set d476-ef15<BR>&nbsp;&nbsp;&nbsp; chainloader +1<BR>}<BR>menuentry "Windows Vista (loader) (on /dev/sda2)" {<BR>&nbsp;&nbsp;&nbsp; insmod ntfs<BR>&nbsp;&nbsp;&nbsp; set root='(hd0,2)'<BR>&nbsp;&nbsp;&nbsp; search --no-floppy --fs-uuid --set 788ac4988ac453f2<BR>&nbsp;&nbsp;&nbsp; chainloader +1<BR>}<BR>### END /etc/grub.d/30_os-prober ###<BR><BR>### BEGIN /etc/grub.d/40_custom ###<BR># This file provides an easy way to add custom menu entries.&nbsp; Simply type the<BR># menu entries you want to add after this comment.&nbsp; Be careful not to change<BR># the 'exec tail' line above.<BR>### END /etc/grub.d/40_custom ###<BR><BR>============================= sda5/Wubi/etc/fstab: =============================<BR><BR># /etc/fstab: static file system information.<BR>#<BR># Use 'blkid -o value -s UUID' to print the universally unique identifier<BR># for a device; this may be used with UUID= as a more robust way to name<BR># devices that works even if disks are added and removed. See fstab(5).<BR>#<BR># &lt;file system&gt; &lt;mount point&gt;&nbsp; &lt;type&gt;&nbsp; &lt;options&gt;&nbsp; &nbsp; &nbsp; &lt;dump&gt;&nbsp; &lt;pass&gt;<BR>proc&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; /proc&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; proc&nbsp; &nbsp; nodev,noexec,nosuid 0&nbsp; &nbsp; &nbsp; 0<BR>/host/ubuntu/disks/root.disk /&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ext4&nbsp; &nbsp; loop,errors=remount-ro 0&nbsp; &nbsp; &nbsp; 1<BR>/host/ubuntu/disks/swap.disk none&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; swap&nbsp; &nbsp; loop,sw&nbsp; &nbsp; &nbsp; &nbsp; 0&nbsp; &nbsp; &nbsp; 0<BR><BR>================= sda5/Wubi: Location of files loaded by Grub: =================<BR><BR><BR>&nbsp; 11.0GB: boot/grub/core.img<BR>&nbsp; 9.1GB: boot/grub/grub.cfg<BR>&nbsp; &nbsp; .9GB: boot/initrd.img-2.6.32-24-generic<BR>&nbsp; 2.9GB: boot/initrd.img-2.6.32-25-generic<BR>&nbsp; 3.5GB: boot/initrd.img-2.6.32-26-generic<BR>&nbsp; 11.4GB: boot/vmlinuz-2.6.32-24-generic<BR>&nbsp; 1.8GB: boot/vmlinuz-2.6.32-25-generic<BR>&nbsp; 11.9GB: boot/vmlinuz-2.6.32-26-generic<BR>&nbsp; 3.5GB: initrd.img<BR>&nbsp; 2.9GB: initrd.img.old<BR>&nbsp; 11.9GB: vmlinuz<BR>&nbsp; 1.8GB: vmlinuz.old<BR>
```

---

### Post by bcbc on 2010-12-07
See [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) (Problem #1)

---

