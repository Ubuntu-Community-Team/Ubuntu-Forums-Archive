---
title: "Urgent Help with GRUB"
date: 2011-04-25
forum: General Help
---

### Post by nankura on 2011-04-25
hey everybody

ok abit of a story so that you guys understand my situation

Basically, i have 2 hard drives connected to sata ports randomly on my motherboard ( i didnt do it in any order )

1. Western digital 500GB - Windows 7
2. Seagate 500GB - Linux HDD - had ubuntu 10.04 on it before suse

Ok basically, ive been trying distro's by installing them on my linux HD, my favourite is ubuntu, but i wanted to see what else is out there

so i tried out OpenSUSE, and with suse i unfortantly came across many problems with grub-legacy, and i solved that eventually by changing my boot hard disk in BIOS to the seagate, and installing grub on that

Ive never had a grub issue in the past using ubuntu, only with suse

Then i decided to go back to ubuntu because everything just works and i like .deb packages, so i installed 10.10 32Bit

Everything went fine, 
chose default install options, 
formatted the Seagate drive, 
and installed to the seagate, HD
changedt the boot drive to the western digital in BIOS ( were ubuntu likes to install grub in the past )
 booted fine, installed fine, grub showed fine, booted to linux
then i went back to windows for a day of gaming and fun, i just rebooted about 30 minutes ago to play with linux, and i cant access the grub menu

my pc goes to the POST screen and then were grub should show, i get a blank screen and the pc just reboots to the POST constantly

this problem has never happened with ubuntu, ive had 10.10 before, this is all started after removing opensuse 

ive tried F8 and booting from both drives, the seagate i just get a white underline for ages and nothing happens and i cant boot to windows on the WD

Im currently on my livecd

P.S - im using the 11.04 livecd, all my cds arent labelled, so i have no idea which is which, i just chucked one in to get a browser so i can get help haha, but i gotta say natty 11.04 IS AWSOME!!!! , unity rocks xD

---

### Post by nankura on 2011-04-25
please. anybody. i need to get back into windows for my job

---

### Post by Ad@m on 2011-04-25
Please run this boot info script and paste the results.txt file here.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by nankura on 2011-04-25
here it is, its abit long >.<




>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. According to 
                       the info in the boot sector, sda1 has 204799 sectors, 
                       but according to the info from fdisk, it has 1984 
                       sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 206848. But according to the info from 
                       fdisk, sda2 starts at sector 2048. The info in boot 
                       sector on the starting sector of the MFT is wrong. 
                       According to the info in the boot sector, sda2 has 
                       976564223 sectors, but according to the info from 
                       fdisk, it has 204799 sectors.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       206,847       204,800  42 SFS
/dev/sda3             206,848   976,771,071   976,564,224  42 SFS
/dev/sda4         976,771,072   976,771,119            48  42 SFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   946,825,215   946,823,168  83 Linux
/dev/sdb2         946,827,262   976,771,071    29,943,810   5 Extended
/dev/sdb5         946,827,264   976,771,071    29,943,808  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        28020A1E0209F19C                       ntfs                                     
/dev/sda2        F0720899720866A6                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2e99e476-7de3-4936-9a76-6ede260864d0   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        1a1292d0-ebaf-4418-8159-49d2ad6874f4   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 2e99e476-7de3-4936-9a76-6ede260864d0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 2e99e476-7de3-4936-9a76-6ede260864d0
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 2e99e476-7de3-4936-9a76-6ede260864d0
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=2e99e476-7de3-4936-9a76-6ede260864d0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 2e99e476-7de3-4936-9a76-6ede260864d0
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=2e99e476-7de3-4936-9a76-6ede260864d0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 2e99e476-7de3-4936-9a76-6ede260864d0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 2e99e476-7de3-4936-9a76-6ede260864d0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 28020a1e0209f19c
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=2e99e476-7de3-4936-9a76-6ede260864d0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=1a1292d0-ebaf-4418-8159-49d2ad6874f4 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  60.2GB: boot/grub/core.img
 133.3GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.35-28-generic-pae
  60.2GB: boot/vmlinuz-2.6.35-28-generic-pae
    .7GB: initrd.img
  60.2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

MFT Sector of sda1

00000000  46 49 4c 45 30 00 03 00  ea 22 10 00 00 00 00 00  |FILE0...."......|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  03 00 26 86 00 00 00 00  10 00 00 00 60 00 00 00  |..&.........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  41 08 e8 09 90 e0 cb 01  41 08 e8 09 90 e0 cb 01  |A.......A.......|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  41 08 e8 09 90 e0 cb 01  |........A.......|
000000c0  41 08 e8 09 90 e0 cb 01  41 08 e8 09 90 e0 cb 01  |A.......A.......|
000000d0  41 08 e8 09 90 e0 cb 01  00 40 00 00 00 00 00 00  |A........@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  3f 00 00 00 00 00 00 00  |........?.......|
00000120  40 00 00 00 00 00 00 00  00 00 04 00 00 00 00 00  |@...............|
00000130  00 00 04 00 00 00 00 00  00 00 04 00 00 00 00 00  |................|
00000140  21 40 55 21 00 01 68 83  b0 00 00 00 50 00 00 00  |!@U!..h.....P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  01 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 20 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |. ..............|
00000180  08 10 00 00 00 00 00 00  21 01 54 21 21 01 fe fd  |........!.T!!...|
00000190  00 00 01 00 00 20 26 86  ff ff ff ff 00 00 00 00  |..... &.........|
000001a0  00 00 04 00 00 00 00 00  21 40 55 21 00 01 68 83  |........!@U!..h.|
000001b0  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  21 01 54 21 21 01 fe fd  00 00 01 00 00 20 03 00  |!.T!!........ ..|
00000200
MFT Sector of sda2

