---
title: "Ubuntu No Longer in Grub Menu"
date: 2011-12-10
forum: General Help
---

### Post by nikRbokR on 2011-12-10
I currently have 11.10 dual-booting with Windows 7.

I decided to just log-in on my Ubuntu partition and update it, as I haven't used it in about a month. The updates installed, and I decided to restart the system. However, after restarting my computer, the Grub menu at boot up only shows Windows 7. The Oneiric installs are nowhere to be found.

How exactly would I fix this? I'd like to start using Ubuntu again :)

---

### Post by nikRbokR on 2011-12-10
So I ran Boot-Info Script, and these are my results:

sdb1 looks to be my external hard-drive that's plugged in, and sdc1 is probably the USB drive that I'm running the LiveCD from.


```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 20110518
    Boot sector info:   Syslinux looks at sector 1474440 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       305,234       305,172  de Dell Utility
/dev/sda2    *        307,200       511,999       204,800   7 NTFS / exFAT / HPFS
/dev/sda3             512,000   170,495,999   169,984,000   7 NTFS / exFAT / HPFS
/dev/sda4         170,498,046   312,576,704   142,078,659   5 Extended
/dev/sda5         205,326,828   312,576,704   107,249,877   7 NTFS / exFAT / HPFS
/dev/sda6         170,498,048   196,950,015    26,451,968  83 Linux
/dev/sda7         196,952,064   205,326,335     8,374,272  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   976,768,064   976,768,002   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4007 MB, 4007624704 bytes
32 heads, 63 sectors/track, 3882 cylinders, total 7827392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     7,826,111     7,826,049   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       dd8c66a5-68e9-4fb3-9514-a8033fa5f719   ext3       
/dev/sda1        07D9-0417                              vfat       DellUtility
/dev/sda2        D8144CE4144CC6EA                       ntfs       System Reserved
/dev/sda3        4ABA552BBA5514B3                       ntfs       
/dev/sda5        0B8BD09B2B8CED42                       ntfs       
/dev/sda6        75d4f900-c2d0-4df3-9782-18d32a3e65b7   ext4       
/dev/sda7        b1b9dce0-be7f-4d8b-9f9d-ca4089b3ae6b   swap       
/dev/sdb1        36308026307FEAEF                       ntfs       FreeAgent GoFlex Drive
/dev/sdc1        0418-13EC                              vfat       HP v125w

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/FreeAgent GoFlex Drive fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


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
set default="Windows 7 (loader) (on /dev/sda2)"
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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 75d4f900-c2d0-4df3-9782-18d32a3e65b7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 75d4f900-c2d0-4df3-9782-18d32a3e65b7
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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

### BEGIN /etc/grub.d/10_linux_proxy ###
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_os-prober_proxy ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root D8144CE4144CC6EA
	chainloader +1
}
### END /etc/grub.d/20_os-prober_proxy ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=75d4f900-c2d0-4df3-9782-18d32a3e65b7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=b1b9dce0-be7f-4d8b-9f9d-ca4089b3ae6b none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               1
               =                boot/initrd.img-3.0.0-12-generic-pae           2
               =                boot/initrd.img-3.0.0-13-generic               2
               =                boot/initrd.img-3.0.0-13-generic-pae           2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-12-generic-pae              2
               =                boot/vmlinuz-3.0.0-13-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic-pae              1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  b5 67 96 de 05 30 2f 41  78 12 ff 38 d1 00 f9 55  |.g...0/Ax..8...U|
00000010  2f 99 b6 5a 22 8f 1a b5  9c 24 56 40 01 9e 1f 01  |/..Z"....$V@....|
00000020  ad e4 51 2e 01 81 45 98  6b d6 9a 0a 7e 7d 95 07  |..Q...E.k...~}..|
00000030  ad a7 f9 3a 2e e3 dc 94  e8 8d 2b a4 05 f3 1d 71  |...:......+....q|
00000040  ff b0 f1 a0 a6 8c 89 4d  8a bd af a9 75 69 1c 01  |.......M....ui..|
00000050  c0 1b 6c cf 48 9c 88 e7  5a 70 6d b5 14 e4 5c 9f  |..l.H...Zpm...\.|
00000060  ef ac ca 06 45 ce 6d 0d  b0 51 bf d8 d6 f6 a0 a8  |....E.m..Q......|
00000070  05 5e 93 e9 82 77 08 7c  44 42 34 1a 10 22 77 02  |.^...w.|DB4.."w.|
00000080  60 39 80 c4 4f 99 04 a2  05 14 12 c1 6e 07 c2 cf  |`9..O.......n...|
00000090  d3 2a 05 4b 21 66 3c 2a  2f fe 03 4f 63 55 99 00  |.*.K!f<*/..OcU..|
000000a0  8b 4d 27 c5 38 a0 35 51  ff e5 06 0c 8e 1f 08 6a  |.M'.8.5Q.......j|
000000b0  93 ef ae 68 e3 db 50 5b  9c 78 cc de c5 cf 09 ee  |...h..P[.x......|
000000c0  72 ac 7c 36 59 82 e4 c1  fb 54 40 68 90 3d 67 bc  |r.|6Y....T@h.=g.|
000000d0  19 e9 e2 5a c3 51 ad 0f  06 dc 21 4d 25 4d 52 95  |...Z.Q....!M%MR.|
000000e0  55 73 7d 88 b5 ae 40 a6  6d 96 55 d1 c2 66 a0 46  |Us}...@.m.U..f.F|
000000f0  b5 55 ea d5 05 62 dc 02  26 53 2d 54 d6 83 07 54  |.U...b..&S-T...T|
00000100  6d 41 84 5d 09 10 62 e5  ef ba 31 87 a4 7a d2 ac  |mA.]..b...1..z..|
00000110  f9 5a bf e5 e2 06 3a 0c  13 ca f0 36 86 69 71 60  |.Z....:....6.iq`|
00000120  38 14 d7 8a 68 30 15 a0  c1 22 49 7c 10 2d 9b f1  |8...h0..."I|.-..|
00000130  d3 3a 0a e5 60 f9 d0 03  91 54 24 30 ac b8 3c 6f  |.:..`....T$0..<o|
00000140  bd e9 59 65 81 52 f4 0f  65 9b ed 6e f3 9c ed 6b  |..Ye.R..e..n...k|
00000150  60 bf a7 6d ae aa 2d 7b  7a a5 45 de 2e 8a 26 e4  |`..m..-{z.E...&.|
00000160  a6 5d c0 ab 84 70 5b 16  0a 3c 66 bb d4 d3 b4 d6  |.]...p[..<f.....|
00000170  f6 d5 ef be fb a3 25 08  de 33 8d 1e 8e 11 ea c5  |......%..3......|
00000180  44 7b 94 64 26 7b ed 67  df 5b 95 ec 66 1e 92 62  |D{.d&{.g.[..f..b|
00000190  a7 d7 29 bc 60 fb eb 64  cd 67 95 fe 65 80 18 05  |..).`..d.g..e...|
000001a0  3f ca af 58 34 24 09 58  10 c1 95 0f 95 8f be 08  |?..X4$.X........|
000001b0  73 da 24 7c 49 93 2d ba  cc a6 4a 96 68 e0 00 fe  |s.$|I.-...J.h...|
000001c0  ff ff 07 fe ff ff ee 71  13 02 d5 80 64 06 00 fe  |.......q....d...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 a0 93 01 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
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
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by oldfred on 2011-12-10
Boot script shows the Ubuntu entries missing, but script did find kernel & grub files. Errors on locations may be just awk, if you installed gawk it might just show a little more but that would not fix anything.

Sometimes this will boot a system with grub issues, otherwise you may have to chroot into your system from a liveCD or USB and update again from the chroot system.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by nikRbokR on 2011-12-10
> **oldfred said:**
> Boot script shows the Ubuntu entries missing, but script did find kernel & grub files. Errors on locations may be just awk, if you installed gawk it might just show a little more but that would not fix anything.

Sometimes this will boot a system with grub issues, otherwise you may have to chroot into your system from a liveCD or USB and update again from the chroot system.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
Thanks!

drs305's method was the one that worked for me (chroot and purge/reinstall Grub2)

I feel like it was the update that caused this issue. Not sure why. But, thanks again; this was great. I was about to reinstall...

---

### Post by oldfred on 2011-12-11
Glad you got it fixed.

I have had grub not write the entire grub.cfg when I had a typo in my 40_custom, otherwise I do not know why you would be missing the normal Ubuntu entries.

---

