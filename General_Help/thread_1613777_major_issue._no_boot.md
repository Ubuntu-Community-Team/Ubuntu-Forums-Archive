---
title: "major issue. no boot"
date: 2010-11-04
forum: General Help
---

### Post by kirkface8 on 2010-11-04
last night i was watching a family guy episode through vlc on ubuntu.
as the episode finished i opened the avi with vlc and nothing happened. i then tried open vlc separately and it said it could not be found. i thought it probably just crashed so i click the shutdown button and all fonts on the 'shutdown, logout, switch user.' screen were appearing as squares.
on boot all i get is the Plymouth initialized line and that is all.

it seems the whole hard disk has disappeared. is there any fix or cause for this?
Thanks

---

### Post by wilee-nilee on 2010-11-04
Did you try booting a live cd and looking at the OS, it is impossible to ascertain anything from so little information. This may be why you have had no responses hard to say really.

You might consider while using the live cd running the bootscript in my signature, this will create a file with text. Come back to the forums and post the text on code tags as described in my signature. The code tags are very important.

---

### Post by kirkface8 on 2010-11-05
i shall do that now. and yes i understand code tags. And sorry for the little information but thats all i pretty much know.

ill run the script now.

---

### Post by kirkface8 on 2010-11-05
heres the RESULTS.txt
```
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
sda2: _________________________________________________________________________
    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  
sda5: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
sda6: _________________________________________________________________________
    File system:       swap
    Boot sector type:  -
    Boot sector info:  
sda3: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
sda4: _________________________________________________________________________
    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   
sdc1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 1.
    Operating System:  
    Boot files/dirs:   
hda: _________________________________________________________________________
    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst
=========================== Drive/Partition Info: =============================
Drive: sda ___________________ _____________________________________________________
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd58e9730
Partition  Boot         Start           End          Size  Id System
/dev/sda1                  63    78,124,094    78,124,032  83 Linux
/dev/sda2          78,127,102   234,375,167   156,248,066   5 Extended
/dev/sda5          78,127,104   205,078,527   126,951,424   b W95 FAT32
/dev/sda6         205,080,576   234,375,167    29,294,592  82 Linux swap / Solaris
/dev/sda3         234,579,968   532,977,663   298,397,696   7 HPFS/NTFS
/dev/sda4         532,977,664   625,141,759    92,164,096  83 Linux
 
Drive: sdc ___________________ _____________________________________________________
Disk /dev/sdc: 8036 MB, 8036286464 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695872 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000
Partition  Boot         Start           End          Size  Id System
/dev/sdc1                   1    15,695,871    15,695,871   b W95 FAT32
 
blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/hda                                                iso9660    BT4                           
/dev/loop0                                              squashfs                                 
/dev/sda1        660effbe-3e30-4e80-b011-f3e7e49f053d   ext4                                     
/dev/sda3        EA0E44B10E447899                       ntfs                                     
/dev/sda4        ca382a1d-34db-48ed-b45b-7fc2b3589c80   ext4       Data                          
/dev/sda5        4807-71C0                              vfat                                     
/dev/sda6        ec9bf680-bb94-41fb-b538-926cd693322e   swap                                     
/dev/sdc1        124D-4CA5                              vfat       New Volume                    
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
rootfs           /                        rootfs     (rw)
/dev/hda         /media/cdrom0            iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/New Volume        vfat       (rw,nosuid,nodev,noatime,uhelper=hal,flush,uid=0,utf8,shortname=lower)
 
=========================== sda1/boot/grub/grub.cfg: ===========================
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
search --no-floppy --fs-uuid --set 660effbe-3e30-4e80-b011-f3e7e49f053d
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 660effbe-3e30-4e80-b011-f3e7e49f053d
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 660effbe-3e30-4e80-b011-f3e7e49f053d
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=660effbe-3e30-4e80-b011-f3e7e49f053d ro  vga=771  quiet splash
 initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 660effbe-3e30-4e80-b011-f3e7e49f053d
 echo 'Loading Linux 2.6.35-22-generic ...'
 linux /boot/vmlinuz-2.6.35-22-generic root=UUID=660effbe-3e30-4e80-b011-f3e7e49f053d ro single  vga=771
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.34-020634-generic' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 660effbe-3e30-4e80-b011-f3e7e49f053d
 linux /boot/vmlinuz-2.6.34-020634-generic root=UUID=660effbe-3e30-4e80-b011-f3e7e49f053d ro  vga=771  quiet splash
 initrd /boot/initrd.img-2.6.34-020634-generic
}
menuentry 'Ubuntu, with Linux 2.6.34-020634-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
 recordfail
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 660effbe-3e30-4e80-b011-f3e7e49f053d
 echo 'Loading Linux 2.6.34-020634-generic ...'
 linux /boot/vmlinuz-2.6.34-020634-generic root=UUID=660effbe-3e30-4e80-b011-f3e7e49f053d ro single  vga=771
 echo 'Loading initial ramdisk ...'
 initrd /boot/initrd.img-2.6.34-020634-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###
### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 660effbe-3e30-4e80-b011-f3e7e49f053d
 linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
 insmod part_msdos
 insmod ext2
 set root='(hd0,msdos1)'
 search --no-floppy --fs-uuid --set 660effbe-3e30-4e80-b011-f3e7e49f053d
 linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb3)" {
 insmod part_msdos
 insmod ntfs
 set root='(hd0,msdos3)'
 search --no-floppy --fs-uuid --set ea0e44b10e447899
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
=============================== sda1/etc/fstab: ===============================
 
UUID=660effbe-3e30-4e80-b011-f3e7e49f053d / ext4 users 0 0
UUID=EA0E44B10E447899 /media/EA0E44B10E447899 ntfs-3g users 0 0
UUID=ec9bf680-bb94-41fb-b538-926cd693322e swap swap sw 0 0
UUID=ca382a1d-34db-48ed-b45b-7fc2b3589c80 /media/Data ext4 users 0 0
 
=================== sda1: Location of files loaded by Grub: ===================
 
  17.3GB: boot/grub/core.img
  11.2GB: boot/grub/grub.cfg
  17.6GB: boot/initrd.img-2.6.34-020634-generic
  11.8GB: boot/initrd.img-2.6.35-22-generic
  17.4GB: boot/vmlinuz-2.6.34-020634-generic
  17.5GB: boot/vmlinuz-2.6.35-22-generic
  11.8GB: initrd.img
  17.6GB: initrd.img.old
  17.5GB: vmlinuz
  17.4GB: vmlinuz.old
=========================== hda/boot/grub/menu.lst: ===========================
# By default, boot the first entry.
default 0
# Boot automatically after 30 secs.
timeout 30
splashimage=/boot/grub/bt4.xpm.gz
foreground e3e3e3
background 303030
title                Start BackTrack FrameBuffer (1024x768)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
initrd                /boot/initrd.gz
title                Start BackTrack FrameBuffer (800x600)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x314
initrd                /boot/initrd800.gz
title                Start BackTrack Forensics (no swap)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
initrd                /boot/initrdfr.gz
title                Start BackTrack in Safe Graphical Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper xforcevesa rw quiet 
initrd                /boot/initrd.gz
title                Start Persistent Live CD
kernel                /boot/vmlinuz BOOT=casper boot=casper persistent rw quiet 
initrd                /boot/initrd.gz
title                Start BackTrack in Text Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw quiet
initrd                /boot/initrd.gz
title                Start BackTrack Graphical Mode from RAM
kernel                /boot/vmlinuz BOOT=casper boot=casper toram nopersistent rw quiet 
initrd                /boot/initrd.gz
title                Memory Test
kernel                /boot/memtest86+.bin
title                Boot the First Hard Disk
root                (hd0)
chainloader +1
==================== hda: Location of files loaded by Grub: ====================
 
    .0GB: boot/grub/menu.lst
    .0GB: boot/initrd800.gz
    .0GB: boot/initrdfr.gz
    .0GB: boot/initrd.gz
    .0GB: boot/vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================
Unknown BootLoader  on sda2
00000000  a3 0e 7d 0e 26 0e 3b 0f  94 0f 9f 0f 74 0e e9 0a  |..}.&.;.....t...|
00000010  ef 06 e0 04 fc 02 8c 01  6a ff b4 fb a3 f9 3c f8  |........j.....<.|
00000020  53 f6 02 f6 69 f6 35 f6  ea f5 91 f4 f4 f0 71 f0  |S...i.5.......q.|
00000030  5e f1 1f f1 ae f3 7d f4  10 f5 f8 f5 3d f4 27 f1  |^.....}.....=.'.|
00000040  43 ef 43 ee 9f f0 b2 f2  0c f3 12 f5 46 f5 3a f6  |C.C.........F.:.|
00000050  2f f7 fa f5 ae f5 ab f6  8c f5 3f f5 27 f4 0e f6  |/.........?.'...|
00000060  f2 f9 51 fb 65 fb 98 fb  05 fc 2d fb a8 fa c3 f9  |..Q.e.....-.....|
00000070  5c f9 5e fa f9 f8 b2 f7  5b f9 ea fc 3a ff 03 fe  |\.^.....[...:...|
00000080  d2 fb 93 fb 5d fa fc f9  f1 fb ac fc fd fe 8f 00  |....]...........|
00000090  27 01 8a 01 bf 02 8a 02  9e 01 dd 01 56 03 bf 02  |'...........V...|
000000a0  b9 03 7c 08 82 09 a7 08  b4 07 36 06 db 05 95 06  |..|.......6.....|
000000b0  37 06 5e 04 75 03 27 02  c0 02 54 04 a2 07 58 0b  |7.^.u.'...T...X.|
000000c0  04 0e 77 0f e8 0d 53 0c  6c 0d 0b 0c b9 09 69 0b  |..w...S.l.....i.|
000000d0  e0 0c bd 0d f8 0d 0d 0e  74 0e a0 0d 86 0b 81 0b  |........t.......|
000000e0  0e 0d c8 0d 57 0d 14 08  69 04 95 02 87 01 13 02  |....W...i.......|
000000f0  13 00 49 fd 37 fd 2c fc  ce f9 43 fa 44 f9 49 f8  |..I.7.,...C.D.I.|
00000100  6b f8 13 fa 76 fb 6b fc  b6 fd 04 fe 94 fd a2 fd  |k...v.k.........|
00000110  2f fb b8 fc a0 fc 57 f9  88 f8 27 f8 a7 f8 a1 fa  |/.....W...'.....|
00000120  6a fc d1 fb 41 fb 02 fc  ed fa 8d fc 7d fe 97 fe  |j...A.......}...|
00000130  8d fe e1 fd cd fe 4a 01  21 04 ed 05 b7 04 77 02  |......J.!.....w.|
00000140  b9 03 ba 03 4c 02 6f 02  62 02 d0 00 2a ff 05 ff  |....L.o.b...*...|
00000150  3d ff 17 00 8f ff a0 fe  00 00 2e 01 2a 01 8a 00  |=...........*...|
00000160  50 00 b6 ff b3 fe 79 fe  ec ff fa 00 e8 fd aa fc  |P.....y.........|
00000170  d6 fc 9d fb 75 fb a5 f9  51 f7 60 f7 af f8 09 fa  |....u...Q.`.....|
00000180  f2 fa 12 fb e5 fc 02 fe  37 ff 0a ff 81 fd 2b fe  |........7.....+.|
00000190  16 00 dc fe de fc b6 fd  99 fe 45 00 d3 00 2e 00  |..........E.....|
000001a0  92 01 64 03 f0 03 44 02  bb ff 9f fe 0d ff 10 ff  |..d...D.........|
000001b0  e1 fd 0c fe aa ff 1a 00  54 00 97 01 2b 02 00 fe  |........T...+...|
000001c0  ff ff 0b fe ff ff 02 00  00 00 00 20 91 07 00 fe  |........... ....|
000001d0  ff ff 05 fe ff ff 02 20  91 07 00 08 bf 01 00 00  |....... ........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
 
