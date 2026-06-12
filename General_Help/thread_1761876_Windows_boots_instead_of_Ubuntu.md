---
title: "Windows boots instead of Ubuntu"
date: 2011-05-18
forum: General Help
---

### Post by JD9 on 2011-05-18
Running Ubuntu 11.04 along with Windows XP, using Ubuntu approx 90% of the time. Normally able to select Ubuntu at startup, but after installing Windows updates, Windows now starts with no option to select OS.  I can't find my Ubuntu! How can I restore the screen that allows me to select either Ubuntu or Windows?

---

### Post by idoitprone on 2011-05-18
Live cd and bootscript anyone [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) ?

welcome to forums

post the result.txt under code tages

---

### Post by Hedgehog1 on 2011-05-19
The windows updates have overwritten the grub bootloader.  It is an easy fix, BUT we need to see your system info to give you the right commands to fix it.

The above post is asking for that. So if you would:

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by JD9 on 2011-05-19
Ran the script and now have a RESULTS.txt file.  There is a lot of text there, am I supposed to paste the entire thing into a Quick Reply box?  Also, what are the ```
 & 
``` tags?  Sorry, just new to the terminology.  Thanks for the help so far.

---

### Post by JD9 on 2011-05-19
Thinking I should have posted in Absolute Beginner Talk, as I am new to Ubuntu (intermediate Windows user though) and the protocols of this forum.  What is it about the "#" sign to post on here?  Again, thanks for the help so far.  At least I have the RESULTS.txt file now, just not sure what to do next.

---

### Post by Quackers on 2011-05-19
CLick on New Reply (not quick reply) then copy the contents of the Results.txt file then click on the # symbol in the toolbar of the reply window. Two CODE tags will appear with the cursor in between them. Paste the contents of the results file in between those code tags.
Post the reply.

---

### Post by JD9 on 2011-05-19
I am pasting the RESULTS.txt file here: #  ```
                Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   123,808,951   123,808,889   7 NTFS / exFAT / HPFS
/dev/sda2         123,809,790   156,301,311    32,491,522   5 Extended
/dev/sda5         123,809,792   154,845,183    31,035,392  83 Linux
/dev/sda6         154,847,232   156,301,311     1,454,080  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mspblk0p1   8093-2097                              vfat       
/dev/sda1        C6F48F69F48F5B17                       ntfs       
/dev/sda5        e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf   ext4       
/dev/sda6        9b2b5aa9-4250-4712-a3f6-034e04db0db8   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root C6F48F69F48F5B17
    drivemap -s (hd0) ${root}
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
UUID=e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9b2b5aa9-4250-4712-a3f6-034e04db0db8 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  67.168422699 = 72.121544704   boot/grub/core.img                             1
  62.474555969 = 67.081543680   boot/grub/grub.cfg                             1
  59.924709320 = 64.343666688   boot/initrd.img-2.6.32-27-generic              2
  68.529033661 = 73.582489600   boot/initrd.img-2.6.35-28-generic              2
  63.094951630 = 67.747688448   boot/initrd.img-2.6.38-8-generic               2
  68.169326782 = 73.196257280   boot/vmlinuz-2.6.32-27-generic                 1
  67.225879669 = 72.183238656   boot/vmlinuz-2.6.35-28-generic                 1
  73.353820801 = 78.763065344   boot/vmlinuz-2.6.38-8-generic                  1
  63.094951630 = 67.747688448   initrd.img                                     2
  68.529033661 = 73.582489600   initrd.img.old                                 2
  73.353820801 = 78.763065344   vmlinuz                                        1
  67.225879669 = 72.183238656   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  e4 eb e5 94 1a 03 a4 fd  86 67 17 98 8d 53 c3 00  |.........g...S..|
