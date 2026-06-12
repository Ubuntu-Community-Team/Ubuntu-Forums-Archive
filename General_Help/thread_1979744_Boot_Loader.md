---
title: "Boot Loader"
date: 2012-05-14
forum: General Help
---

### Post by bheemamahesh on 2012-05-14
Hello Every one

i ve installed Windows 7 in Primary and created "/" and "swap" in logical for backbox after that i accidentally selected the drive where i installed windows 7 for boot loader

now backbox is working fine and windows is not opening for me 

pls help me out from this

---

### Post by carl4926 on 2012-05-14
what error are you getting when selecting windows from grub?

---

### Post by bheemamahesh on 2012-05-14
> **carl4926 said:**
> what error are you getting when selecting windows from grub?

nothing..when i select the windows 7 i didnt get anything...it just blinks and same page exists

---

### Post by carl4926 on 2012-05-14
You need to be more specific about your number of HD's and the partitioning and boot order.
You obviously have grub working

Try running this in Linux

```
sudo update-grub
```

---

### Post by bheemamahesh on 2012-05-14
> **carl4926 said:**
> You need to be more specific about your number of HD's and the partitioning and boot order.
You obviously have grub working

Try running this in Linux

```
sudo update-grub
```
got this by running sudo update-grub

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-15-generic
Found initrd image: /boot/initrd.img-2.6.38-15-generic
Found linux image: /boot/vmlinuz-2.6.38-14-generic
Found initrd image: /boot/initrd.img-2.6.38-14-generic
Found memtest86+ image: /boot/memtest86+.bin
  No volume groups found
Found Windows 7 (loader) on /dev/sda1
done

---

### Post by carl4926 on 2012-05-14
try windows again

if it still doesn't work
tell us about your HD's and boot order

do you think you installed grub to sda or a partition of sda such as sda1

---

### Post by bheemamahesh on 2012-05-14
> **carl4926 said:**
> try windows again

if it still doesn't work
tell us about your HD's and boot order