=======Devices which don't seem to have a corresponding hard drive==============
sdb 

```
 
yeah i ran this through backtrack
i hope this is okay could not find my ubuntu live cd

---

### Post by drs305 on 2010-11-05
One quick check would be to edit your first entry from the Grub menu - press "e" to open the menuentry for editing.

Go to the "linux" line and remove the "vga=771", then CTRL-x to boot. It's probably not the problem but it is a deprecated video mode that *could* be a possible conflict.

---

### Post by kirkface8 on 2010-11-05
> **drs305 said:**
> One quick check would be to edit your first entry from the Grub menu - press "e" to open the menuentry for editing.

Go to the "linux" line and remove the "vga=771", then CTRL-x to boot. It's probably not the problem but it is a deprecated video mode that *could* be a possible conflict.
okay sure
ill try that.

---

### Post by kirkface8 on 2010-11-05
changing the grub config did not work

---

### Post by drs305 on 2010-11-05
You state that the hard drive seems to have disappeared. Have you checked the partition for filesystem errors?

You can check by running this from the LiveCD - the partition must be unmounted:
```
sudo e2fsck -C0 -p -f -v /dev/sda1
*if errors:*
sudo e2fsck -f -y -v /dev/sda1
```

---

### Post by kirkface8 on 2010-11-05
> **drs305 said:**
> You state that the hard drive seems to have disappeared. Have you checked the partition for filesystem errors?

You can check by running this from the LiveCD - the partition must be unmounted:
```
sudo e2fsck -C0 -p -f -v /dev/sda1
*if errors:*
sudo e2fsck -f -y -v /dev/sda1
```
yeah as i was using it the programs seemed to be disapearing and as well as the fonts.
then booting into recovery mode lists that all the system folders are empty.
before you ask if i ran any comands. no i didnt.
the system was working perfectly all day. and as i changed to a different avi i noticed the problem.
but i shall check the disk for errors now.

---

### Post by kirkface8 on 2010-11-05
just ran that.
there were few errors. succesfuly fixed them.
ill attempt a boot now
the hardisk files seem to be all intact though

---

### Post by kirkface8 on 2010-11-05
as i boot the plymouth starts.
which is just the text based one saying ubuntu with the "."(fullstops) changing color.
pushing f1 displays 
```
init: plymouth main process (339) terminated with status 1
```

---

### Post by kirkface8 on 2010-11-05
booting standard it has the text plymouth. ubuntu with the fullstops changing color below.pushing f1 displays the plymouth process has been terminated.
 
recovery mode runs commands then halts at. 
```

