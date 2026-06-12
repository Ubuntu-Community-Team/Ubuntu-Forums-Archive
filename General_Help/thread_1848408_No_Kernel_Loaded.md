---
title: "No Kernel Loaded"
date: 2011-09-22
forum: General Help
---

### Post by bcbrown on 2011-09-22
I have a Dell laptop with Windows XP and Ubuntu 11.04 OS installed. I did some security updates and scans on Windows XP last night and now when I try to boot up Ubuntu 11.04 I receive the following error message:

GNU Grub version 1.99~rc1-13ubuntu3

Minimal Bash-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible, device or file completions.

grub>

---

### Post by Rubi1200 on 2011-09-22
Please post the results of the boot info script so we can get a better overview of what is going on.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by JRV on 2011-09-22
Is this the problem?

[http://ubuntuforums.org/showthread.php?t=1670010](http://ubuntuforums.org/showthread.php?t=1670010)

---

### Post by bcbrown on 2011-09-22
Below is the information from the RESULTS.txt

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda2    *        160,650   200,730,127   200,569,478   7 NTFS / exFAT / HPFS
/dev/sda3         200,730,622   312,576,704   111,846,083   f W95 Extended (LBA)
/dev/sda5         307,339,578   312,576,704     5,237,127  dd Dell Media Direct
/dev/sda6         200,730,624   305,248,255   104,517,632  83 Linux
/dev/sda7         305,250,304   307,339,263     2,088,960  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        07D7-0B0F                              vfat       DellUtility
/dev/sda2        1E6CDB306CDB0207                       ntfs       
/dev/sda5        07D7-0B0F                              vfat       MEDIADIRECT
/dev/sda6        28f6c7a8-7cf4-4442-9507-f9928621ed23   ext4       
/dev/sda7        081af27c-ca58-453e-8219-222dc6d96665   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /media/1E6CDB306CDB0207  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"
--------------------------------------------------------------------------------

================================ sda5/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768--------------------------------------------------------------------------------

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
search --no-floppy --fs-uuid --set=root 28f6c7a8-7cf4-4442-9507-f9928621ed23
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 28f6c7a8-7cf4-4442-9507-f9928621ed23
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
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 28f6c7a8-7cf4-4442-9507-f9928621ed23
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=28f6c7a8-7cf4-4442-9507-f9928621ed23 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 28f6c7a8-7cf4-4442-9507-f9928621ed23
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=28f6c7a8-7cf4-4442-9507-f9928621ed23 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 28f6c7a8-7cf4-4442-9507-f9928621ed23
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 28f6c7a8-7cf4-4442-9507-f9928621ed23
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 1E6CDB306CDB0207
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 07d7-0b0f
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
UUID=28f6c7a8-7cf4-4442-9507-f9928621ed23 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=081af27c-ca58-453e-8219-222dc6d96665 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  97.914451599 = 105.134841856  boot/grub/core.img                             1
 109.888065338 = 117.991411712  boot/grub/grub.cfg                             1
 114.989257812 = 123.468775424  boot/initrd.img-2.6.38-8-generic               2
  97.848121643 = 105.063620608  boot/vmlinuz-2.6.38-8-generic                  1
 114.989257812 = 123.468775424  initrd.img                                     2
  97.848121643 = 105.063620608  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  e8 3a e3 ff ff a1 44 83  b4 6f 8b 4d 08 85 c9 74  |.:....D..o.M...t|
00000010  06 0f bf 79 3a eb 02 33  ff 3b c6 74 1b f6 40 1c  |...y:..3.;.t..@.|
00000020  01 74 15 80 78 19 05 72  0f 57 53 6a 64 ff 70 14  |.t..x..r.WSjd.p.|
00000030  ff 70 10 e8 35 e4 ff ff  8b c7 5f 5e 5b 5d c2 04  |.p..5....._^[]..|
00000040  00 cc cc cc cc cc 8b ff  55 8b ec 53 56 57 a1 44  |........U..SVW.D|
00000050  83 b4 6f 8b 7d 0c bb 44  83 b4 6f 3b c3 74 24 f6  |..o.}..D..o;.t$.|
00000060  40 1c 01 74 1e 80 78 19  05 72 18 57 68 20 5b b0  |@..t..x..r.Wh [.|
00000070  6f 6a 65 ff 70 14 ff 70  10 e8 ef e3 ff ff a1 44  |oje.p..p.......D|
00000080  83 b4 6f 8b 75 08 85 f6  74 20 83 ff 01 7c 1b 0f  |..o.u...t ...|..|
00000090  bf 4e 3a 3b f9 7f 13 e8  02 45 01 00 8b 46 40 8b  |.N:;.....E...F@.|
000000a0  74 b8 fc a1 44 83 b4 6f  eb 02 33 f6 3b c3 74 19  |t...D..o..3.;.t.|
000000b0  f6 40 1c 01 74 13 80 78  19 05 72 0d 6a 66 ff 70  |.@..t..x..r.jf.p|
000000c0  14 ff 70 10 e8 29 e5 ff  ff 5f 8b c6 5e 5b 5d c2  |..p..)..._..^[].|
000000d0  08 00 cc cc cc cc cc 8b  ff 55 8b ec 56 57 a1 44  |.........U..VW.D|
000000e0  83 b4 6f 8b 75 0c bf 44  83 b4 6f 3b c7 74 19 f6  |..o.u..D..o;.t..|
000000f0  40 1c 01 74 13 80 78 19  05 72 0d 6a 67 ff 70 14  |@..t..x..r.jg.p.|
00000100  ff 70 10 e8 ea e4 ff ff  8b 45 08 56 e8 da 44 01  |.p.......E.V..D.|
00000110  00 8b f0 a1 44 83 b4 6f  3b c7 74 1f f6 40 1c 01  |....D..o;.t..@..|
00000120  74 19 80 78 19 05 72 13  56 68 20 5b b0 6f 6a 68  |t..x..r.Vh [.ojh|
00000130  ff 70 14 ff 70 10 e8 32  e3 ff ff 5f 8b c6 5e 5d  |.p..p..2..._..^]|
00000140  c2 08 00 cc cc cc cc cc  8b ff 55 8b ec 83 e4 f8  |..........U.....|
00000150  51 53 56 57 a1 44 83 b4  6f 3d 44 83 b4 6f 74 1e  |QSVW.D..o=D..ot.|
00000160  f6 40 1c 01 74 18 80 78  19 05 72 12 68 20 5b b0  |.@..t..x..r.h [.|
00000170  6f 6a 69 ff 70 14 ff 70  10 e8 c1 e1 ff ff 8b 75  |oji.p..p.......u|
00000180  08 8b 06 8b 40 44 50 89  44 24 10 e8 88 2c 00 00  |....@DP.D$...,..|
00000190  33 c0 33 db 66 3b 46 3a  7d 24 33 ff 8b 46 3c 03  |3.3.f;F:}$3..F<.|
000001a0  c7 50 e8 94 0d 01 00 8b  46 3c 33 c9 41 66 89 4c  |.P......F<3.Af.L|
000001b0  38 1c 0f bf 46 3a 43 83  c7 28 3b d8 7c de 00 01  |8...F:C..(;.|...|
000001c0  c1 ff dd fe ff ff 3c b9  5a 06 87 e9 4f 00 00 fe  |......<.Z...O...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 d0 3a 06 00 00  |............:...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
```

---

