---
title: "Help with dual booting 10.04 and windows xp"
date: 2010-07-26
forum: General Help
---

### Post by staterunner180 on 2010-07-26
Okay, so just let me say that i have seen posts of others that have a similar problem, but nothing exactly like my situation.

So i have a 650 GB HD and wanted to dual boot XP and ubuntu 10.04. so i installed XP since i've seen that its recommended to do so. then i went into disk management (Start>right-click my computer>manage>disk management) and created a partition of about 150 GB for ubuntu.

then i took the LiveCD and in the installation i just chose to have ubuntu installed on the 'largest continuous free space' or something to that effect. so now i have 456 GB for XP, 134 GB for ubuntu, and 5 GB which im assuming is the 'swap.' but on disk management it defines both the ubuntu partition and the 'swap' partition as 'healthy (unknown partition).'

and when i boot up, the bootloader sends my straight to XP, there in no choice for ubuntu or anything. and i've tried holding down the shift key (i read this on some post on this forum) to get the  boot menu to come up but nothing. i think i need to install the GRUB or GRUB2 bootloader, but have no idea how to do that, or where to even start. i have EasyBCD 2.0.1 downloaded on XP if that will help any.

all posts, answers and suggestions are greatly appreciated!!

---

### Post by Rubi1200 on 2010-07-26
Hi and welcome.
 
Use the LiveCD and boot the computer. Then follow the instructions in the link at the botttom of my post.
 
Post the results back here.
 
Once we have an overview of your setup we can offer advice and solutions.
 
Good luck!

---

### Post by staterunner180 on 2010-07-27
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

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

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    76,908,543    76,906,496  83 Linux
/dev/sda2          76,910,590    80,291,839     3,381,250   5 Extended
/dev/sda5          76,910,592    80,291,839     3,381,248  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   956,482,574   956,482,512   7 HPFS/NTFS
/dev/sdb2         956,483,582 1,250,263,039   293,779,458   5 Extended
/dev/sdb5         956,483,584 1,238,249,471   281,765,888  83 Linux
/dev/sdb6       1,238,251,520 1,250,263,039    12,011,520  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 507 MB, 507322880 bytes
16 heads, 63 sectors/track, 983 cylinders, total 990865 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                 237       990,863       990,627   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C2AC-4954                              vfat       Old IDE                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        ff05b972-909c-40ab-993e-b61db66460bd   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        52C8C39AC8C37AAD                       ntfs                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        983ab287-2cbd-4ec7-a85e-7d082e9b08ee   ext4                                     
/dev/sdb6        b4545cd5-9758-4bd0-9f77-864d75b1f31b   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        30E5-9DAC                              vfat                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr2         /media/U3 System         iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdc1        /media/30E5-9DAC         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 983ab287-2cbd-4ec7-a85e-7d082e9b08ee
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 983ab287-2cbd-4ec7-a85e-7d082e9b08ee
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 983ab287-2cbd-4ec7-a85e-7d082e9b08ee
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=983ab287-2cbd-4ec7-a85e-7d082e9b08ee ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 983ab287-2cbd-4ec7-a85e-7d082e9b08ee
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=983ab287-2cbd-4ec7-a85e-7d082e9b08ee ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 983ab287-2cbd-4ec7-a85e-7d082e9b08ee
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 983ab287-2cbd-4ec7-a85e-7d082e9b08ee
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 52c8c39ac8c37aad
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=983ab287-2cbd-4ec7-a85e-7d082e9b08ee /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=b4545cd5-9758-4bd0-9f77-864d75b1f31b none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 623.0GB: boot/grub/core.img
 597.2GB: boot/grub/grub.cfg
 623.0GB: boot/initrd.img-2.6.32-21-generic
 623.0GB: boot/vmlinuz-2.6.32-21-generic
 623.0GB: initrd.img
 623.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  1b 29 34 1b 29 34 1b 29  34 1b 2b 34 1b 2b 34 1b  |.)4.)4.)4.+4.+4.|
