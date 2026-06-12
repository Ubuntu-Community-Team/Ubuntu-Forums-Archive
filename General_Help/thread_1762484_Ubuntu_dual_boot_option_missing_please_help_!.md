---
title: "Ubuntu dual boot option missing please help !"
date: 2011-05-19
forum: General Help
---

### Post by Hot_Sauce on 2011-05-19
Ok so I had windows XP and Ubuntu 10.04 dual boot set up. Unfortunately my windows XP got corrupted and I had to reinstall XP so when I reinstalled XP the dual boot option for Ubuntu is now missing ! On top of that my Windows XP got corrupted again and I lost the windows CD !

Right now im running Ubuntu straight from Ubuntu 10.04 CD. How do I bring back my installed Ubuntu/boot option ? 

I can assure that Ubuntu is installed on my system it's just that the option to boot it is not coming up !

---

### Post by ysangkok on 2011-05-19
The WinXP installation installs it's own boot loader. You can re-install GRUB, but it might break Windows if you are not careful.

The command "grub-install" is available in the terminal when running the LiveCD. Read the "man" page.

Tell me if you want to reinstall Grub or not.

---

### Post by Hot_Sauce on 2011-05-19
yes ! i would like to reinstall grub ! but how ? i dont care about the windows at this point
		 		 		 	 		 		 		 		 		 	               	 	 		 		 			[Register]("http://ubuntuforums.org/register.php") [Reset  Password]("http://ubuntuforums.org/login.php?do=lostpw") 		  		 		         [Forum  Help]("http://ubuntuforums.org/forumdisplay.php?f=331&order=desc&page=3&nojs=1#helpmenu")   [IMG]http://ubuntuforums.org/images/misc/menu_open.gif[/IMG] 	[Forum  Council]("http://ubuntuforums.org/forumdisplay.php?f=331&order=desc&page=3&nojs=1#fcmenu")   [IMG]http://ubuntuforums.org/images/misc/menu_open.gif[/IMG] 		 			 				 				[Today's  Posts]("http://ubuntuforums.org/search.php?do=getdaily") 				 				[Search]("http://ubuntuforums.org/search.php")

---

### Post by apollothethird on 2011-05-19
> **Hot_Sauce said:**
> Ok so I had windows XP and Ubuntu 10.04 dual boot set up. Unfortunately my windows XP got corrupted and I had to reinstall XP so when I reinstalled XP the dual boot option for Ubuntu is now missing ! On top of that my Windows XP got corrupted again and I lost the windows CD !

Right now im running Ubuntu straight from Ubuntu 10.04 CD. How do I bring back my installed Ubuntu/boot option ? 

I can assure that Ubuntu is installed on my system it's just that the option to boot it is not coming up !

Hi, Hot_Sauce.

Many people refer to running Ubuntu as a Windows application (wubi) as dual boot.  If this is the case, where you were running Wubi, when you removed Windows XP, you also removed Wubi (your Ubuntu OS, operating under Windows).

I real Dual Boot would have meant that Windows had it's drive or drive partition and Ubuntu had it's Drive or Drive partition.  You can remove drives or partitions without affecting other Drives or partitions.  If you remove the boot drive or the boot or the boot loader you can easily recover the OS' that are on their separate Drives or partitions just by installing another Boot loader.

An extremely simple way to recover your Ubuntu OS if it were on it's own drive or partition is to just simple reinstall Ubuntu when you finish the installation it's display all your Linux OS installations as selectable boot options.  If you don't see selectable boot options after a fresh install of Ubuntu, it will mean that you didn't have it there.

If you had Windows running when you installed Ubuntu, you installed it as a Windows Application, called Wubi.  When you removed Windows you removed Wubi.

If you installed Ubuntu by booting to the disk, then you installed Ubuntu on it's own drive or partition and you can recover it in many ways including the very simple way I just mentioned.

There are many other ways that are very simple also, but some of the terminology might appear confusing to a novice.  The recovery option is simple as just installing Grub (which happens when you install Ubuntu).

Look at "Recovering Ubuntu After Installing Windows":
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by oldfred on 2011-05-19
To see what is installed where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply, Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. It is also a .zip file that you have to extract to get the script.

