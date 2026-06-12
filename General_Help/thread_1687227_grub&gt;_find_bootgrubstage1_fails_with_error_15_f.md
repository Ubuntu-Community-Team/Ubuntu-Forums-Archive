---
title: "grub&gt; find /boot/grub/stage1 fails with error 15: file not found"
date: 2011-02-13
forum: General Help
---

### Post by Ninja duck on 2011-02-13
I messed up my boot to ubuntu somehow, but booting to windows xp works. (which i installed after ubuntu, which helped in screwing up the ubuntu boot)

Most help I found for this tell me to boot to live cd (which i'm on now) say to run grub in terminal and type

find /boot/grub/stage1

or

find /grub/stage1

and both returned

Error 15: File not found

I get the same error when i boot to the SGD (Super-Grub Disc) and try any of the linux booting options. I can't get ubuntu to run.

---

### Post by oldfred on 2011-02-13
What version are you running. Most are grub2 now and there is no stage1. 

For help on exact commands to fix:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

Or see instructions for grub2:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Ninja duck on 2011-04-06
Huge delay.

I've finally gotten to trying to fix ubuntu again. I ran the code you wanted me to.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Syslinux is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

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
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    10,233,404    10,233,342   7 HPFS/NTFS
/dev/sda2          10,233,405    74,862,899    64,629,495  83 Linux
/dev/sda3          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sda5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4007 MB, 4007657472 bytes
5 heads, 32 sectors/track, 48921 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          8,064     7,827,455     7,819,392   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        F810D7D510D79948                       ntfs                                     
/dev/sda2        f837fa75-d372-4f27-9dd8-116ba758fc37   ext4                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        a347b264-a10c-4dd6-85e7-21310cf5c024   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        28D8C262D8C22DBE                       ntfs       Storage                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        98C1-02F7                              vfat       PATRIOT                       
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set f837fa75-d372-4f27-9dd8-116ba758fc37
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set f837fa75-d372-4f27-9dd8-116ba758fc37
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f837fa75-d372-4f27-9dd8-116ba758fc37
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=f837fa75-d372-4f27-9dd8-116ba758fc37 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f837fa75-d372-4f27-9dd8-116ba758fc37
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=f837fa75-d372-4f27-9dd8-116ba758fc37 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f837fa75-d372-4f27-9dd8-116ba758fc37
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=f837fa75-d372-4f27-9dd8-116ba758fc37 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f837fa75-d372-4f27-9dd8-116ba758fc37
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=f837fa75-d372-4f27-9dd8-116ba758fc37 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f837fa75-d372-4f27-9dd8-116ba758fc37
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=f837fa75-d372-4f27-9dd8-116ba758fc37 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f837fa75-d372-4f27-9dd8-116ba758fc37
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=f837fa75-d372-4f27-9dd8-116ba758fc37 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f837fa75-d372-4f27-9dd8-116ba758fc37
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f837fa75-d372-4f27-9dd8-116ba758fc37 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f837fa75-d372-4f27-9dd8-116ba758fc37
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=f837fa75-d372-4f27-9dd8-116ba758fc37 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f837fa75-d372-4f27-9dd8-116ba758fc37
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f837fa75-d372-4f27-9dd8-116ba758fc37 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f837fa75-d372-4f27-9dd8-116ba758fc37
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=f837fa75-d372-4f27-9dd8-116ba758fc37 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f837fa75-d372-4f27-9dd8-116ba758fc37
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set f837fa75-d372-4f27-9dd8-116ba758fc37
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda2/etc/fstab: ===============================

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
UUID=a347b264-a10c-4dd6-85e7-21310cf5c024 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


   6.3GB: boot/grub/core.img
  15.2GB: boot/grub/grub.cfg
   5.6GB: boot/initrd.img-2.6.32-21-generic
   6.0GB: boot/initrd.img-2.6.32-24-generic
   6.6GB: boot/initrd.img-2.6.32-25-generic
  10.2GB: boot/initrd.img-2.6.32-26-generic
  11.7GB: boot/initrd.img-2.6.32-27-generic
   5.3GB: boot/vmlinuz-2.6.32-21-generic
   6.0GB: boot/vmlinuz-2.6.32-24-generic
   6.0GB: boot/vmlinuz-2.6.32-25-generic
  10.2GB: boot/vmlinuz-2.6.32-26-generic
  10.3GB: boot/vmlinuz-2.6.32-27-generic
  11.7GB: initrd.img
  10.2GB: initrd.img.old
  10.3GB: vmlinuz
  10.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  fe 44 88 4e a7 02 82 e7  6c df 54 00 e2 38 26 29  |.D.N....l.T..8&)|
