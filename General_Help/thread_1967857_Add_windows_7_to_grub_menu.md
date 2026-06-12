---
title: "Add windows 7 to grub menu?"
date: 2012-04-28
forum: General Help
---

### Post by zeating on 2012-04-28
I just installed 12.04 LTS over Windows 7 and it doesn't show up in my grub menu and I don't know how to get it there. 


                  > Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 30494 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000200658432 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953516911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2    *        206,848   248,218,566   248,011,719   7 NTFS / exFAT / HPFS
/dev/sda3       1,907,183,614 1,953,515,980    46,332,367   5 Extended
/dev/sda5       1,910,605,824 1,953,515,980    42,910,157  83 Linux
/dev/sda6       1,907,183,616 1,910,605,490     3,421,875  82 Linux swap / Solaris
/dev/sda4         248,219,648 1,907,182,538 1,658,962,891   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *            128     7,827,583     7,827,456   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        DE9EBA719EBA4237                       ntfs       Music
/dev/sda4        1492163E921624B0                       ntfs       
/dev/sda5        f974f581-e4e8-46f6-8e50-8a373c3d11eb   ext4       
/dev/sda6        c1a962eb-d9fb-42bb-8789-6a1b1e1a3bf5   swap       
/dev/sdb1        1B14-2C25                              vfat       PENDRIVE
/dev/sr0                                                iso9660    CD_ROM

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0         /media/CD_ROM            iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


=========================== sda5/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows 7
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root f974f581-e4e8-46f6-8e50-8a373c3d11eb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root f974f581-e4e8-46f6-8e50-8a373c3d11eb
  set locale_dir=($root)/boot/grub/locale
  set lang=en_CA
  insmod gettext
fi
terminal_output gfxterm
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
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f974f581-e4e8-46f6-8e50-8a373c3d11eb
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=f974f581-e4e8-46f6-8e50-8a373c3d11eb ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f974f581-e4e8-46f6-8e50-8a373c3d11eb
    echo    'Loading Linux 3.2.0-24-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=f974f581-e4e8-46f6-8e50-8a373c3d11eb ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f974f581-e4e8-46f6-8e50-8a373c3d11eb
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=f974f581-e4e8-46f6-8e50-8a373c3d11eb ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f974f581-e4e8-46f6-8e50-8a373c3d11eb
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=f974f581-e4e8-46f6-8e50-8a373c3d11eb ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry &#8220;Windows 7&#8243; {
set root=(/dev/sda4): root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/11_Windows.save ###
menuentry &#8220;Windows 7&#8243; {
set root= root=(hd0,1)
chainloader +1
}
### END /etc/grub.d/11_Windows.save ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f974f581-e4e8-46f6-8e50-8a373c3d11eb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root f974f581-e4e8-46f6-8e50-8a373c3d11eb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f974f581-e4e8-46f6-8e50-8a373c3d11eb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=c1a962eb-d9fb-42bb-8789-6a1b1e1a3bf5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/grub/menu.lst                             1
               =                boot/initrd.img-3.2.0-23-generic-pae           2
               =                boot/initrd.img-3.2.0-24-generic-pae           2
               =                boot/vmlinuz-3.2.0-23-generic-pae              1
               =                boot/vmlinuz-3.2.0-24-generic-pae              2
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  ad aa b5 6a 22 91 ff 57  6c ff fb 22 6d 23 ae b6  |...j"..Wl.."m#..|
00000010  c4 ff 5f b5 24 64 66 46  8d d5 96 64 22 f2 5f 55  |.._.$dfF...d"._U|
00000020  4c f9 be 48 7e 44 5c b5  e4 bf 56 db 73 cd cc 78  |L..H~D\...V.s..x|
00000030  aa b6 b5 ec 11 f1 e7 aa  b6 1f 11 11 65 27 89 aa  |............e'..|
00000040  22 fe ff aa ff 47 33 33  ff db 92 b6 ab 4a b2 54  |"....G33.....J.T|
00000050  46 66 b5 6d 20 08 4c b2  20 92 5f 85 df e7 fb 00  |Ff.m .L. ._.....|
00000060  e4 57 fd 9f cb 56 13 5f  6d 6b ab 6a 42 08 4c b6  |.W...V._mk.jB.L.|
00000070  46 00 91 db ab ad 5a c9  f7 6b 13 d5 99 ec f3 c5  |F.....Z..k......|
00000080  22 fe 6b 99 e2 fb be 2f  ff e4 03 22 5f c9 ac 57  |".k..../..."_..W|
00000090  df 17 c9 93 f2 5f 6d 1f  6d 4b 9f 2f 27 f1 44 12  |....._m.mK./'.D.|
000000a0  49 96 6d ff 99 64 af 2d  41 17 98 6d ff f7 ff 6d  |I.m..d.-A..m...m|
000000b0  c9 b2 49 f2 fe ff bf 25  c9 ff 3f 79 c9 27 92 3f  |..I....%..?y.'.?|
000000c0  c1 6c cb 82 21 84 10 04  b0 10 42 08 92 d9 96 59  |.l..!.....B....Y|
000000d0  b6 2c 84 60 cc cc 24 c9  c1 24 c9 cc 84 10 42 08  |.,.`..$..$....B.|
000000e0  e9 6a 0b 21 4c b2 2d 33  10 42 08 16 08 74 81 85  |.j.!L.-3.B...t..|
000000f0  85 20 84 20 17 af 96 25  1f f0 7d c0 ac aa 7f 7c  |. . ...%..}....||
00000100  99 64 d5 92 56 cb cc 24  b9 2d 48 b6 92 24 5f fc  |.d..V..$.-H..$_.|
00000110  db b6 25 7d ba 20 98 24  ef f2 f2 74 e0 bb 05 79  |..%}. .$...t...y|
00000120  b6 4d f2 3f ff d1 d6 d7  a0 cb d3 05 10 e8 02 5d  |.M.?...........]|
00000130  5b 66 92 a4 05 59 f5 5e  1c 5e ee bb f7 45 24 80  |[f...Y.^.^...E$.|
00000140  7f f2 ff cf 8f e4 d6 ff  cf bd fe bf 60 66 d6 ab  |............`f..|
00000150  44 44 6c 85 91 c4 07 44  be 1c 00 7c 00 20 f2 27  |DDl....D...|. .'|
00000160  40 2e 97 fb 00 1f 00 00  e6 47 04 00 ae ca 4c 66  |@........G....Lf|
00000170  ff 49 f2 24 e2 8b b8 fa  e6 47 44 22 7d 5f c4 6d  |.I.$.....GD"}_.m|
00000180  44 04 90 cb 13 f1 01 40  f5 c9 f5 ff 6f d5 56 55  |D......@....o.VU|
00000190  99 8d 5c 25 c9 d5 e6 97  f5 bf fe bf 33 33 c9 f6  |..\%........33..|
000001a0  99 49 55 6d 93 24 93 99  c1 64 3b 04 25 d9 56 08  |.IUm.$...d;.%.V.|
000001b0  92 6c 55 b5 24 33 b3 ca  b2 6d db 92 4c 92 00 fe  |.lU.$3...m..L...|
000001c0  ff ff 83 fe ff ff 02 38  34 00 cd c1 8e 02 00 fe  |.......84.......|
000001d0  ff ff 05 fe ff ff 01 00  00 00 b4 36 34 00 00 00  |...........64...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/zack/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected





