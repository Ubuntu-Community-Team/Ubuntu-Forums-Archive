---
title: "xp, 7, and ubuntu.... triple boot problems"
date: 2011-01-20
forum: General Help
---

### Post by cinikal on 2011-01-20
p { margin-bottom: 0.08in; }  Hello all,
Heres one for ya! I had windows 7 and ubuntu 10.04 running in dual boot. Ran fine No Problems! I wanted to play some games that only ran in windows xp, so i installed windows xp. Wouldnt you know it...Grub2 got screwed. Fixed my grub problem and now i am back to windows 7 and ubuntu in grub but now i dont see Windows xp and never did. I did sudo update-grub and still nothing. Any ideas on what i should try so i can triple boot?
Thanks in advance

---

### Post by oldfred on 2011-01-20
Windows combines its boot into the first install with the boot flag. From grub you can only boot one windows as the second does not have its boot files.

To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by garvinrick4 on 2011-01-20
This will take about 2 minutes to do:
Download this to DESKTOP:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
Open a terminal and run this:
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```
Will put a text file on Desktop that says RESULTS, copy and paste
to this thread. When pasted highlight whole thing and hit # sign in
upper right of message box and will put in nice little box to read from.
It will give your drive essentials for booting purposes. We can then
tell you what to do.

---

### Post by cinikal on 2011-01-21
ok ..Im a little lost. but let me tell you what is going on here. i have 4 hard drives installed. on drive a i have windows 7 , on drive b i have ubuntu 10.04, on drive c i have windows xp. first i installed windows 7, then ubuntu. worked great, then i installed xp... fooked it all up and had only windows xp no grub. fixed my grub problem and then i had no xp.
1. Can i triple boot?
2. How do I tell grub2 to see xp

Im sorry if i am being redundant but i am a little lost (or alot lost)

---

### Post by oldfred on 2011-01-22
We really need the boot script results.txt to know what is where.

see    	garvinrick4's post.

---

### Post by cinikal on 2011-01-22
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub4Dos is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sda2         163,846,935   390,700,799   226,853,865   f W95 Ext d (LBA)
/dev/sda5         163,846,998   390,700,799   226,853,802   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    12,273,659    12,273,597   7 HPFS/NTFS
/dev/sdb2          12,273,660   312,576,704   300,303,045   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   195,314,547   195,312,500  83 Linux
/dev/sdc2         195,315,710   390,627,327   195,311,618   5 Extended
/dev/sdc5         195,315,712   390,627,327   195,311,616  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   312,560,639   312,560,577   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        325C5C895C5C4A2D                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        861C970C1C96F701                       ntfs       Media                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        DCBCF92FBCF904B4                       ntfs       Computers n' Things           
/dev/sdb2        2A561A71561A3E4F                       ntfs       Movies                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        9344f4a0-1ea8-4be7-985d-d516280647d5   ext2                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        3b7083d9-62d7-4ee4-ae40-09d7840ac317   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        2CA0B726A0B6F584                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc1        /                        ext2       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(3)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(3)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 9344f4a0-1ea8-4be7-985d-d516280647d5
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 9344f4a0-1ea8-4be7-985d-d516280647d5
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
insmod ext2
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 9344f4a0-1ea8-4be7-985d-d516280647d5
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=light-gray/black
  set color_highlight=white/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 9344f4a0-1ea8-4be7-985d-d516280647d5
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=9344f4a0-1ea8-4be7-985d-d516280647d5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 9344f4a0-1ea8-4be7-985d-d516280647d5
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=9344f4a0-1ea8-4be7-985d-d516280647d5 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 9344f4a0-1ea8-4be7-985d-d516280647d5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 9344f4a0-1ea8-4be7-985d-d516280647d5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 325c5c895c5c4a2d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc1       /               ext2    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=3b7083d9-62d7-4ee4-ae40-09d7840ac317 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


  65.6GB: boot/grub/grub.cfg
  65.3GB: boot/initrd.img-2.6.32-27-generic
  65.4GB: boot/vmlinuz-2.6.32-27-generic
  65.3GB: initrd.img
  65.3GB: initrd.img.old
  65.4GB: vmlinuz
  65.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  44 24 08 50 ff 74 24 08  b9 40 b2 c8 69 e8 99 30  |D$.P.t$..@..i..0|
00000010  00 00 c3 56 8b f1 57 8d  7e 04 83 3f 00 74 2b 83  |...V..W.~..?.t+.|
00000020  7e 0c 00 74 0b 57 ff 15  08 80 c8 69 83 66 0c 00  |~..t.W.....i.f..|
00000030  8b 46 28 85 c0 74 06 8b  08 50 ff 51 08 83 c6 10  |.F(..t...P.Q....|
00000040  56 ff 15 64 80 c8 69 83  27 00 5f 5e c3 8b 41 08  |V..d..i.'._^..A.|
00000050  c3 e9 bd ff ff ff e9 f6  ff ff ff 33 c0 c3 56 8b  |...........3..V.|
00000060  74 24 10 85 f6 74 0b 57  bf 14 b2 c8 69 a5 a5 a5  |t$...t.W....i...|
00000070  a5 5f 8b 44 24 08 83 f8  ff 74 1b 85 c0 89 41 2c  |._.D$....t....A,|
00000080  74 14 83 38 00 8b f0 74  0d 6a 01 ff 56 20 83 c6  |t..8...t.j..V ..|
00000090  24 83 3e 00 75 f3 8b 35  48 b3 c8 69 eb 0e 8b 06  |$.>.u..5H..i....|
000000a0  85 c0 74 05 6a 01 ff 50  20 83 c6 04 3b 35 4c b3  |..t.j..P ...;5L.|
000000b0  c8 69 72 ea 33 c0 5e c2  0c 00 53 56 8b d9 8b 73  |.ir.3.^...SV...s|
000000c0  2c 57 33 ff 3b f7 74 1d  eb 17 8b 46 10 3b c7 74  |,W3.;.t....F.;.t|
000000d0  06 8b 08 50 ff 51 08 57  89 7e 10 ff 56 20 83 c6  |...P.Q.W.~..V ..|
000000e0  24 39 3e 75 e5 8b 35 48  b3 c8 69 eb 0d 8b 06 3b  |$9>u..5H..i....;|
000000f0  c7 74 04 57 ff 50 20 83  c6 04 3b 35 4c b3 c8 69  |.t.W.P ...;5L..i|
00000100  72 eb 5f 5e 8b cb 5b e9  07 ff ff ff c2 04 00 56  |r._^..[........V|
00000110  8b f1 e8 5d fd ff ff c7  06 58 89 c8 69 c7 46 04  |...].....X..i.F.|
00000120  44 89 c8 69 8b 0d 00 b2  c8 69 8b 01 ff 50 04 8b  |D..i.....i...P..|
00000130  c6 5e c2 04 00 8b 44 24  08 85 c0 75 07 b8 03 40  |.^....D$...u...@|
00000140  00 80 eb 08 c7 00 01 00  00 00 33 c0 c2 08 00 8b  |..........3.....|
00000150  44 24 04 ff 40 0c 8b 40  0c c2 04 00 8b 4c 24 04  |D$..@..@.....L$.|
00000160  ff 49 0c 56 8b 71 0c 75  0b 85 c9 74 07 8b 01 6a  |.I.V.q.u...t...j|
00000170  01 ff 50 54 8b c6 5e c2  04 00 56 8b f1 e8 14 00  |..PT..^...V.....|
00000180  00 00 f6 44 24 08 01 74  07 56 e8 e9 28 00 00 59  |...D$..t.V..(..Y|
00000190  8b c6 5e c2 04 00 56 8b  f1 c7 06 58 89 c8 69 c7  |..^...V....X..i.|
000001a0  46 04 44 89 c8 69 c7 46  0c 01 00 00 c0 8b 0d 00  |F.D..i.F........|
000001b0  b2 c8 69 8b 01 ff 50 08  8b ce 5e e9 f3 db 00 fe  |..i...P...^.....|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 aa 83 85 0d 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sde sdf sdg sdh

---

### Post by oldfred on 2011-01-22
Are you able to boot. I do not see boot/grub/core.img??

You boot files for both win7 & XP are in sda1. And the boot.ini in sda1 says it is booting from drive 3 which is sdd?
default=multi(0)disk(0)rdisk(3)partition(1)\WINDOW  S 


Have you tried booting from both the 200GB drive and the 320GB drive in BIOS?

You only get one windows boot entry since all the boot files are in sda1, but windows then should give you a choice on which to boot.

You may be able to repair the XP partition and then make it directly bootable from grub.

---

### Post by cinikal on 2011-01-23
yes i am able to boot to either windows 7 or ubuntu but my windows xp is not on my grub list. i would like to be able to boot from either 3 in grub. is this possible?

---

### Post by oldfred on 2011-01-23
You need to repair your XP install. You should be able to just copy the XP boot files from sda1 back to your XP install partition. Not sure if that will mess with your win7 install, but if you do not delete, but just copy it should be ok.

These 3 files are the XP files. 
/boot.ini /ntldr /NTDETECT.COM

Your boot.ini already says drive 3, so that may be all that is required.
After copying files:
sudo update-grub

More info here (Edit - may be more about moving 7):
Split dual boot win7 & XP - Instructions meierfra. post #3
[http://ubuntuforums.org/showthread.php?t=1421737](http://ubuntuforums.org/showthread.php?t=1421737)

---