00000010  2b 34 1b 2b 34 1b 2b 34  1b 2b 34 1b 2b 34 1b 2b  |+4.+4.+4.+4.+4.+|
00000020  34 1b 29 34 1b 29 34 1e  2b 36 1e 2b 36 1b 2c 36  |4.)4.)4.+6.+6.,6|
00000030  1b 2c 36 1b 2c 36 1b 2c  36 1b 2c 36 1b 2c 36 1b  |.,6.,6.,6.,6.,6.|
00000040  2c 36 1b 2c 36 1b 2c 36  1b 2c 36 1b 2c 36 1b 2c  |,6.,6.,6.,6.,6.,|
00000050  36 d6 d3 ce 08 14 08 08  14 08 08 14 08 08 10 00  |6...............|
00000060  08 10 00 08 10 00 6b 71  68 bd be bd 26 2b 31 26  |......kqh...&+1&|
00000070  2b 31 26 2b 31 21 29 31  21 29 31 21 29 31 21 29  |+1&+1!)1!)1!)1!)|
00000080  31 1e 29 34 1e 29 34 1e  29 34 1b 2b 36 1b 2b 34  |1.)4.)4.)4.+6.+4|
00000090  1e 2d 36 1e 2d 36 1e 2d  36 1e 2d 39 1b 2f 39 1b  |.-6.-6.-6.-9./9.|
000000a0  2f 39 1b 2f 39 1e 2f 39  1e 2f 39 1e 2f 39 1b 2d  |/9./9./9./9./9.-|
000000b0  39 1b 2d 36 1b 2d 36 1b  2d 36 1b 2d 36 1b 2d 36  |9.-6.-6.-6.-6.-6|
000000c0  1b 2d 36 1b 2d 36 1b 2d  36 1e 2d 36 1e 2d 36 1e  |.-6.-6.-6.-6.-6.|
000000d0  2d 36 1e 2d 36 1b 2c 36  1b 2c 36 1b 2c 36 1b 2c  |-6.-6.,6.,6.,6.,|
000000e0  36 1b 2b 36 1b 2b 36 1b  2b 36 1b 2b 36 1b 2c 36  |6.+6.+6.+6.+6.,6|
000000f0  1b 2c 36 1b 2c 36 1b 2c  36 1e 2d 39 1b 2f 39 1b  |.,6.,6.,6.-9./9.|
00000100  2f 39 1b 2f 39 1e 2f 39  1e 2f 39 1e 2f 39 1e 2f  |/9./9./9./9./9./|
00000110  39 1e 2f 39 1e 2f 39 1e  2f 39 1e 2f 39 1e 2e 39  |9./9./9./9./9..9|
00000120  1e 2e 39 1e 2e 39 1e 2e  39 1e 2f 39 1e 2f 39 1e  |..9..9..9./9./9.|
00000130  2f 39 1e 2f 39 1e 2f 39  1e 2f 39 1e 2f 39 1e 2f  |/9./9./9./9./9./|
00000140  39 1e 2f 39 21 30 39 21  30 39 21 30 39 1e 31 3c  |9./9!09!09!09.1<|
00000150  1e 31 3c 1e 31 3c 1e 31  3c 21 33 3f 21 33 3f 21  |.1<.1<.1<!3?!3?!|
00000160  34 42 21 34 42 21 34 42  21 35 42 21 37 42 21 38  |4B!4B!4B!5B!7B!8|
00000170  42 24 39 45 26 3b 47 26  3b 47 26 3b 47 29 3c 4a  |B$9E&;G&;G&;G)<J|
00000180  29 3f 4d 29 42 4f 29 42  4f 26 40 4f 26 40 4f 26  |)?M)BO)BO&@O&@O&|
00000190  40 4f 2c 45 55 34 4d 5d  34 4d 5d 34 4d 5d 2e 49  |@O,EU4M]4M]4M].I|
000001a0  58 31 49 5a 34 4d 5d 36  51 60 34 4d 5d 31 51 63  |X1IZ4M]6Q`4M]1Qc|
000001b0  3c 5c 6e 42 61 73 3c 5c  6e 73 99 a4 73 99 00 fe  |<\nBas<\ns..s...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 98 33 00 00 00  |............3...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200







_**SDA IS A 40GB HD THAT I USE FOR STORAGE. SDB IS THE HARD DRIVE WITH EVERYTHING INSTALLED, AS YOU CAN SEE.**_

---

### Post by staterunner180 on 2010-07-27
and SDC is a 512 MB flash drive.

---

### Post by wojox on 2010-07-27
When you installed Ubuntu did you let it install grub to the MBR?

---

### Post by staterunner180 on 2010-07-27
i honestly have no idea. when it came to where on the HD to install ubuntu i just selected 'install on largest continuous free space' or whatever it is and hit next. i let the installation do everything it wanted to. is there anyway that i can find out if GRUB is install but not overriding the windows bootloader?

---

### Post by wojox on 2010-07-27
It appears you installed them on your partition. See here [Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by staterunner180 on 2010-07-27
okay, but which partition do i put into terminal? it would be the 2nd hd so it would be sdb but which partition? would it be the swap or the partition with ubuntu on it?

---

### Post by staterunner180 on 2010-07-27
disregard that last post haha. i just plugged in sdb5 and it worked! i can choose between ubuntu and windows now! for some reason the command 'sudo update-grub' didn't work, but i still have the choice. on that page i saw something about theming the boot menu? is that recommended for a beginner like me to attempt?

---