:confused::confused::confused:

---

### Post by kc1di on 2012-04-28
Grub usually does a good job of finding your windows install and adding it to the menu.  So I'm not sure that you did not over write it. but if you didn't you can find it by doing the following from a terminal - 

```
sudo update-grub
```

If you want to make Windows the default boot 

Here's a page that describes how to do that:

[http://askubuntu.com/questions/82928/how-to-make-windows-boot-first]("http://askubuntu.com/questions/82928/how-to-make-windows-boot-first")

---

### Post by Monotoko on 2012-04-28
It should have detected it when you installed, try doing a simple ```
sudo update-grub
```

---

### Post by zeating on 2012-04-28
grub-update doesn't find it.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by kc1di on 2012-04-28
> **zeating said:**
> grub-update doesn't find it.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done

Try this first: it's the easiest if it works.

install Boot Repair from :

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
Run that and see if it finds windows if not let me know will walk you through how to add it to your grub menu.

---

### Post by zeating on 2012-04-28
I ran it but it still isn't in my grub list.
This is the log it gave me 
[http://paste.ubuntu.com/953349/](http://paste.ubuntu.com/953349/)

---

### Post by oldfred on 2012-04-28
Your boot flag is on sda2, but you have it labeled music. And it starts about 100MB from normal start of NTFS boot partition.

Did you delete the 100MB sda1 a hidden NTFS Windows boot/recovery partition that started at sector 2048 and had boot flag?

Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You are missing /bootmgr and /Boot/BCD. You need a Windows repairCD to add them back to you sda4 partition and have to move boot flag to sda4 as Windows only repairs the active (boot flag) partition.

If you have not overwritten anything in sda1, you might be able to recover it with testdisk.

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by zeating on 2012-04-28
> **oldfred said:**
> Your boot flag is on sda2, but you have it labeled music. And it starts about 100MB from normal start of NTFS boot partition.

Did you delete the 100MB sda1 a hidden NTFS Windows boot/recovery partition that started at sector 2048 and had boot flag?

Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You are missing /bootmgr and /Boot/BCD. You need a Windows repairCD to add them back to you sda4 partition and have to move boot flag to sda4 as Windows only repairs the active (boot flag) partition.

If you have not overwritten anything in sda1, you might be able to recover it with testdisk.

[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)


Actually, I did delete a 100mb partition..oops. I tried a windows repair cd but for some reason it said I was using the wrong version of windows for the repair, even though i used the CD yesterday on the same install of the OS. I'll try testdisk

---