do you think you installed grub to sda or a partition of sda such as sda1
i tried and not working :(

i think i ve to install grub to sda
i installed grub to sda1

---

### Post by carl4926 on 2012-05-14
If you wrote grub to sda1 you'll need to fix windows. depending what sda1 is?
grub should have gone to the mbr of sda

either start over or fix windows with the windows dvd
then use supergrubdisk to boot ubuntu
and do
sudo update-grub
```
sudo grub-install /dev/sda
```


> Win7 Boot repair:
Boot off the windows 7 installation DVD
Proceed to the screen "Windows 7 / Install Now" BUT DO NOT click to install
Select to "Repair your computer"
Select/put the radio button/dot next to "Use recovery tools that can help fix problems" --> Next
Select "command prompt"
enter this command: Bootrec.exe /FixBoot
enter this command: Bootrec.exe /FixMbr
enter this command: exit
Click to Restart 

---

### Post by wilee-nilee on 2012-05-14
If you put grub in the windows partition you will not boot to windows, good news this is fixable. So lets confirm whats up, down load this link. Extract it to your desktop and run the command, and post the results.txt

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by bheemamahesh on 2012-05-14
after fixing windows only windows will boot? and i ve to use ubuntu live disc and update grub?

---

### Post by bheemamahesh on 2012-05-14
> **wilee-nilee said:**
> If you put grub in the windows partition you will not boot to windows, good news this is fixable. So lets confirm whats up, down load this link. Extract it to your desktop and run the command, and post the results.txt

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

Results.txt


                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 290147160 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  BackBox Linux 2.05
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848    84,084,735    83,877,888   7 NTFS / exFAT / HPFS
/dev/sda3          84,086,782   312,580,095   228,493,314   f W95 Extended (LBA)
/dev/sda5          84,086,784   272,830,463   188,743,680   7 NTFS / exFAT / HPFS
/dev/sda6         272,832,512   307,986,431    35,153,920  83 Linux
/dev/sda7         307,988,480   312,580,095     4,591,616  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 1134f17a-1ca6-45aa-b9b5-3c0e4ae88536   swap       
/dev/sda1        3826768526764442                       ntfs       System Reserved
/dev/sda2        56BC22B1BC228C15                       ntfs       
/dev/sda5        54A4FA18A4F9FC74                       ntfs       New Volume
/dev/sda6        8bcf173b-032c-451e-85c4-5e9d8d5670ab   ext4       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
	linux	/boot/vmlinuz-2.6.38-15-generic root=UUID=8bcf173b-032c-451e-85c4-5e9d8d5670ab ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
	echo	'Loading Linux 2.6.38-15-generic ...'
	linux	/boot/vmlinuz-2.6.38-15-generic root=UUID=8bcf173b-032c-451e-85c4-5e9d8d5670ab ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
	linux	/boot/vmlinuz-2.6.38-14-generic root=UUID=8bcf173b-032c-451e-85c4-5e9d8d5670ab ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
	echo	'Loading Linux 2.6.38-14-generic ...'
	linux	/boot/vmlinuz-2.6.38-14-generic root=UUID=8bcf173b-032c-451e-85c4-5e9d8d5670ab ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-14-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 3826768526764442
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=8bcf173b-032c-451e-85c4-5e9d8d5670ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
#UUID=bfc3b6a3-eab2-4934-a88e-9c21a9b0dad7 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 138.352973938 = 148.555374592  boot/grub/core.img                             1
 132.542179108 = 142.316081152  boot/grub/grub.cfg                             1
 131.760742188 = 141.477019648  boot/initrd.img-2.6.38-14-generic              2
 131.885742188 = 141.611237376  boot/initrd.img-2.6.38-15-generic              2
 131.272769928 = 140.953063424  boot/vmlinuz-2.6.38-14-generic                 1
 131.288394928 = 140.969840640  boot/vmlinuz-2.6.38-15-generic                 1
 131.885742188 = 141.611237376  initrd.img                                     2
 131.760742188 = 141.477019648  initrd.img.old                                 2
 131.288394928 = 140.969840640  vmlinuz                                        1
 131.272769928 = 140.953063424  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  93 d7 76 41 a8 40 f0 b5  6e de f9 61 0d aa 0d 13  |..vA.@..n..a....|
00000010  6b 92 48 44 2a 24 61 bf  fc 3b 0b 23 2a 1a 1c a6  |k.HD*$a..;.#*...|
00000020  89 1b 14 c2 d8 b1 c1 05  0e 0d 36 1d 84 89 0e 70  |..........6....p|
00000030  cd a8 ca 08 81 79 68 af  9b 08 25 32 90 f8 54 cb  |.....yh...%2..T.|
00000040  f0 60 9e 0d 54 cc 42 19  d6 27 e3 42 43 b4 f7 43  |.`..T.B..'.BC..C|
00000050  43 63 1c 73 85 45 8d 81  59 29 71 da 1e da 16 3a  |Cc.s.E..Y)q....:|
00000060  c4 d0 fb 92 a5 8f 6a d8  89 bf f5 76 ba 90 04 8d  |......j....v....|
00000070  80 ad 52 e9 2d d0 0f 0f  49 63 4e 51 24 96 d0 e2  |..R.-...IcNQ$...|
00000080  8c 2d a9 18 e2 8c 1c e4  c3 39 50 22 87 fa 6f b9  |.-.......9P"..o.|
00000090  81 05 15 e8 c7 2b 6a b2  10 44 64 a4 3a 1f 45 22  |.....+j..Dd.:.E"|
000000a0  3f df 5d cd d0 ce e6 38  a0 c6 11 3d c3 ce ee c1  |?.]....8...=....|
000000b0  ae 70 b6 7e 51 c4 c4 95  ed 0f 9f 4b e6 3b 5f b5  |.p.~Q......K.;_.|
000000c0  46 2f 63 1e b5 90 11 01  0d 55 00 48 04 db 92 09  |F/c......U.H....|
000000d0  98 5a 8b e1 f0 76 27 59  63 be 57 47 74 da 37 08  |.Z...v'Yc.WGt.7.|
000000e0  83 48 0c 88 9a 40 8e 6b  c6 ff bf d5 a4 e3 2b 95  |.H...@.k......+.|
000000f0  6a 71 bc 3f 94 ed fe 37  8e d9 3e 75 91 4f bf d9  |jq.?...7..>u.O..|
00000100  cc 73 b3 b7 ec da d2 f8  99 04 dd db 2f c4 db bf  |.s........../...|
00000110  40 e2 65 48 c5 37 af de  aa 77 3e b2 30 30 64 63  |@.eH.7...w>.00dc|
00000120  16 02 00 00 00 00 01 b6  57 e0 23 fd bc 61 6b 3b  |........W.#..ak;|
00000130  ff ec 66 3f f7 4b ff ff  ff ff fc 5a bf ff f8 fc  |..f?.K.....Z....|
00000140  2c fa d9 af f7 5b bf f7  bf ff c7 e2 bf d6 c1 6b  |,....[.........k|
00000150  ff dd ff fd d7 5b 20 6f  18 ff 63 05 97 dd af fe  |.....[ o..c.....|
00000160  f7 fb 18 af f8 bc df 63  0b 5b ce b7 bf ff f7 5d  |.......c.[.....]|
00000170  d7 ba 8b 77 d8 c6 bc 7e  30 fc 57 b0 14 8c 87 e8  |...w...~0.W.....|
00000180  0d b5 8c 5b c1 ce ff fe  c6 7d 5c d1 8f 6b 17 b1  |...[.....}\..k..|
00000190  84 7f 5b 15 f6 1c 9b 8e  b0 70 6a 42 12 37 a7 04  |..[......pjB.7..|
000001a0  c6 f0 71 b1 47 d0 47 79  23 18 49 d6 72 5e 2f 1a  |..q.G.Gy#.I.r^/.|
000001b0  7f ff f6 30 19 e2 f1 70  5f 27 26 ad 82 7a 00 fe  |...0...p_'&..z..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 00 40 0b 00 fe  |............@...|
000001d0  ff ff 05 fe ff ff 99 05  40 0b 69 6a 18 02 00 00  |........@.ij....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
  No volume groups found

---

### Post by wilee-nilee on 2012-05-14
So as you have described grub is in the sda1 windows boot partition. Follow the links instructions and you should be set.
```
sda1: __________________________________________________  ________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 290147160 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD
```


[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by carl4926 on 2012-05-14
> **bheemamahesh said:**
> after fixing windows only windows will boot? and i ve to use ubuntu live disc and update grub?
I said use supergrubdisk to boot ubuntu

either that or the Ubuntu live cd
and chroot

>  * Open a terminal and type

$ sudo fdisk -l

    * Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt

$ sudo mount /dev/sda1 /mnt

    * Now mount the rest of your devices

$ sudo mount --bind /dev /mnt/dev

    * Now chroot into your system

$ sudo chroot /mnt

    *

      When that is done you need to run update-grub to create the configuration file.

$ update-grub

    *

      To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda

$ grub-install /dev/sda

---

### Post by wilee-nilee on 2012-05-14
> **carl4926 said:**
> I said use supergrubdisk to boot ubuntu

either that or the Ubuntu live cd
and chroot

If you look at the bootscript you will see that the sda1 partition has not been cleaned, the windows repair rarely works without straight up commands. And rarely with grub in the mbr.

OP stop where your at run the bootscript again and let me direct you.

---

### Post by bheemamahesh on 2012-05-14
> **wilee-nilee said:**
> So as you have described grub is in the sda1 windows boot partition. Follow the links instructions and you should be set.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If  the sixth  screen i did not have  a "BackupBS"  tab :(

now i inserted win7 dvd and selected repair-->command prompt

Bootrec.exe/FixBoot
Bootrec.exe/FixMbr
exit

now as expected only windows is working

i started live session using backbox dvd
then Terminal-->sudo update-grub
and i got this error
"**/usr/sbin/grub-probe: error: cannot stat `aufs'.**"

---

### Post by wilee-nilee on 2012-05-14
> **bheemamahesh said:**
> If  the sixth  screen i did not have  a "BackupBS"  tab :(

now i inserted win7 dvd and selected repair-->command prompt

Bootrec.exe/FixBoot
Bootrec.exe/FixMbr
exit

now as expected only windows is working

i started live session using backbox dvd
then Terminal-->sudo update-grub
and i got this error
"**/usr/sbin/grub-probe: error: cannot stat `aufs'.**"

Boot the windows disc again and run this full command set, it should rebuild the sda1 partition then run the script again so we can be sure that grub is gone from the sda1. We want to do this systematically.

```

[FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /fixmbr 
[/SIZE][/FONT][FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /FixBoot (#updates PBR partition boot) [/SIZE][/FONT] 
[FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /ScanOs [/SIZE][/FONT] 
[FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /RebuildBcd [/SIZE][/FONT] 
 
```

---

### Post by bheemamahesh on 2012-05-14
> **carl4926 said:**
> I said use supergrubdisk to boot ubuntu

either that or the Ubuntu live cd
and chroot

* Now, you need to remember which device listed is your linux  distribution, for reference, /dev/sda1 will be used. Now we need to  mount the filesystem to /mnt

$ sudo mount /dev/sda1 /mnt

as i dont ve supergrubdisk im using live cd

 after sudo update-grub i ve to use this sudo mount /dev/sda1 /mnt?
"**sda1**"?

---

### Post by bheemamahesh on 2012-05-14
> **wilee-nilee said:**
> Boot the windows disc again and run this full command set, it should rebuild the sda1 partition then run the script again so we can be sure that grub is gone from the sda1. We want to do this systematically.

```

[FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /fixmbr 
[/SIZE][/FONT][FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /FixBoot (#updates PBR partition boot) [/SIZE][/FONT] 
[FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /ScanOs [/SIZE][/FONT] 
[FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /RebuildBcd [/SIZE][/FONT] 
 
```
ok..i'll do and post the results

---

### Post by bheemamahesh on 2012-05-14
> **wilee-nilee said:**
> Boot the windows disc again and run this full command set, it should rebuild the sda1 partition then run the script again so we can be sure that grub is gone from the sda1. We want to do this systematically.

```

[FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /fixmbr 
[/SIZE][/FONT][FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /FixBoot (#updates PBR partition boot) [/SIZE][/FONT] 
[FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /ScanOs [/SIZE][/FONT] 
[FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /RebuildBcd [/SIZE][/FONT] 
 
```
[FONT=Verdana, sans-serif][SIZE=1][/SIZE][/FONT]results for fixmbr & fixboot
[FONT=Verdana, sans-serif][SIZE=1]Operation Completed Successfully

for scanos & rebuildbcd
successfully scanned windows installtions
total identified windows installations :0
[/SIZE][/FONT][FONT=Verdana, sans-serif][SIZE=1]Operation Completed Successfully[/SIZE][/FONT]

---

### Post by bheemamahesh on 2012-05-14
im running script now

---

### Post by wilee-nilee on 2012-05-14
> **bheemamahesh said:**
> im running script now

Cool, download supergrub as well that is a excellent tool.

[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

---

### Post by bheemamahesh on 2012-05-14
Results.txt

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  BackBox Linux 2.05
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848    84,084,735    83,877,888   7 NTFS / exFAT / HPFS
/dev/sda3          84,086,782   312,580,095   228,493,314   f W95 Extended (LBA)
/dev/sda5          84,086,784   272,830,463   188,743,680   7 NTFS / exFAT / HPFS
/dev/sda6         272,832,512   307,986,431    35,153,920  83 Linux
/dev/sda7         307,988,480   312,580,095     4,591,616  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3826768526764442                       ntfs       System Reserved
/dev/sda2        56BC22B1BC228C15                       ntfs       
/dev/sda5        54A4FA18A4F9FC74                       ntfs       New Volume
/dev/sda6        8bcf173b-032c-451e-85c4-5e9d8d5670ab   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/8bcf173b-032c-451e-85c4-5e9d8d5670ab ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
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
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
    linux    /boot/vmlinuz-2.6.38-15-generic root=UUID=8bcf173b-032c-451e-85c4-5e9d8d5670ab ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-15-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-15-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
    echo    'Loading Linux 2.6.38-15-generic ...'
    linux    /boot/vmlinuz-2.6.38-15-generic root=UUID=8bcf173b-032c-451e-85c4-5e9d8d5670ab ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
    linux    /boot/vmlinuz-2.6.38-14-generic root=UUID=8bcf173b-032c-451e-85c4-5e9d8d5670ab ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
    echo    'Loading Linux 2.6.38-14-generic ...'
    linux    /boot/vmlinuz-2.6.38-14-generic root=UUID=8bcf173b-032c-451e-85c4-5e9d8d5670ab ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-14-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 8bcf173b-032c-451e-85c4-5e9d8d5670ab
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3826768526764442
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=8bcf173b-032c-451e-85c4-5e9d8d5670ab /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
#UUID=bfc3b6a3-eab2-4934-a88e-9c21a9b0dad7 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 138.352973938 = 148.555374592  boot/grub/core.img                             1
 132.542179108 = 142.316081152  boot/grub/grub.cfg                             1
 131.760742188 = 141.477019648  boot/initrd.img-2.6.38-14-generic              2
 131.885742188 = 141.611237376  boot/initrd.img-2.6.38-15-generic              2
 131.272769928 = 140.953063424  boot/vmlinuz-2.6.38-14-generic                 1
 131.288394928 = 140.969840640  boot/vmlinuz-2.6.38-15-generic                 1
 131.885742188 = 141.611237376  initrd.img                                     2
 131.760742188 = 141.477019648  initrd.img.old                                 2
 131.288394928 = 140.969840640  vmlinuz                                        1
 131.272769928 = 140.953063424  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  93 d7 76 41 a8 40 f0 b5  6e de f9 61 0d aa 0d 13  |..vA.@..n..a....|
00000010  6b 92 48 44 2a 24 61 bf  fc 3b 0b 23 2a 1a 1c a6  |k.HD*$a..;.#*...|
00000020  89 1b 14 c2 d8 b1 c1 05  0e 0d 36 1d 84 89 0e 70  |..........6....p|
00000030  cd a8 ca 08 81 79 68 af  9b 08 25 32 90 f8 54 cb  |.....yh...%2..T.|
00000040  f0 60 9e 0d 54 cc 42 19  d6 27 e3 42 43 b4 f7 43  |.`..T.B..'.BC..C|
00000050  43 63 1c 73 85 45 8d 81  59 29 71 da 1e da 16 3a  |Cc.s.E..Y)q....:|
00000060  c4 d0 fb 92 a5 8f 6a d8  89 bf f5 76 ba 90 04 8d  |......j....v....|
00000070  80 ad 52 e9 2d d0 0f 0f  49 63 4e 51 24 96 d0 e2  |..R.-...IcNQ$...|
00000080  8c 2d a9 18 e2 8c 1c e4  c3 39 50 22 87 fa 6f b9  |.-.......9P"..o.|
00000090  81 05 15 e8 c7 2b 6a b2  10 44 64 a4 3a 1f 45 22  |.....+j..Dd.:.E"|
000000a0  3f df 5d cd d0 ce e6 38  a0 c6 11 3d c3 ce ee c1  |?.]....8...=....|
000000b0  ae 70 b6 7e 51 c4 c4 95  ed 0f 9f 4b e6 3b 5f b5  |.p.~Q......K.;_.|
000000c0  46 2f 63 1e b5 90 11 01  0d 55 00 48 04 db 92 09  |F/c......U.H....|
000000d0  98 5a 8b e1 f0 76 27 59  63 be 57 47 74 da 37 08  |.Z...v'Yc.WGt.7.|
000000e0  83 48 0c 88 9a 40 8e 6b  c6 ff bf d5 a4 e3 2b 95  |.H...@.k......+.|
000000f0  6a 71 bc 3f 94 ed fe 37  8e d9 3e 75 91 4f bf d9  |jq.?...7..>u.O..|
00000100  cc 73 b3 b7 ec da d2 f8  99 04 dd db 2f c4 db bf  |.s........../...|
00000110  40 e2 65 48 c5 37 af de  aa 77 3e b2 30 30 64 63  |@.eH.7...w>.00dc|
00000120  16 02 00 00 00 00 01 b6  57 e0 23 fd bc 61 6b 3b  |........W.#..ak;|
00000130  ff ec 66 3f f7 4b ff ff  ff ff fc 5a bf ff f8 fc  |..f?.K.....Z....|
00000140  2c fa d9 af f7 5b bf f7  bf ff c7 e2 bf d6 c1 6b  |,....[.........k|
00000150  ff dd ff fd d7 5b 20 6f  18 ff 63 05 97 dd af fe  |.....[ o..c.....|
00000160  f7 fb 18 af f8 bc df 63  0b 5b ce b7 bf ff f7 5d  |.......c.[.....]|
00000170  d7 ba 8b 77 d8 c6 bc 7e  30 fc 57 b0 14 8c 87 e8  |...w...~0.W.....|
00000180  0d b5 8c 5b c1 ce ff fe  c6 7d 5c d1 8f 6b 17 b1  |...[.....}\..k..|
00000190  84 7f 5b 15 f6 1c 9b 8e  b0 70 6a 42 12 37 a7 04  |..[......pjB.7..|
000001a0  c6 f0 71 b1 47 d0 47 79  23 18 49 d6 72 5e 2f 1a  |..q.G.Gy#.I.r^/.|
000001b0  7f ff f6 30 19 e2 f1 70  5f 27 26 ad 82 7a 00 fe  |...0...p_'&..z..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 00 00 40 0b 00 fe  |............@...|
000001d0  ff ff 05 fe ff ff 99 05  40 0b 69 6a 18 02 00 00  |........@.ij....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

  No volume groups found

---

### Post by wilee-nilee on 2012-05-14
Looks good, so we have the option of chrooting from a live ubuntu cd, or using super grub. Supergrub is for booting in and fixing the mbr from the live installed ubuntu desktop, of the two options the easiest. I have a feeling you may not have a ubuntu cd as well, so down load supergrub, and burn it to a cd or load a usb thumb with it, you can use unetbootin for this. Boot it to the screen I post here and choose the option highlighted in blue.

[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

[ATTACH]217908[/ATTACH]

Once your in the installed Ubuntu run these commands

```
sudo grub-install /dev/sda
```Then

```
sudo update-grub
```Windows should show in the terminal and be bootable.

If you only have a ubuntu cd we can chroot in and fix this just let me know if that is what you need.

---

### Post by bheemamahesh on 2012-05-14
> **wilee-nilee said:**
> Looks good, so we have the option of chrooting from a live ubuntu cd, or using super grub. Supergrub is for booting in and fixing the mbr from the live installed ubuntu desktop, of the two options the easiest. I have a feeling you may not have a ubuntu cd as well, so down load supergrub, and burn it to a cd or load a usb thumb with it, you can use unetbootin for this. Boot it to the screen I post here and choose the option highlighted in blue.

[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

[ATTACH]217908[/ATTACH]

Once your in the installed Ubuntu run these commands

```
sudo grub-install /dev/sda
```Then

```
sudo update-grub
```Windows should show in the terminal and be bootable.

If you only have a ubuntu cd we can chroot in and fix this just let me know if that is what you need.
i ve downloaded both supergrubdisk and unetbootin..
and i dont ve either usb or cd what to do now ?

---

### Post by wilee-nilee on 2012-05-14
> **bheemamahesh said:**
> i ve downloaded both supergrubdisk and unetbootin..
and i dont ve either usb or cd what to do now ?

Do you have a ubuntu cd?

---

### Post by bheemamahesh on 2012-05-14
yes

---

### Post by wilee-nilee on 2012-05-14
Cool, boot the cd open a terminal and run all these commands.

```
sudo mount /dev/sda6 /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
``````
grub-install /dev/sda
``````
grub-install --recheck /dev/sda
``````
update-grub
``````
Exit chroot: CTRL-D on keyboard
``````
sudo reboot
```

---

### Post by bheemamahesh on 2012-05-14
> **wilee-nilee said:**
> Cool, boot the cd open a terminal and run all these commands.

```
sudo mount /dev/sda6 /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
``````
grub-install /dev/sda
``````
grub-install --recheck /dev/sda
``````
update-grub
``````
Exit chroot: CTRL-D on keyboard
``````
sudo reboot
```
worked perfectly :)
thnX for ur Support :D

can u explain"sudo mount /dev/sda6 /mnt" why we used sda6 here

---

### Post by bheemamahesh on 2012-05-14
Than'Q' for ur help wilee-nilee & carl4926

---

### Post by wilee-nilee on 2012-05-14
> **bheemamahesh said:**
> Than'Q' for ur help wilee-nilee & carl4926

No problem the sudo mount /dev/sda6 /mnt mounts the partition that the ubuntu is in it is part of the chroot process, once you saw the terminal change from $ to # you were in the root of the Ubuntu install. Your basically running the install then from the live cd.

Here is a link on the chroot if your interested.

[https://help.ubuntu.com/community/Grub2/Installing#ChRoot](https://help.ubuntu.com/community/Grub2/Installing#ChRoot)

@carl4926, you were on the right track. :)

---

### Post by carl4926 on 2012-05-14
> **wilee-nilee said:**
> 

@carl4926, you were on the right track. :)
Sometimes I am :D

---

### Post by bheemamahesh on 2012-05-14
i learned something today happie :D

---