---

### Post by Hot_Sauce on 2011-05-19
```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda5 starts at sector 20482938. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   According to the info in the boot sector, sda9 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda9 starts at sector 102414438. "63" and "2048" are 
                       quite common values for the starting sector of a 
                       logical partition and they only need to be fixed when 
                       you want to boot Windows from a logical partition.
    Operating System:  
    Boot files:        

sdb: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   According to the info in the boot sector, sdb has 0 
                       sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    20,482,874    20,482,812   c W95 FAT32 (LBA)
/dev/sda2          20,482,936   160,055,594   139,572,659   f W95 Extended (LBA)
/dev/sda5          20,482,938    61,448,624    40,965,687   b W95 FAT32
/dev/sda6          61,448,688    79,345,106    17,896,419   b W95 FAT32
/dev/sda7          79,345,664   101,339,135    21,993,472  83 Linux
/dev/sda8         101,341,184   102,414,335     1,073,152  82 Linux swap / Solaris
/dev/sda9         102,414,438   160,055,594    57,641,157   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/ramzswap0                                          swap       
/dev/sda1        58CE-F6AA                              vfat       
/dev/sda5        582C-EB2F                              vfat       
/dev/sda6        7440-A9B6                              vfat       MUSIC
/dev/sda7        dbb72443-66df-42b7-ac62-748cd66870bf   ext4       
/dev/sda8        f673f352-2ef5-4d37-b847-4b057e6b21df   swap       
/dev/sda9        C802-C695                              vfat       
/dev/sdb         6C98-3CA9                              vfat       PHONE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda7        /media/dbb72443-66df-42b7-ac62-748cd66870bf ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sda7/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set dbb72443-66df-42b7-ac62-748cd66870bf
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
set root='(hd0,8)'
search --no-floppy --fs-uuid --set dbb72443-66df-42b7-ac62-748cd66870bf
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
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set dbb72443-66df-42b7-ac62-748cd66870bf
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=dbb72443-66df-42b7-ac62-748cd66870bf ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set dbb72443-66df-42b7-ac62-748cd66870bf
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=dbb72443-66df-42b7-ac62-748cd66870bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set dbb72443-66df-42b7-ac62-748cd66870bf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,8)'
    search --no-floppy --fs-uuid --set dbb72443-66df-42b7-ac62-748cd66870bf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ee84538284534be9
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=dbb72443-66df-42b7-ac62-748cd66870bf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=f673f352-2ef5-4d37-b847-4b057e6b21df none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  42.171695709 = 45.281513472   boot/grub/core.img                             1
  42.171241760 = 45.281026048   boot/grub/grub.cfg                             1
  43.092380524 = 46.270091264   boot/initrd.img-2.6.32-21-generic              1
  42.994964600 = 46.165491712   boot/vmlinuz-2.6.32-21-generic                 1
  43.092380524 = 46.270091264   initrd.img                                     1
  42.994964600 = 46.165491712   vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  bf a5 c6 ac dd 1d 0e aa  f0 ce 04 d4 c1 56 69 82  |.............Vi.|
00000010  77 0a 4e 82 6c a2 4e a0  cd a3 8f f7 f3 90 78 fb  |w.N.l.N.......x.|
00000020  85 cf 2f 42 4a 5d d9 15  cf 31 91 ba bc 71 25 7f  |../BJ]...1...q%.|
00000030  f7 57 93 86 76 e2 46 54  e4 3c 10 18 fb ee e7 bb  |.W..v.FT.<......|
00000040  9c c6 5f ab af 84 eb 67  bd 47 d3 cb 4e ba f4 19  |.._....g.G..N...|
00000050  04 fd 3b cb 74 55 e0 1b  c8 94 62 4e 15 47 45 c4  |..;.tU....bN.GE.|
00000060  7d a1 8e c1 04 2a fb f9  33 27 02 dd 6f c8 90 a8  |}....*..3'..o...|
00000070  16 14 7e 28 5e 95 d3 4d  ee c3 bc 73 3a 31 4c 6f  |..~(^..M...s:1Lo|
00000080  9f 79 f4 5b 42 e8 c0 22  a8 ea 57 ca 15 34 b0 84  |.y.[B.."..W..4..|
00000090  a6 b4 94 75 2d 38 d9 42  d0 e0 58 5e 61 45 b3 13  |...u-8.B..X^aE..|
000000a0  7b 66 c8 51 60 56 f3 3a  95 a8 08 69 3a 96 0c 06  |{f.Q`V.:...i:...|
000000b0  2b f4 b6 8a d9 d7 a8 53  e6 04 6d e7 82 1a 31 08  |+......S..m...1.|
000000c0  88 7f 44 7c 57 0c 4d 99  71 78 4e 92 d6 85 5b 84  |..D|W.M.qxN...[.|
000000d0  1e ec 1a 40 59 09 f9 d6  a7 47 32 e6 96 49 80 a6  |...@Y....G2..I..|
000000e0  3e dd 9e b2 1e a2 84 97  b5 73 61 1e e0 9a 57 58  |>........sa...WX|
000000f0  f6 b6 f8 6e a5 68 84 25  8b c0 e1 34 94 6a 56 46  |...n.h.%...4.jVF|
00000100  16 98 10 cd ae af 51 8c  d8 b1 79 e3 50 6d b6 d9  |......Q...y.Pm..|
00000110  2c 68 8a eb b6 8a 02 97  0b 88 b0 a7 75 15 6d 3e  |,h..........u.m>|
00000120  88 c8 d0 a4 fe cb 6c d1  52 49 cd bb 1f 95 31 5f  |......l.RI....1_|
00000130  37 1b 07 91 83 07 29 85  9e b7 d8 19 30 e1 7b e8  |7.....).....0.{.|
00000140  0a 84 17 0f 06 90 8e bd  9c 54 97 7d 45 ab 81 43  |.........T.}E..C|
00000150  90 e6 a7 38 05 78 b2 45  bd 64 91 61 bd 67 39 9b  |...8.x.E.d.a.g9.|
00000160  17 e5 1d e6 bf 94 6d a8  2e ea 0e 01 b8 47 5c db  |......m......G\.|
00000170  ae e2 a2 b6 33 75 55 31  df a8 14 57 15 3f 60 af  |....3uU1...W.?`.|
00000180  24 02 1b 02 20 70 c2 ea  7f 22 6a 1f 73 01 7b 81  |$... p..."j.s.{.|
00000190  09 27 2f e5 06 96 ca 9f  7c 9b 97 d4 30 00 a6 7c  |.'/.....|...0..||
000001a0  ac f5 47 3a 22 bb 44 dc  07 16 e2 b0 6b 70 96 8c  |..G:".D.....kp..|
000001b0  1a cd 88 9b 75 72 c9 e9  0d 55 53 ae 04 43 00 01  |....ur...US..C..|
000001c0  c1 ff 0b fe ff ff 02 00  00 00 37 16 71 02 00 00  |..........7.q...|
000001d0  c1 ff 05 01 c9 ff 39 16  71 02 22 14 11 01 00 00  |......9.q.".....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by oldfred on 2011-05-19
Please go back and add code tags. When editing click on advanced and you get the full edit menu at the top. Hightlight the entire results.txt and then click on the # to automatically add code tags.

Your grub bootloader in the MBR tries to boot from sda5 but your install is in sda7.

---

### Post by Hot_Sauce on 2011-05-19
> **oldfred said:**
> Please go back and add code tags. When editing click on advanced and you get the full edit menu at the top. Hightlight the entire results.txt and then click on the # to automatically add code tags.

Your grub bootloader in the MBR tries to boot from sda5 but your install is in sda7.

Sorry about that. Fixed it now. So how do I get it to load from sda7 now ? I tried the tutorial in above posts but now when I boot my PC it loads the GRUB loader thing and accepts no commands whatsoever.

Please help !

---

### Post by oldfred on 2011-05-19
Did you follow an example that used sda5 and did not change it to sda7 where your install is? I changed this to sda7.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda7 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda7 if not correct:
sudo fdisk -l
#confirm that linux is sda7
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

---

### Post by Hot_Sauce on 2011-05-28
Thank you very much oldfred ! I appreciate it alot !

---