init: mountall main process (422) terminated with status 1
init: failed to spawn mountain post-stop process: unable to exectue: Permission denied

```
 
i cant right it all down but its then followed by the same structure. etc 'init: failed - Permission denied' by the processes
spawn plymouth
spawn mountall
spawn mountall-shell
spawn udev 
 
all of these are unable to execute

---

### Post by chaanakya_chiraag on 2010-11-05
That is a big problem...I think that means the permissions are wrong on the boot scripts or something...not sure though...

---

### Post by kirkface8 on 2010-11-05
ahh dammnit. this is really bugging me

---

### Post by kirkface8 on 2010-11-05
im wondering if this could be something to do with the time. the problem seemed to arouse from 12am on the dot. and was working perfect all day
 
 
EDIT: [http://ubuntuforums.org/showthread.php?t=1335937](http://ubuntuforums.org/showthread.php?t=1335937) is that similar to my issue?

---

### Post by chaanakya_chiraag on 2010-11-06
I don't think it is unless you edited /etc/conf/sreadahead.conf.  I think the best thing to do is to boot up a live cd, back up all your stuff, and reinstall.

---

### Post by kirkface8 on 2010-11-07
> **chaanakya_chiraag said:**
> I don't think it is unless you edited /etc/conf/sreadahead.conf.  I think the best thing to do is to boot up a live cd, back up all your stuff, and reinstall.
yeah i didnt edit it.
ive got a backup buts its not heeps recent but if i cant find a solution i shall use the backup

---

### Post by chaanakya_chiraag on 2010-11-07
Basically, if even the recovery mode isn't working...you have a MAJOR problem, and even if you DO manage to get things working again (a.k.a actually make it boot up), things will probably be completely screwy anyway.  Therefore, I would definitely just do a backup and reinstall.

---

### Post by kirkface8 on 2010-11-09
did a backup and restore. Sorry i could not solve this if anyone else encounters this issue.

---