00000010  a3 ed b9 5b 9b 9c 0e dd  50 ce 82 fe ff ac 7b 56  |...[....P.....{V|
00000020  10 c3 72 12 d9 22 3b 2c  3e 63 3f 56 4f 27 c6 46  |..r..";,>c?VO'.F|
00000030  11 7c 74 81 4d 96 84 a3  07 b4 40 6c 91 80 9d fa  |.|t.M.....@l....|
00000040  44 6b b2 52 52 8e b4 f1  37 30 04 c0 20 02 a0 31  |Dk.RR...70.. ..1|
00000050  59 45 f3 cd 56 60 f9 a7  74 1f c9 d1 83 1c ef 6b  |YE..V`..t......k|
00000060  c3 1b 84 e2 c3 9b c8 8e  51 4a 72 68 7a 30 1d 89  |........QJrhz0..|
00000070  34 30 86 05 0b c1 8b 4a  4f 6c b7 0f 69 88 64 32  |40.....JOl..i.d2|
00000080  69 33 23 f2 62 98 f7 5a  85 2e a1 a3 45 b8 88 03  |i3#.b..Z....E...|
00000090  1d 9d b2 87 bd d3 c0 c0  6e 24 f0 f4 62 25 30 66  |........n$..b%0f|
000000a0  c7 74 07 66 b4 86 00 5e  57 52 50 92 9c 73 72 05  |.t.f...^WRP..sr.|
000000b0  48 05 a1 89 5e 4b e1 64  16 8e a5 2f 09 d5 72 93  |H...^K.d.../..r.|
000000c0  96 c1 4d 74 a0 33 8e dc  78 4f 20 ca 03 6f 94 33  |..Mt.3..xO ..o.3|
000000d0  87 25 c8 93 93 0b c4 d4  e4 06 27 60 fd 52 1a 03  |.%........'`.R..|
000000e0  72 13 39 5b 8b f8 fc 1d  33 4c 80 96 5b ec 3f db  |r.9[....3L..[.?.|
000000f0  a0 0a 24 fc 4b c1 5f 91  ac e4 c2 69 34 98 c0 14  |..$.K._....i4...|
00000100  81 54 31 8c 07 6b 70 0e  d4 01 31 41 69 d3 00 5a  |.T1..kp...1Ai..Z|
00000110  9f c0 71 f0 bc 9d ea fb  f3 f2 83 a1 c6 7d f2 c2  |..q..........}..|
00000120  ef 02 00 1e 80 9d 1c 20  34 bf 80 7b 80 dd 8c a0  |....... 4..{....|
00000130  05 e0 3b 46 59 2b b0 fc  92 05 d9 c4 de 8e be 5e  |..;FY+.........^|
00000140  11 9e a4 06 e3 31 24 b1  e4 8a d2 42 2b 81 ec 14  |.....1$....B+...|
00000150  07 28 41 0c bc 07 fe 10  c4 1b e2 94 00 ac bf c2  |.(A.............|
00000160  50 80 b2 0e b3 06 00 37  02 85 92 76 c1 5e f4 b8  |P......7...v.^..|
00000170  87 f9 b8 3d 18 81 22 08  6b 38 ae c3 b3 5a 24 06  |...=..".k8...Z$.|
00000180  05 73 b3 08 f4 14 02 70  dc 6b 89 bf 2f 80 33 01  |.s.....p.k../.3.|
00000190  81 7d 9f 60 bd 56 80 d0  28 59 c5 e0 ef af 51 89  |.}.`.V..(Y....Q.|
000001a0  b8 02 44 77 17 26 ec bd  b8 5d 7c 04 d8 cf f1 3e  |..Dw.&...]|....>|
000001b0  cf 00 85 23 b7 0b d7 e5  c6 23 9c 98 12 87 00 fe  |...#.....#......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 90 d9 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 90  d9 01 00 38 16 00 00 00  |...........8....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


#
```

---

### Post by JD9 on 2011-05-19
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   123,808,951   123,808,889   7 NTFS / exFAT / HPFS
/dev/sda2         123,809,790   156,301,311    32,491,522   5 Extended
/dev/sda5         123,809,792   154,845,183    31,035,392  83 Linux
/dev/sda6         154,847,232   156,301,311     1,454,080  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mspblk0p1   8093-2097                              vfat       
/dev/sda1        C6F48F69F48F5B17                       ntfs       
/dev/sda5        e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf   ext4       
/dev/sda6        9b2b5aa9-4250-4712-a3f6-034e04db0db8   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root C6F48F69F48F5B17
    drivemap -s (hd0) ${root}
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
UUID=e4b8e8d6-40e5-4282-8790-c5ee2a19d6bf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=9b2b5aa9-4250-4712-a3f6-034e04db0db8 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  67.168422699 = 72.121544704   boot/grub/core.img                             1
  62.474555969 = 67.081543680   boot/grub/grub.cfg                             1
  59.924709320 = 64.343666688   boot/initrd.img-2.6.32-27-generic              2
  68.529033661 = 73.582489600   boot/initrd.img-2.6.35-28-generic              2
  63.094951630 = 67.747688448   boot/initrd.img-2.6.38-8-generic               2
  68.169326782 = 73.196257280   boot/vmlinuz-2.6.32-27-generic                 1
  67.225879669 = 72.183238656   boot/vmlinuz-2.6.35-28-generic                 1
  73.353820801 = 78.763065344   boot/vmlinuz-2.6.38-8-generic                  1
  63.094951630 = 67.747688448   initrd.img                                     2
  68.529033661 = 73.582489600   initrd.img.old                                 2
  73.353820801 = 78.763065344   vmlinuz                                        1
  67.225879669 = 72.183238656   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  e4 eb e5 94 1a 03 a4 fd  86 67 17 98 8d 53 c3 00  |.........g...S..|
00000010  a3 ed b9 5b 9b 9c 0e dd  50 ce 82 fe ff ac 7b 56  |...[....P.....{V|
00000020  10 c3 72 12 d9 22 3b 2c  3e 63 3f 56 4f 27 c6 46  |..r..";,>c?VO'.F|
00000030  11 7c 74 81 4d 96 84 a3  07 b4 40 6c 91 80 9d fa  |.|t.M.....@l....|
00000040  44 6b b2 52 52 8e b4 f1  37 30 04 c0 20 02 a0 31  |Dk.RR...70.. ..1|
00000050  59 45 f3 cd 56 60 f9 a7  74 1f c9 d1 83 1c ef 6b  |YE..V`..t......k|
00000060  c3 1b 84 e2 c3 9b c8 8e  51 4a 72 68 7a 30 1d 89  |........QJrhz0..|
00000070  34 30 86 05 0b c1 8b 4a  4f 6c b7 0f 69 88 64 32  |40.....JOl..i.d2|
00000080  69 33 23 f2 62 98 f7 5a  85 2e a1 a3 45 b8 88 03  |i3#.b..Z....E...|
00000090  1d 9d b2 87 bd d3 c0 c0  6e 24 f0 f4 62 25 30 66  |........n$..b%0f|
000000a0  c7 74 07 66 b4 86 00 5e  57 52 50 92 9c 73 72 05  |.t.f...^WRP..sr.|
000000b0  48 05 a1 89 5e 4b e1 64  16 8e a5 2f 09 d5 72 93  |H...^K.d.../..r.|
000000c0  96 c1 4d 74 a0 33 8e dc  78 4f 20 ca 03 6f 94 33  |..Mt.3..xO ..o.3|
000000d0  87 25 c8 93 93 0b c4 d4  e4 06 27 60 fd 52 1a 03  |.%........'`.R..|
000000e0  72 13 39 5b 8b f8 fc 1d  33 4c 80 96 5b ec 3f db  |r.9[....3L..[.?.|
000000f0  a0 0a 24 fc 4b c1 5f 91  ac e4 c2 69 34 98 c0 14  |..$.K._....i4...|
00000100  81 54 31 8c 07 6b 70 0e  d4 01 31 41 69 d3 00 5a  |.T1..kp...1Ai..Z|
00000110  9f c0 71 f0 bc 9d ea fb  f3 f2 83 a1 c6 7d f2 c2  |..q..........}..|
00000120  ef 02 00 1e 80 9d 1c 20  34 bf 80 7b 80 dd 8c a0  |....... 4..{....|
00000130  05 e0 3b 46 59 2b b0 fc  92 05 d9 c4 de 8e be 5e  |..;FY+.........^|
00000140  11 9e a4 06 e3 31 24 b1  e4 8a d2 42 2b 81 ec 14  |.....1$....B+...|
00000150  07 28 41 0c bc 07 fe 10  c4 1b e2 94 00 ac bf c2  |.(A.............|
00000160  50 80 b2 0e b3 06 00 37  02 85 92 76 c1 5e f4 b8  |P......7...v.^..|
00000170  87 f9 b8 3d 18 81 22 08  6b 38 ae c3 b3 5a 24 06  |...=..".k8...Z$.|
00000180  05 73 b3 08 f4 14 02 70  dc 6b 89 bf 2f 80 33 01  |.s.....p.k../.3.|
00000190  81 7d 9f 60 bd 56 80 d0  28 59 c5 e0 ef af 51 89  |.}.`.V..(Y....Q.|
000001a0  b8 02 44 77 17 26 ec bd  b8 5d 7c 04 d8 cf f1 3e  |..Dw.&...]|....>|
000001b0  cf 00 85 23 b7 0b d7 e5  c6 23 9c 98 12 87 00 fe  |...#.....#......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 90 d9 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 90  d9 01 00 38 16 00 00 00  |...........8....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by JD9 on 2011-05-19
Thanks, hope I did it right.  The cursor was flashing AFTER the two code tags, not between.

---

### Post by idoitprone on 2011-05-22
Oh i thought some else more capable than an idoit like me would answer.

jd9 you copied the results correctly. From the looks of it, windows did overide the mbr and you will have to reinstall grub

get a live cd 9.10 or later

[https://help.ubuntu.com/community/Grub2#SIMPLEST - Copy GRUB 2 Files from the LiveCD](https://help.ubuntu.com/community/Grub2#SIMPLEST - Copy GRUB 2 Files from the LiveCD)

```
sudo mount /dev/sda5 /mnt

```

```
sudo grub-install --root-directory=/mnt /dev/sda

```
restart your computer

follow the things in this guide

[https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands](https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands)

to sum things up 

do this

```
sudo update-grub
```

---

### Post by linuxinstalledfromhdd on 2011-05-22
you're capable enough.. :P

---

### Post by katykat on 2011-05-23
[http://www.bootproblems.com/super-grub2-disk/](http://www.bootproblems.com/super-grub2-disk/)

Can also help in these situations, especially if Win is the boot disk.....

---

### Post by katykat on 2011-05-23
[http://www.bootproblems.com/super-grub2-disk/](http://www.bootproblems.com/super-grub2-disk/)

Can also help in these situations, especially if Win is the boot disk.....

---

