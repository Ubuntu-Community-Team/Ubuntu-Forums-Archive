---
title: "Boot problem Grub"
date: 2011-07-25
forum: General Help
---

### Post by Fiddler 2 on 2011-07-25
I'd be very grateful if someone could help me with a problem.

I installed Ubuntu on a friends computer as a dual boot setup, which worked OK. My friend asked me to change it so that the default OS would be WinXP.

When I went to change it in boot manager, Win XP was not given as an option, and when I rebooted, Ubuntu was the only option available.

How can I get back to Win XP given that on startup the option to boot to XP isn't offered?

Is there any way to boot up Win XP?

Thanks in advance.

---

### Post by westie457 on 2011-07-25
> **Fiddler 2 said:**
> I'd be very grateful if someone could help me with a problem.

I installed Ubuntu on a friends computer as a dual boot setup, which worked OK. My friend asked me to change it so that the default OS would be WinXP.

When I went to change it in boot manager, Win XP was not given as an option, and when I rebooted, Ubuntu was the only option available.

How can I get back to Win XP given that on startup the option to boot to XP isn't offered?

Is there any way to boot up Win XP?

Thanks in advance.

Hello and welcome to the forums.

Firstly, boot up the pc using a LiveCD/USB and select try.

When the dust has settled download and run bootinfoscript.
The download and instructions are here [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

They even explain how to post the results.

This will give us more information and ideas on how to proceed.

---

### Post by Quackers on 2011-07-25
Welcome to UF.
Which version of Ubuntu?
Try running ```
sudo update-grub
``` in the terminal and watch to see if the Windows Loader is recognised.

---

### Post by Fiddler 2 on 2011-07-30
Thanks very much, will try what you suggest.

---

### Post by Fiddler 2 on 2011-08-01
> **westie457 said:**
> Hello and welcome to the forums.

Firstly, boot up the pc using a LiveCD/USB and select try.

When the dust has settled download and run bootinfoscript.
The download and instructions are here [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

They even explain how to post the results.

This will give us more information and ideas on how to proceed.

Hi I did as you said and here are the results:

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for (,msdos7)/boot/grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,390   163,113,590   163,017,201   7 NTFS / exFAT / HPFS
/dev/sda3         163,115,006   302,759,935   139,644,930   5 Extended
/dev/sda5         209,733,632   298,858,495    89,124,864  83 Linux
/dev/sda6         298,860,544   302,759,935     3,899,392  82 Linux swap / Solaris
/dev/sda7         163,115,008   207,708,159    44,593,152  83 Linux
/dev/sda8         207,710,208   209,729,535     2,019,328  82 Linux swap / Solaris
/dev/sda4         302,760,990   312,496,379     9,735,390  db CP/M / CTOS / ...


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D7-0118                              vfat       DellUtility
/dev/sda2        8A90A54490A53799                       ntfs       
/dev/sda4                                               vfat       DellRestore
/dev/sda5        8e47ab43-0322-4388-ab99-ebf8df202a1f   ext4       
/dev/sda6        c911eb1b-8320-4a76-bf09-e4960592f21f   swap       
/dev/sda7        57e62373-5671-4344-8763-646f22fd5d5d   ext4       
/dev/sda8        ce02733c-1134-4cb7-b12c-65c7326b3a08   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=8e47ab43-0322-4388-ab99-ebf8df202a1f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c911eb1b-8320-4a76-bf09-e4960592f21f none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 102.387786865 = 109.938049024  boot/vmlinuz-2.6.35-22-generic                 1
 102.387786865 = 109.938049024  vmlinuz                                        1

=========================== sda7/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 57e62373-5671-4344-8763-646f22fd5d5d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 57e62373-5671-4344-8763-646f22fd5d5d
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
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 57e62373-5671-4344-8763-646f22fd5d5d
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=57e62373-5671-4344-8763-646f22fd5d5d ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 57e62373-5671-4344-8763-646f22fd5d5d
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=57e62373-5671-4344-8763-646f22fd5d5d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 57e62373-5671-4344-8763-646f22fd5d5d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 57e62373-5671-4344-8763-646f22fd5d5d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
# / was on /dev/sda7 during installation
UUID=57e62373-5671-4344-8763-646f22fd5d5d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=ce02733c-1134-4cb7-b12c-65c7326b3a08 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  96.179004669 = 103.271419904  boot/grub/core.img                             1
  90.834159851 = 97.532436480   boot/grub/grub.cfg                             1
  79.161567688 = 84.999086080   boot/initrd.img-2.6.35-22-generic              2
  78.792968750 = 84.603305984   boot/vmlinuz-2.6.35-22-generic                 2
  79.161567688 = 84.999086080   initrd.img                                     2
  78.792968750 = 84.603305984   vmlinuz                                        2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 4a 90 44 65 6c 6c 20  38 2e 30 00 02 04 01 00  |.J.Dell 8.0.....|
00000010  02 00 02 00 00 f8 5e 00  3f 00 ff 00 3f 00 00 00  |......^.?...?...|
00000020  47 78 01 00 80 00 29 18  01 d7 07 44 65 6c 6c 55  |Gx....)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  00 00 00 30 33 c0 8e d0  |...........03...|
00000050  bc 00 07 fc b9 80 00 8e  d8 be 00 7c b8 00 20 8e  |...........|.. .|
00000060  c0 33 ff f3 66 a5 ea 6b  00 00 20 8e d8 b8 01 02  |.3..f..k.. .....|
00000070  b9 01 00 b6 00 8a 16 24  00 bb 00 02 cd 13 0f 82  |.......$........|
00000080  e0 00 80 3e c2 03 06 74  0e c6 06 c2 03 06 b8 01  |...>...t........|
00000090  03 cd 13 0f 82 cb 00 66  0f b7 06 16 00 66 d1 e0  |.......f.....f..|
000000a0  66 40 66 03 06 1c 00 66  a3 3e 00 8b 2e 11 00 89  |f@f....f.>......|
000000b0  2e 44 00 c1 ed 04 e8 cb  00 4d 75 fa b9 0b 00 be  |.D.......Mu.....|
000000c0  ea 01 8b fd f3 a6 74 0f  83 c5 20 ff 0e 44 00 75  |......t... ..D.u|
000000d0  eb be e0 01 e9 8e 00 26  8b 46 1a a3 46 00 66 a1  |.......&.F..F.f.|
000000e0  1c 00 66 40 66 a3 3e 00  c7 06 48 00 00 00 8b 2e  |..f@f.>...H.....|
000000f0  16 00 e8 8f 00 4d 75 fa  c7 06 4a 00 70 00 c7 06  |.....Mu...J.p...|
00000100  48 00 00 00 66 0f b7 06  46 00 66 83 e8 02 66 0f  |H...f...F.f...f.|
00000110  b6 0e 0d 00 66 f7 e1 66  0f b7 0e 16 00 66 d1 e1  |....f..f.....f..|
00000120  66 41 66 03 0e 1c 00 66  03 c1 66 0f b7 0e 11 00  |fAf....f..f.....|
00000130  66 c1 e9 04 66 03 c1 66  a3 3e 00 0f b6 2e 0d 00  |f...f..f.>......|
00000140  e8 41 00 4d 75 fa 8b 36  46 00 b8 00 30 d1 e6 73  |.A.Mu..6F...0..s|
00000150  03 05 00 10 8e c0 26 ad  3d f8 ff 73 0d a3 46 00  |......&.=..s..F.|
00000160  eb a2 be d5 01 e8 0d 00  eb fe 8a 16 24 00 33 ed  |............$.3.|
00000170  ea 00 00 70 00 ac 3c 00  74 09 b4 0e bb 07 00 cd  |...p..<.t.......|
00000180  10 eb f2 c3 66 a1 3e 00  66 33 d2 66 0f b7 0e 18  |....f.>.f3.f....|
00000190  00 66 f7 f1 fe c2 88 16  25 00 32 d2 66 0f b7 0e  |.f......%.2.f...|
000001a0  1a 00 66 f7 f1 8a f2 8b  c8 b8 01 02 c0 e5 06 0a  |..f.............|
000001b0  2e 25 00 86 e9 8a 16 24  00 c4 1e 48 00 cd 13 72  |.%.....$...H...r|
000001c0  a1 66 ff 06 3e 00 81 06  48 00 00 02 75 06 81 06  |.f..>...H...u...|
000001d0  4a 00 00 10 c3 44 69 73  6b 20 65 72 72 6f 72 00  |J....Disk error.|
000001e0  4e 6f 20 6c 6f 61 64 65  72 00 44 45 4c 4c 42 49  |No loader.DELLBI|
000001f0  4f 20 42 49 4e 00 00 00  00 00 00 00 00 00 55 aa  |O BIN.........U.|
00000200

Unknown BootLoader on sda3

00000000  00 00 01 ba 44 80 2f 27  04 17 01 89 c3 f8 00 00  |....D./'........|
00000010  01 e0 07 ec 81 00 00 52  6d 25 46 c6 bd 0a 6d a4  |.......Rm%F...m.|
00000020  5a ad bd 97 40 0f b3 79  c9 52 19 16 da 74 1f 5b  |Z...@..y.R...t.[|
00000030  89 80 0f 3b 17 d5 7e 4f  2e b2 95 69 57 6d 1a de  |...;..~O...iWm..|
00000040  1a 91 aa d7 95 24 a9 65  fd d2 43 76 04 de df a9  |.....$.e..Cv....|
00000050  af a8 33 30 e2 83 23 69  e7 74 75 09 68 b1 00 a6  |..30..#i.tu.h...|
00000060  a2 7d e4 01 bf d2 9b 61  a6 a5 3e 35 e0 0e 80 19  |.}.....a..>5....|
00000070  80 39 00 61 8f cf 61 3a  e2 7c b3 65 5a 53 7c b0  |.9.a..a:.|.eZS|.|
00000080  01 9f f3 5c ec 7d 75 cc  b0 a8 85 d0 da df 4d b5  |...\.}u.......M.|
00000090  36 44 2c 36 37 0a 3b b7  26 e4 d8 de 81 bb d6 ae  |6D,67.;.&.......|
000000a0  6d ca 18 d4 8f 9f 7c 00  3b ce 6c 9e fe 7a 42 03  |m.....|.;.l..zB.|
000000b0  6d f8 b4 01 b0 03 d1 0f  ae e3 83 42 db f7 98 87  |m..........B....|
000000c0  0a e4 aa f3 34 ba 18 df  19 00 70 00 ce 3b b9 c3  |....4.....p..;..|
000000d0  fa c5 54 cd c3 db eb 3e  45 4b 81 ca 51 69 11 be  |..T....>EK..Qi..|
000000e0  17 ec 26 e7 30 db 91 4a  5d 56 a2 7f 3a 5f d3 84  |..&.0..J]V..:_..|
000000f0  ba 19 24 2d 52 0f a3 5b  9a e7 47 38 c6 eb 00 3e  |..$-R..[..G8...>|
00000100  e4 d7 40 d9 3d 5b 8b cc  b2 b7 ea 17 29 ab 4f b1  |..@.=[......).O.|
00000110  2b 7e 35 cd 31 32 13 21  70 2d b7 d4 80 18 80 3e  |+~5.12.!p-.....>|
00000120  f3 0f 8d e8 3e 3f 9e 58  ba df 25 17 b8 f8 8d ec  |....>?.X..%.....|
00000130  c0 1f be 0a 15 6c 29 bd  2e 7e 92 6d ee 9c 8a 8d  |.....l)..~.m....|
00000140  e2 70 26 d7 4c 6a 2f 78  58 87 09 ca e2 aa b7 ec  |.p&.Lj/xX.......|
00000150  40 03 10 40 02 f2 7e ee  e6 1e df 99 3e 84 5b bc  |@..@..~.....>.[.|
00000160  d5 ad e1 c5 eb b9 72 d9  1b a1 d3 05 cb 65 4b 1b  |......r......eK.|
00000170  3b f8 a5 c6 df db 30 06  60 05 dc 91 ad 5c ad f4  |;.....0.`....\..|
00000180  81 13 04 3d 2c 6f e4 80  02 d0 06 9d 7d f3 66 64  |...=,o......}.fd|
00000190  b5 bf a2 00 09 c0 11 76  46 ee d9 94 f6 9e bd cc  |.......vF.......|
000001a0  d3 37 c5 ba 3b 14 b0 dc  f0 6a 47 81 00 75 cc db  |.7..;....jG..u..|
000001b0  1b f9 f2 00 eb 4d 92 37  f4 64 01 a3 ac a5 00 fe  |.....M.7.d......|
000001c0  ff ff 83 fe ff ff 02 58  c7 02 00 f0 4f 05 00 fe  |.......X....O...|
000001d0  ff ff 05 fe ff ff 02 48  17 08 00 88 3b 00 00 00  |.......H....;...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

I'd be very grateful for any advice about how to proceed.

All the best,

Colin

---

### Post by Fiddler 2 on 2011-08-01
> **Quackers said:**
> Welcome to UF.
Which version of Ubuntu?
Try running ```
sudo update-grub
``` in the terminal and watch to see if the Windows Loader is recognised.

Did as you suggested and this is what I got:

atalie@natalie-Dell-DM061:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
natalie@natalie-Dell-DM061:~$ 


Thanks for your help.

All the best,

Colin

---

### Post by oldfred on 2011-08-01
Did XP boot after the install originally?

The boot script looks normal and all the windows files seem to be in the correct places. Normally the os-prober then finds windows and adds it.

I might use a Windows XP disk, go into repair console and run chkdsk on the c: (sda2) partition.

Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)

XP CHKDSK command:
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by Fiddler 2 on 2011-08-02
After install of Ubuntu, it did work normally - I was offered the option of booting into Ubuntu or XP. The person who owns the computer wanted XP to be the default, so I installed Bootmanager via the Ubuntu software centre. After I rebooted, XP did not appear in the OS selection screen or in the Bootmanager config screen.

Thanks for your help.

Colin

---