00000000  46 49 4c 45 30 00 03 00  cb c1 2e 95 01 00 00 00  |FILE0...........|
00000010  01 00 01 00 38 00 01 00  d8 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  08 00 00 00 00 00 00 00  |................|
00000030  b1 5f 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |._..........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  9c 46 84 07 90 e0 cb 01  |.........F......|
000000c0  9c 46 84 07 90 e0 cb 01  9c 46 84 07 90 e0 cb 01  |.F.......F......|
000000d0  9c 46 84 07 90 e0 cb 01  00 00 a4 0b 00 00 00 00  |.F..............|
000000e0  00 00 a4 0b 00 00 00 00  06 00 00 00 00 00 00 00  |................|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 78 00 00 00  01 00 40 00 00 00 01 00  |....x.....@.....|
00000110  00 00 00 00 00 00 00 00  ff e2 00 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 30 0e 00 00 00 00  |@.........0.....|
00000130  00 00 30 0e 00 00 00 00  00 00 30 0e 00 00 00 00  |..0.......0.....|
00000140  32 40 66 00 00 0c 32 40  52 5c df 17 42 c3 01 91  |2@f...2@R\..B...|
00000150  73 9f 03 42 7d 05 c2 16  7a ff 32 f8 16 01 27 0a  |s..B}...z.2...'.|
00000160  42 0a 08 c2 a6 8c 00 32  3e 01 6e 06 a3 22 00 03  |B......2>.n.."..|
00000170  00 77 00 00 00 00 00 00  b0 00 00 00 58 00 00 00  |.w..........X...|
00000180  01 00 40 00 00 00 07 00  00 00 00 00 00 00 00 00  |..@.............|
00000190  07 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
000001a0  00 80 00 00 00 00 00 00  20 7d 00 00 00 00 00 00  |........ }......|
000001b0  20 7d 00 00 00 00 00 00  31 01 ff ff 0b 31 05 f3  | }......1....1..|
000001c0  f4 01 31 01 2d a1 1b 41  01 dc 35 ce 02 00 0f 8c  |..1.-..A..5.....|
000001d0  ff ff ff ff 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 b1 5f  |..............._|
00000200
Unknown BootLoader  on sda3


Unknown BootLoader  on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory

---

### Post by nankura on 2011-04-25
this is very similiar to the opensuse problem

the opensuse community said it was due to some update on windows 7 which appearently messed with grub

the solution was changing the seagate linux hd to my default bios hard drive and installing the bootloader onto the seagate HD

and setting grub to boot from the root partition not the MBR

but i have no idea how ubuntu works or if thats the problem, but its a similiar issue, the grub-legacy ubuntu uses would keep rebooting exactly the same way

---

### Post by Quackers on 2011-04-25
You seem to have a number of problems with sda.
On sda1 and sda2 it seems that the start of the Master File Table is recorded wrongly.
The Windows type partitions on sda are now showing as SFS instead of HPFS. This means that all the Windows partitions now have a SFS file system, ie Windows has changed them from basic partitions to dynamic disks. 
One possible cause for this is that more than the maximum 4 primary partitions on any one hard drive has been exceeded. Have you created a fifth primary partition at any time on sda?
Basically, now Linux cannot read those partitions.If you restore the Windows bootloader to sda using the Windows repair disc you may be able to get Windows booting again. As far as installing any other operating system on sda, you would first need to re-install Windows.
At the moment no bootloader is installed in the mbr of sdb.
If you open a terminal from the live cd desktop you can run these commands, which will install grub to that drive. You can then make that drive bootable in your bios. Ubuntu should then boot.
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

---

### Post by Ad@m on 2011-04-25
EDIT: Quackers beat me to it

Grub has been installed on your Windows drive (/dev/sda) and not on your Ubuntu drive (/dev/sdb)

The best thing to do would be to install grub to your Ubuntu drive, then later configure it to load your windows drive.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Following ^

sudo mount /dev/sdb1 /mnt[FONT=monospace]
s[/FONT]udo grub-install --root-directory=/mnt /dev/sdb

This should make your Ubuntu drive bootable. Let us know the outcome.
[FONT=monospace]
[/FONT]

---

### Post by nankura on 2011-04-25
thankyou so much guys

the 2 simple terminal commands did it, everythings working, grub works on the sdb hard disk just fine and windows boots just fine

Idk about any 5 partitions on windows, i certainly didnt do anything knowingly haha im a noob so i prob did something by accident

tho , a phew days ago ( about 4-5) i did a windows update, and windows rebooted and did a bunch of updates on the splash screen, which scared me, i thought i had a virus or something, but it was an extreme core windows update

ever since that. ive had problems with linux and grubs if anything grub goes on the windows hard disk, it all works fine if its all on the sdb hard disk

---

### Post by Quackers on 2011-04-25
I would recommend backing up wahtever you need off sda. The MFT error is significant. Also the SFS problem won't go away - but it only matters really if you want to put something else on sda.

---

### Post by oldfred on 2011-04-25
I agree with Quackers, you need to have good backups. 

Not sure if some of the issues are just with SFS. I get the idea that even everything in windows does not work as well with dynamic partitions.

You may be able to undo it if you only have 4 partitions and they are each separate. But windows offical policy is to backup, reformat and reinstall all your data, programs & updates.

SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
One user used these two:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

---