00000010  84 bf 51 9d 24 d1 d6 5c  ca 5a 74 86 7d cc 5a 40  |..Q.$..\.Zt.}.Z@|
00000020  f3 09 1a c7 dc 3c 42 fc  9a 5c b1 91 17 c9 d4 fc  |.....<B..\......|
00000030  6e fa 16 e2 f2 0f 9f 46  65 bb d4 4a 37 b3 0e a4  |n......Fe..J7...|
00000040  87 1a cc 64 dd 0b 77 90  4a 25 8c ca ed 40 1c 98  |...d..w.J%...@..|
00000050  d0 72 63 d0 ac ed 28 02  50 b6 74 bb f6 52 ab ec  |.rc...(.P.t..R..|
00000060  1d f6 f8 da 80 e8 10 9d  14 89 83 ce 46 0c 0a a1  |............F...|
00000070  2a 13 6f 65 8c 8c 0b 1d  65 d3 7e dc 63 64 28 04  |*.oe....e.~.cd(.|
00000080  a5 a3 d9 57 87 b3 66 49  f5 a9 cf 23 09 ab 66 d0  |...W..fI...#..f.|
00000090  92 2e 60 c0 77 6c 2d e8  b2 13 49 44 3f 3c eb b8  |..`.wl-...ID?<..|
000000a0  13 5f 63 50 14 58 3f a0  9d a5 5e bc ae cf 64 59  |._cP.X?...^...dY|
000000b0  ab 21 f6 85 6f cf 22 af  1b f8 73 10 ed 15 f4 b2  |.!..o."...s.....|
000000c0  56 31 dc 68 13 77 3c c3  e4 10 1c 6a 7c 47 43 39  |V1.h.w<....j|GC9|
000000d0  0c 00 38 00 8f 76 cf af  5d 17 96 ca 2c ef 82 8c  |..8..v..]...,...|
000000e0  bd 78 92 4e a3 16 54 24  67 06 5b af de 96 01 de  |.x.N..T$g.[.....|
000000f0  e9 d6 eb 14 f7 54 36 89  29 c3 ee 3f c9 c4 84 93  |.....T6.)..?....|
00000100  4b 71 af d6 1f 70 40 c6  1c ca fb f3 f9 ef 8d 3b  |Kq...p@........;|
00000110  d9 df db 16 72 15 2f 85  fd 07 65 e1 85 cd 84 b3  |....r./...e.....|
00000120  06 fe a0 a1 be 66 19 48  ce b8 e0 33 ad 86 2f aa  |.....f.H...3../.|
00000130  4c 8b 9a 01 b0 7a d5 1a  44 a5 84 38 f3 68 d7 27  |L....z..D..8.h.'|
00000140  20 67 88 52 36 28 71 07  63 11 25 ff 4c 4d 42 56  | g.R6(q.c.%.LMBV|
00000150  24 92 62 7b cb b8 03 84  a0 e2 15 c5 2c e8 db c4  |$.b{........,...|
00000160  97 7f 72 4b 74 c6 a5 cd  ff 72 60 50 97 d1 c5 ac  |..rKt....r`P....|
00000170  66 67 dd a8 d6 1c 4c c4  16 f9 32 b9 9f 04 e7 47  |fg....L...2....G|
00000180  91 d3 e2 e3 4b 72 46 8b  d0 83 2a c9 96 df c6 4a  |....KrF...*....J|
00000190  29 dc 43 a8 8d 38 0f b8  86 3f ba 06 2a eb 28 71  |).C..8...?..*.(q|
000001a0  e3 94 35 e3 ea 86 83 1c  43 2b 66 b3 fd 90 07 12  |..5.....C+f.....|
000001b0  dc 5b 3d 33 a6 15 85 83  00 1c 52 6d 1e 1f 00 3c  |.[=3......Rm...<|
000001c0  c9 ff 82 7a f9 ff 02 00  00 00 00 50 32 00 00 00  |...z.......P2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```I then followed the instructions in the first help thread you posted. I mkdir'd and mounted sda2 and did the sudo grub install and got "Installation finished. No error reported."

I'll reboot and see if it worked then report back. (though i've tried tons of grub install help threads and none have worked so far, this might.)


*EDIT:
Rebooted, and it displayed a _ for a while at the top left of the screen, then booted to ubuntu. It gave me no grub choices. This happened last time i restored ubuntu, and i used livecd to restore windows, and then ubuntu didn't show up again and i couldn't get it back (until now).

How do I get a dual-boot?

---

### Post by oldfred on 2011-04-06
Sometimes grub needs a little help:

Boot your install and at a terminal run this:

sudo update-grub

That should scan system, find windows & add it to the grub menu. 

When grub has only found one system it does not even show menu unless you hold down shift key from BIOS boot.

---

### Post by grahammechanical on 2011-04-06
Here is a link to the community documentation

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

It is a long read.

Regards.

---

### Post by oldfred on 2011-04-06
I missed the first time  you do not have grub in the MBR of drive sda.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda2 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda2
sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

---

### Post by Ninja duck on 2011-04-07
Followed your instructions until i got to the "reboot into working system."
The grub menu shows up this time, gives me the normal ubuntu list when i go into the menu, doesn't show windows. I try to boot into any of them and it gives me
"error 15: file not found"

I'm back to the liveCD with no other OS. I'm gonna try some ways I already tried before to fix the boot but i'm not sure if It will change anything.


AFTER REBOOT: i did the same thing that worked earlier in this forum, and i'm back to no grub menu but a working ubuntu boot. I'm done trying to get windows, it's not important enough to risk losing ubuntu again. Thanks for all your help.

---

### Post by oldfred on 2011-04-07
error 15 is usually from old grub legacy. Do you have part of it still on  your system. That sometimes interferes with grub2.

If grub has not found windows, it does not show a menu.

sudo update-grub

That should find windows & add it to the menu. Then you should be able to boot windows.

---

