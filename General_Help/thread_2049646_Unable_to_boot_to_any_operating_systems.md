---
title: "Unable to boot to any operating systems"
date: 2012-08-29
forum: General Help
---

### Post by Mathman87 on 2012-08-29
I've recently switched from Windows XP to Ubuntu 12.04. Just a few days ago I ran out of file system space for /. To try to repartition, I first tried running my usb flash drive with Ubuntu on it. That failed because of a decompression error so I wiped the usb drive. My next option was to try to boot Windows Vista which is on the same hard drive but different partition as Ubuntu. The error this time was that hal.dll was missing or corrupt. I tried rebooting; same luck. Next, I tried my old xp system which is on a totally separate hard drive. This time the error was bootmgr is missing. By this time I gave on Windows and tried Puppy Linux. It seemed to almost work untill it said loading initrcd or linuz and then just failed and rebooted. My last option was to try Windows Recovery. That got stuck on a screen and never went on. I would like to know what is Ubuntu has done to my computer or just what is wrong. Thanks for any help.

---

### Post by dino99 on 2012-08-29
my way for installation

[http://ubuntuforums.org/showpost.php?p=11843514&postcount=9](http://ubuntuforums.org/showpost.php?p=11843514&postcount=9)

---

### Post by Mark Phelps on 2012-08-29
You said you tried to repartition using GParted, and Vista is on the same hard drive as Ubuntu, right?  So, did you try to shrink the Vista partition using GParted? Doing that runs the risk of corrupting the Vista filesystem so it will not boot anymore.  Such corruption can produce the error message you saw.  You should ALWAYS shrink Vista/Win7 OS partitions using ONLY the MS Windows Disk Management utility.

If you don't have a Vista Repair CD, then you should look into using Boot-Repair (you will have to burn a CD of it) to see if that will repair the boot process:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by oldfred on 2012-08-29
Welcome to the forums, Mathman87.

An interesting chain of errors/problems. And Mark Phelps suggestion of Boot-Repair is good. Many of the Windows fixes will require Windows repairCD or installCD to fix those.

Uusally a hal.dll error is not hal missing but a malformed boot.ini for XP. And Bootmgr missing is from Vista or 7 partition PBR not XP. But when you install multiple Windows in one system, Windows installs all the boot files into one primary NTFS partition that has boot flag. It will convert a XP to Vista/7 partition also. NTFS has at least two different NTFS partition boot sectors - PBR.  One specifies to boot with XP's ntldr and the other to boot with Vista/7's bootmgr. So depending on what partition had/has boot flag and what Windows are installed will determine the boot process.

---

### Post by Mathman87 on 2012-09-01
Today, I tried boot repair. It boots up to the start screen where it asks you if you want to do 32 or 64 bit, then when you choose any it comes up with this error:

[          0.380249] Initramfs unpacking failed: junk in compressed archive
[          0.685388] Kernal panic - not syncing: VFS: Unable to mount root fs on unknown-block(254,4)

Then it the system halts and I have to reboot. I wonder if I have a dvd burning problem. I'm just using the burning utility that ubuntu 12.04 came with.

---

### Post by Mathman87 on 2012-09-01
[FONT=Arial]I just ran boot repair on ubuntu and it generated this report:[/FONT]

         Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info August 2nd 2012]


```
============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 2 for /grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdd.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdg.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /etc/fstab

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sdd1 has 0 
                       sectors.
    Operating System:  
    Boot files:        

sdg1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 539752 of /dev/sdg1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   488,279,609   488,279,547   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   201,872,789   201,872,727   7 NTFS / exFAT / HPFS
/dev/sdb2         201,873,408   202,459,135       585,728  83 Linux
/dev/sdb3         202,461,182   398,295,039   195,833,858   5 Extended
/dev/sdb5         202,461,184   206,364,671     3,903,488  82 Linux swap / Solaris
/dev/sdb6         206,366,720   221,988,863    15,622,144  83 Linux
/dev/sdb7         221,990,912   398,295,039   176,304,128  83 Linux


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 4 MB, 4030464 bytes
2 heads, 32 sectors/track, 123 cylinders, total 7872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             32         7,807         7,776   1 FAT12


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 4051 MB, 4051697664 bytes
128 heads, 42 sectors/track, 1472 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1    *             32     7,913,471     7,913,440   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        A82E654E2E65171A                       ntfs       From_Work_250WD_JS
/dev/sdb1        01C9B5EC5A0731A0                       ntfs       MxtrBkup_Vista_100GB
/dev/sdb2        fc9483be-8c9e-4ff6-bfda-586bbdd96d5d   ext4       
/dev/sdb5        a4693448-8851-4d68-94db-4f71b2fdc923   swap       
/dev/sdb6        37db65d7-d268-4d0f-b21d-18427bc01dbf   ext4       
/dev/sdb7        e969ceec-53d2-4a3a-a716-4e6929eb0d1b   ext4       
/dev/sdd1                                               vfat       DSC_LABEL
/dev/sdg1        F83E-5E4B                              vfat       PENDRIVE
/dev/sr0                                                iso9660    Boot-Repair-Disk

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb2        /boot                    ext4       (rw)
/dev/sdb6        /                        ext4       (rw,errors=remount-ro)
/dev/sdb7        /home                    ext4       (rw)
/dev/sdd1        /media/DSC_LABEL         vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdg1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0         /media/Boot-Repair-Disk  iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
--------------------------------------------------------------------------------

============================= sdb2/grub/grub.cfg: ==============================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set=root 37db65d7-d268-4d0f-b21d-18427bc01dbf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos2)'
  search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux    /vmlinuz-3.2.0-29-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    echo    'Loading Linux 3.2.0-29-generic-pae ...'
    linux    /vmlinuz-3.2.0-29-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-29-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux    /vmlinuz-3.2.0-27-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    echo    'Loading Linux 3.2.0-27-generic-pae ...'
    linux    /vmlinuz-3.2.0-27-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux    /vmlinuz-3.2.0-26-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-26-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    echo    'Loading Linux 3.2.0-26-generic-pae ...'
    linux    /vmlinuz-3.2.0-26-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-26-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux    /vmlinuz-3.2.0-23-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /vmlinuz-3.2.0-23-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 01C9B5EC5A0731A0
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

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  96.272395134 = 103.371697152  grub/core.img                                  1
            ?? = ??             grub/grub.cfg                                  1
  96.330539703 = 103.434129408  initrd.img-3.2.0-23-generic-pae                1
  96.436023712 = 103.547392000  initrd.img-3.2.0-26-generic-pae                1
  96.377440453 = 103.484488704  initrd.img-3.2.0-27-generic-pae                3
  96.455567360 = 103.568376832  initrd.img-3.2.0-29-generic-pae                2
  96.281040192 = 103.380979712  vmlinuz-3.2.0-23-generic-pae                   1
  96.290800095 = 103.391459328  vmlinuz-3.2.0-26-generic-pae                   1
  96.302519798 = 103.404043264  vmlinuz-3.2.0-27-generic-pae                   2
  96.384550095 = 103.492122624  vmlinuz-3.2.0-29-generic-pae                   1

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb2 during installation
UUID=fc9483be-8c9e-4ff6-bfda-586bbdd96d5d /boot           ext4    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=e969ceec-53d2-4a3a-a716-4e6929eb0d1b /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=a4693448-8851-4d68-94db-4f71b2fdc923 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  98.598145485 = 105.868952576  initrd.img                                     2
  98.520018578 = 105.785064448  initrd.img.old                                 3
  98.527128220 = 105.792698368  vmlinuz                                        1
  98.445097923 = 105.704619008  vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb3

00000000  93 b8 9f 78 d4 59 1d 73  d3 89 19 e0 16 5d 71 15  |...x.Y.s.....]q.|
00000010  f7 9f 5d 71 26 9f 55 72  b9 75 54 a4 54 f8 00 00  |..]q&.Ur.uT.T...|
00000020  01 1e 12 73 17 58 b2 74  ff 05 35 5e 09 3a 26 61  |...s.X.t..5^.:&a|
00000030  86 ae ee ef 06 a2 0e 5c  e4 18 9f 10 2f 09 74 5c  |.......\..../.t\|
00000040  57 23 da 9e ef 34 cf e0  fb c6 e6 72 c9 d3 a9 f4  |W#...4.....r....|
00000050  24 dc 3e ee f1 28 99 c9  80 ed b1 e7 9d da 3a cd  |$.>..(........:.|
00000060  bc 7e 06 ef 2d ce 55 ce  a1 46 44 4a e2 33 cd 11  |.~..-.U..FDJ.3..|
00000070  1d 5c 27 33 b1 9e 17 78  b1 90 63 2c e9 39 75 79  |.\'3...x..c,.9uy|
00000080  ae ee 17 26 f3 64 1f 92  40 92 45 ba e1 19 aa 4d  |...&.d..@.E....M|
00000090  39 8a d4 1f 77 99 90 ee  01 fd de 37 4f 78 d4 c2  |9...w......7Ox..|
000000a0  fb ab 3a b8 9b b9 e3 2f  06 b6 07 ec fb 77 16 61  |..:..../.....w.a|
000000b0  d7 75 c5 cc cd 9e 0c fd  d4 13 38 78 e2 7d ea 61  |.u........8x.}.a|
000000c0  17 84 a2 67 0e e0 76 16  c7 70 91 c6 49 10 03 e9  |...g..v..p..I...|
000000d0  c9 fa 7c 23 de 12 64 ce  e5 80 8a 40 f5 e1 58 4c  |..|#..d....@..XL|
000000e0  9b a2 83 6f dc cb 32 90  8e 1a 30 93 80 da 82 85  |...o..2...0.....|
000000f0  43 28 a0 b4 55 80 b2 ec  08 b5 b0 5c 9a e2 bb de  |C(..U......\....|
00000100  6c 85 71 96 f5 af 1e e8  87 0f b3 e4 d3 82 c0 e9  |l.q.............|
00000110  87 e0 39 44 e6 91 26 f1  f9 68 f8 9f 4e 65 ba d7  |..9D..&..h..Ne..|
00000120  9a 60 fc 4f 88 97 4e 1f  87 5e 0b 76 29 c0 6a 3a  |.`.O..N..^.v).j:|
00000130  87 06 f2 1c f4 50 5e 06  b4 4b 60 d0 cc 91 a9 1e  |.....P^..K`.....|
00000140  51 c1 cc 17 0a 3c 52 b8  ee 26 48 50 5d 83 a7 ff  |Q....<R..&HP]...|
00000150  de 3d 93 12 63 d8 70 0f  a0 19 d9 c3 d4 3a ec fa  |.=..c.p......:..|
00000160  e2 66 00 77 71 28 6b 9c  07 6b b0 6a 00 73 d6 06  |.f.wq(k..k.j.s..|
00000170  a6 3c cb bc 5a 26 0a b7  01 ac 44 31 71 6b c0 78  |.<..Z&....D1qk.x|
00000180  76 38 5d c9 13 78 d4 4c  e1 30 a2 78 7c e2 09 d1  |v8]..x.L.0.x|...|
00000190  e1 f7 5c 47 00 5d 78 6b  24 91 75 cd d4 f5 5c 44  |..\G.]xk$.u...\D|
000001a0  6e a5 c7 53 89 be 00 00  01 00 01 5a 92 eb b8 00  |n..S.......Z....|
000001b0  00 01 b5 83 32 23 04 00  00 00 01 01 12 57 00 fe  |....2#.......W..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 3b 00 00 fe  |............;...|
000001d0  ff ff 05 fe ff ff 02 90  3b 00 00 68 ee 00 00 00  |........;..h....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sde sdf 


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-09-01__12h32 ===================
boot-repair version : 3.18-0ppa52~precise
boot-sav version : 3.192-0ppa24~precise
glade2script version : 0.3.2.1-0ppa7~precise
boot-sav-nonfree version : 3.18-0ppa10~precise
W: Failed to fetch [http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


The following packages were automatically installed and are no longer required:
ttf-sil-gentium-basic libpython3.2 libhsqldb-java libservlet2.5-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 50 not upgraded.
dpkg-preconfigure: unable to re-open stdin: No such file or directory
boot-repair is executed in installed-session (Ubuntu 12.04.1 LTS, precise, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit

=================== os-prober:
/dev/sdb6:The OS now in use - Ubuntu 12.04.1 LTS CurrentSession:linux
/dev/sdb1:Windows Vista (loader):Windows:chain

=================== blkid:
/dev/sda1: LABEL="From_Work_250WD_JS" UUID="A82E654E2E65171A" TYPE="ntfs"
/dev/sr0: LABEL="Boot-Repair-Disk" TYPE="iso9660"
/dev/sdb1: LABEL="MxtrBkup_Vista_100GB" UUID="01C9B5EC5A0731A0" TYPE="ntfs"
/dev/sdb2: UUID="fc9483be-8c9e-4ff6-bfda-586bbdd96d5d" TYPE="ext4"
/dev/sdb5: UUID="a4693448-8851-4d68-94db-4f71b2fdc923" TYPE="swap"
/dev/sdb6: UUID="37db65d7-d268-4d0f-b21d-18427bc01dbf" TYPE="ext4"
/dev/sdb7: UUID="e969ceec-53d2-4a3a-a716-4e6929eb0d1b" TYPE="ext4"
/dev/sdg1: LABEL="PENDRIVE" UUID="F83E-5E4B" TYPE="vfat"
/dev/sdd1: SEC_TYPE="msdos" LABEL="DSC_LABEL" TYPE="vfat"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

XP not detected by os-prober on sda1. Please report this message to [email]yannubuntu@gmail.com[/email]
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"





=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul  3 08:29 grub.d
total 56
-rwxr-xr-x 1 root root 6715 Apr 17 12:16 00_header
-rwxr-xr-x 1 root root 5522 Apr 17 11:53 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17 01:22 10_linux
-rwxr-xr-x 1 root root 6335 Apr 17 12:16 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 Apr 17 12:16 30_os-prober
-rwxr-xr-x 1 root root  214 Apr 17 12:16 40_custom
-rwxr-xr-x 1 root root   95 Apr 17 12:16 41_custom
-rw-r--r-- 1 root root  483 Apr 17 12:16 README



/boot detected in the fstab of sdb6: UUID=fc9483be-8c9e-4ff6-bfda-586bbdd96d5d (sdb2)

=================== dmesg | grep EFI :
This installed-session is not EFI-compatible.
[    1.295811] EFI Variables Facility v0.08 2004-May-17



=================== PARTITIONS & DISKS:
sdb6    : sdb,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    haswinload,    no-recov-nor-hid,    bootmgr,    no-grldr,    Boot/BCD,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb1.
sdb2    : sdb,    is-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /boot.
sdb7    : sdb,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /home.
sdg1    : sdg,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /media/PENDRIVE.
sdd1    : sdd,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /media/DSC_LABEL.

sdb    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    63 sectors * 512 bytes
sda    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    63 sectors * 512 bytes
sdg    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-correctEFI,     usb-disk,    32 sectors * 512 bytes
sdd    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-correctEFI,     usb-disk,    32 sectors * 512 bytes

=================== parted -l:

Model: ATA WDC WD2500JS-75M (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  250GB  250GB  primary  ntfs         boot


Model: ATA Maxtor 6L200P0 (scsi)
Disk /dev/sdb: 204GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      32.3kB  103GB  103GB   primary   ntfs            boot
2      103GB   104GB  300MB   primary   ext4
3      104GB   204GB  100GB   extended
5      104GB   106GB  1999MB  logical   linux-swap(v1)
6      106GB   114GB  7999MB  logical   ext4
7      114GB   204GB  90.3GB  logical   ext4


Model: Generic USB CF Reader (scsi)
Disk /dev/sdd: 4030kB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  3998kB  3981kB  primary               boot



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label

Model: PNY USB 2.0 FD (scsi)
Disk /dev/sdg: 4052MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  4052MB  4052MB  primary  fat32        boot, lba


=================== mount:
/dev/sdb6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb2 on /boot type ext4 (rw)
/dev/sdb7 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/garon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=garon)
/dev/sdg1 on /media/PENDRIVE type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0 on /media/Boot-Repair-Disk type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)
/dev/sdd1 on /media/DSC_LABEL type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/fd0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb5 sdb6 sdb7 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd1 size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdg (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdg1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dvd dvdrw ecryptfs fb0 fd fd0 full fuse hidraw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null nvidia0 nvidiactl oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdb2 sdb3 sdb5 sdb6 sdb7 sdc sdd sdd1 sde sdf sdg sdg1 sg0 sg1 sg2 sg3 sg4 sg5 sg6 sg7 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 vga_arbiter zero
ls /dev/mapper:  control
ls: cannot access : No such file or directory
ls /mnt/boot-sav/sda1: WINDOWS VC_RED.MSI vcredist.bmp VC_RED.cab tmp Information Volume System RECYCLER Files Program pagefile.sys NVIDIA install.res.3082.dll install.res.2052.dll install.res.1049.dll install.res.1042.dll install.res.1041.dll install.res.1040.dll install.res.1036.dll install.res.1033.dll install.res.1031.dll install.res.1028.dll install.ini install.exe globdata.ini eula.3082.txt eula.2052.txt eula.1049.txt eula.1042.txt eula.1041.txt eula.1040.txt eula.1036.txt eula.1033.txt eula.1031.txt eula.1028.txt Settings and Documents BackupOn.8.14.2012
ls /mnt/boot-sav/sdb1: Windows Users Information Volume System RECYCLER $Recycle.Bin Files Program ProgramData ntldr NTDETECT.COM msdownld.tmp MSDOS.SYS IO.SYS IDT.log hiberfil.sys Settings and Documents config.sys BOOTSECT.BAK boot-sav bootmgr boot.ini Boot $AVG autoexec.bat

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb6      ext4      7.5G  6.8G  320M  96% /
udev           devtmpfs  1.4G   12K  1.4G   1% /dev
tmpfs          tmpfs     555M  1.1M  554M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.4G   80K  1.4G   1% /run/shm
/dev/sdb2      ext4      284M  107M  163M  40% /boot
/dev/sdb7      ext4       84G   42G   39G  53% /home
/dev/sdg1      vfat      3.8G   40K  3.8G   1% /media/PENDRIVE
/dev/sr0       iso9660   346M  346M     0 100% /media/Boot-Repair-Disk
/dev/sdd1      vfat      3.8M  3.0M  876K  78% /media/DSC_LABEL
/dev/sda1      fuseblk   233G   72G  162G  31% /mnt/boot-sav/sda1
/dev/sdb1      fuseblk    97G   13G   84G  14% /mnt/boot-sav/sdb1

=================== fdisk -l:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd2e2d2e2

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488279609   244139773+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0a2c65c6

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   201872789   100936363+   7  HPFS/NTFS/exFAT
/dev/sdb2       201873408   202459135      292864   83  Linux
/dev/sdb3       202461182   398295039    97916929    5  Extended
/dev/sdb5       202461184   206364671     1951744   82  Linux swap / Solaris
/dev/sdb6       206366720   221988863     7811072   83  Linux
/dev/sdb7       221990912   398295039    88152064   83  Linux

Disk /dev/sdg: 4051 MB, 4051697664 bytes
128 heads, 42 sectors/track, 1472 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *          32     7913471     3956720    c  W95 FAT32 (LBA)

Disk /dev/sdd: 4 MB, 4030464 bytes
2 heads, 32 sectors/track, 123 cylinders, total 7872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          32        7807        3888    1  FAT12


sdg1 EFI part (detected by BIS but not in fstab) in a USB disk
sdd1 EFI part (detected by BIS but not in fstab) in a USB disk
grub-efi not selected by default because: [efi not on GPT] [efi on USB] [no sure efi] [no other efi OS]
sdg1 EFI part (detected by BIS but not in fstab) in a USB disk
sdd1 EFI part (detected by BIS but not in fstab) in a USB disk
grub-efi not selected by default because: [efi not on GPT] [efi on USB] [no sure efi] [no other efi OS]
sdg1 EFI part (detected by BIS but not in fstab) in a USB disk
sdd1 EFI part (detected by BIS but not in fstab) in a USB disk
grub-efi not selected by default because: [efi not on GPT] [efi on USB] [no sure efi] [no other efi OS]

=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sdb6 into the MBRs of all disks (except USB without OS).
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 2
Fixed /mnt/boot-sav/sda1/boot.ini

Reinstall the GRUB of sdb6 into all MBRs of disks with OS or not-USB

Reinstall the GRUB of sdb6 into the MBR of sda
grub-install (GRUB) 1.99-21ubuntu3.1
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
grub-install --recheck /dev/sda: Installation finished. No error reported.
exit code of grub-install /dev/sda:0

Reinstall the GRUB of sdb6 into the MBR of sdb
grub-install (GRUB) 1.99-21ubuntu3.1
grub-install --recheck /dev/sdb: Installation finished. No error reported.
exit code of grub-install /dev/sdb:0

update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /memtest86+.bin
Found Windows Vista (loader) on /dev/sdb1
Unhide GRUB boot menu in sdb6/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (204GB) disk!
```

[FONT=Arial]After that, I tried Windows Vista and it said something like "load needed dlls for kernel." 
[/FONT]

---

### Post by jerome1232 on 2012-09-01
Please enclose output in [noparse]```
ouputgoeshere  
```[/noparse] tags in the future, it keeps it readable and it keeps  the formating intact.

> **Mathman87 said:**
> [FONT=Arial]I just ran boot repair on ubuntu and it generated this report:[/FONT]

         ```
Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info August 2nd 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 2 for /grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdd.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdg.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /etc/fstab

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sdd1 has 0 
                       sectors.
    Operating System:  
    Boot files:        

sdg1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 539752 of /dev/sdg1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   488,279,609   488,279,547   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   201,872,789   201,872,727   7 NTFS / exFAT / HPFS
/dev/sdb2         201,873,408   202,459,135       585,728  83 Linux
/dev/sdb3         202,461,182   398,295,039   195,833,858   5 Extended
/dev/sdb5         202,461,184   206,364,671     3,903,488  82 Linux swap / Solaris
/dev/sdb6         206,366,720   221,988,863    15,622,144  83 Linux
/dev/sdb7         221,990,912   398,295,039   176,304,128  83 Linux


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 4 MB, 4030464 bytes
2 heads, 32 sectors/track, 123 cylinders, total 7872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             32         7,807         7,776   1 FAT12


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 4051 MB, 4051697664 bytes
128 heads, 42 sectors/track, 1472 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1    *             32     7,913,471     7,913,440   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        A82E654E2E65171A                       ntfs       From_Work_250WD_JS
/dev/sdb1        01C9B5EC5A0731A0                       ntfs       MxtrBkup_Vista_100GB
/dev/sdb2        fc9483be-8c9e-4ff6-bfda-586bbdd96d5d   ext4       
/dev/sdb5        a4693448-8851-4d68-94db-4f71b2fdc923   swap       
/dev/sdb6        37db65d7-d268-4d0f-b21d-18427bc01dbf   ext4       
/dev/sdb7        e969ceec-53d2-4a3a-a716-4e6929eb0d1b   ext4       
/dev/sdd1                                               vfat       DSC_LABEL
/dev/sdg1        F83E-5E4B                              vfat       PENDRIVE
/dev/sr0                                                iso9660    Boot-Repair-Disk

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb2        /boot                    ext4       (rw)
/dev/sdb6        /                        ext4       (rw,errors=remount-ro)
/dev/sdb7        /home                    ext4       (rw)
/dev/sdd1        /media/DSC_LABEL         vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdg1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0         /media/Boot-Repair-Disk  iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
--------------------------------------------------------------------------------

============================= sdb2/grub/grub.cfg: ==============================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set=root 37db65d7-d268-4d0f-b21d-18427bc01dbf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos2)'
  search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux    /vmlinuz-3.2.0-29-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    echo    'Loading Linux 3.2.0-29-generic-pae ...'
    linux    /vmlinuz-3.2.0-29-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-29-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux    /vmlinuz-3.2.0-27-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    echo    'Loading Linux 3.2.0-27-generic-pae ...'
    linux    /vmlinuz-3.2.0-27-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux    /vmlinuz-3.2.0-26-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-26-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    echo    'Loading Linux 3.2.0-26-generic-pae ...'
    linux    /vmlinuz-3.2.0-26-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-26-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux    /vmlinuz-3.2.0-23-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /vmlinuz-3.2.0-23-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 01C9B5EC5A0731A0
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

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  96.272395134 = 103.371697152  grub/core.img                                  1
            ?? = ??             grub/grub.cfg                                  1
  96.330539703 = 103.434129408  initrd.img-3.2.0-23-generic-pae                1
  96.436023712 = 103.547392000  initrd.img-3.2.0-26-generic-pae                1
  96.377440453 = 103.484488704  initrd.img-3.2.0-27-generic-pae                3
  96.455567360 = 103.568376832  initrd.img-3.2.0-29-generic-pae                2
  96.281040192 = 103.380979712  vmlinuz-3.2.0-23-generic-pae                   1
  96.290800095 = 103.391459328  vmlinuz-3.2.0-26-generic-pae                   1
  96.302519798 = 103.404043264  vmlinuz-3.2.0-27-generic-pae                   2
  96.384550095 = 103.492122624  vmlinuz-3.2.0-29-generic-pae                   1

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb2 during installation
UUID=fc9483be-8c9e-4ff6-bfda-586bbdd96d5d /boot           ext4    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=e969ceec-53d2-4a3a-a716-4e6929eb0d1b /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=a4693448-8851-4d68-94db-4f71b2fdc923 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  98.598145485 = 105.868952576  initrd.img                                     2
  98.520018578 = 105.785064448  initrd.img.old                                 3
  98.527128220 = 105.792698368  vmlinuz                                        1
  98.445097923 = 105.704619008  vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb3

00000000  93 b8 9f 78 d4 59 1d 73  d3 89 19 e0 16 5d 71 15  |...x.Y.s.....]q.|
00000010  f7 9f 5d 71 26 9f 55 72  b9 75 54 a4 54 f8 00 00  |..]q&.Ur.uT.T...|
00000020  01 1e 12 73 17 58 b2 74  ff 05 35 5e 09 3a 26 61  |...s.X.t..5^.:&a|
00000030  86 ae ee ef 06 a2 0e 5c  e4 18 9f 10 2f 09 74 5c  |.......\..../.t\|
00000040  57 23 da 9e ef 34 cf e0  fb c6 e6 72 c9 d3 a9 f4  |W#...4.....r....|
00000050  24 dc 3e ee f1 28 99 c9  80 ed b1 e7 9d da 3a cd  |$.>..(........:.|
00000060  bc 7e 06 ef 2d ce 55 ce  a1 46 44 4a e2 33 cd 11  |.~..-.U..FDJ.3..|
00000070  1d 5c 27 33 b1 9e 17 78  b1 90 63 2c e9 39 75 79  |.\'3...x..c,.9uy|
00000080  ae ee 17 26 f3 64 1f 92  40 92 45 ba e1 19 aa 4d  |...&.d..@.E....M|
00000090  39 8a d4 1f 77 99 90 ee  01 fd de 37 4f 78 d4 c2  |9...w......7Ox..|
000000a0  fb ab 3a b8 9b b9 e3 2f  06 b6 07 ec fb 77 16 61  |..:..../.....w.a|
000000b0  d7 75 c5 cc cd 9e 0c fd  d4 13 38 78 e2 7d ea 61  |.u........8x.}.a|
000000c0  17 84 a2 67 0e e0 76 16  c7 70 91 c6 49 10 03 e9  |...g..v..p..I...|
000000d0  c9 fa 7c 23 de 12 64 ce  e5 80 8a 40 f5 e1 58 4c  |..|#..d....@..XL|
000000e0  9b a2 83 6f dc cb 32 90  8e 1a 30 93 80 da 82 85  |...o..2...0.....|
000000f0  43 28 a0 b4 55 80 b2 ec  08 b5 b0 5c 9a e2 bb de  |C(..U......\....|
00000100  6c 85 71 96 f5 af 1e e8  87 0f b3 e4 d3 82 c0 e9  |l.q.............|
00000110  87 e0 39 44 e6 91 26 f1  f9 68 f8 9f 4e 65 ba d7  |..9D..&..h..Ne..|
00000120  9a 60 fc 4f 88 97 4e 1f  87 5e 0b 76 29 c0 6a 3a  |.`.O..N..^.v).j:|
00000130  87 06 f2 1c f4 50 5e 06  b4 4b 60 d0 cc 91 a9 1e  |.....P^..K`.....|
00000140  51 c1 cc 17 0a 3c 52 b8  ee 26 48 50 5d 83 a7 ff  |Q....<R..&HP]...|
00000150  de 3d 93 12 63 d8 70 0f  a0 19 d9 c3 d4 3a ec fa  |.=..c.p......:..|
00000160  e2 66 00 77 71 28 6b 9c  07 6b b0 6a 00 73 d6 06  |.f.wq(k..k.j.s..|
00000170  a6 3c cb bc 5a 26 0a b7  01 ac 44 31 71 6b c0 78  |.<..Z&....D1qk.x|
00000180  76 38 5d c9 13 78 d4 4c  e1 30 a2 78 7c e2 09 d1  |v8]..x.L.0.x|...|
00000190  e1 f7 5c 47 00 5d 78 6b  24 91 75 cd d4 f5 5c 44  |..\G.]xk$.u...\D|
000001a0  6e a5 c7 53 89 be 00 00  01 00 01 5a 92 eb b8 00  |n..S.......Z....|
000001b0  00 01 b5 83 32 23 04 00  00 00 01 01 12 57 00 fe  |....2#.......W..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 3b 00 00 fe  |............;...|
000001d0  ff ff 05 fe ff ff 02 90  3b 00 00 68 ee 00 00 00  |........;..h....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sde sdf 


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-09-01__12h32 ===================
boot-repair version : 3.18-0ppa52~precise
boot-sav version : 3.192-0ppa24~precise
glade2script version : 0.3.2.1-0ppa7~precise
boot-sav-nonfree version : 3.18-0ppa10~precise
W: Failed to fetch [http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/killeroid/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


The following packages were automatically installed and are no longer required:
ttf-sil-gentium-basic libpython3.2 libhsqldb-java libservlet2.5-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 50 not upgraded.
dpkg-preconfigure: unable to re-open stdin: No such file or directory
boot-repair is executed in installed-session (Ubuntu 12.04.1 LTS, precise, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit

=================== os-prober:
/dev/sdb6:The OS now in use - Ubuntu 12.04.1 LTS CurrentSession:linux
/dev/sdb1:Windows Vista (loader):Windows:chain

=================== blkid:
/dev/sda1: LABEL="From_Work_250WD_JS" UUID="A82E654E2E65171A" TYPE="ntfs"
/dev/sr0: LABEL="Boot-Repair-Disk" TYPE="iso9660"
/dev/sdb1: LABEL="MxtrBkup_Vista_100GB" UUID="01C9B5EC5A0731A0" TYPE="ntfs"
/dev/sdb2: UUID="fc9483be-8c9e-4ff6-bfda-586bbdd96d5d" TYPE="ext4"
/dev/sdb5: UUID="a4693448-8851-4d68-94db-4f71b2fdc923" TYPE="swap"
/dev/sdb6: UUID="37db65d7-d268-4d0f-b21d-18427bc01dbf" TYPE="ext4"
/dev/sdb7: UUID="e969ceec-53d2-4a3a-a716-4e6929eb0d1b" TYPE="ext4"
/dev/sdg1: LABEL="PENDRIVE" UUID="F83E-5E4B" TYPE="vfat"
/dev/sdd1: SEC_TYPE="msdos" LABEL="DSC_LABEL" TYPE="vfat"


1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

XP not detected by os-prober on sda1. Please report this message to [EMAIL="yannubuntu@gmail.com"]yannubuntu@gmail.com[/EMAIL]
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"





=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul  3 08:29 grub.d
total 56
-rwxr-xr-x 1 root root 6715 Apr 17 12:16 00_header
-rwxr-xr-x 1 root root 5522 Apr 17 11:53 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17 01:22 10_linux
-rwxr-xr-x 1 root root 6335 Apr 17 12:16 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 Apr 17 12:16 30_os-prober
-rwxr-xr-x 1 root root  214 Apr 17 12:16 40_custom
-rwxr-xr-x 1 root root   95 Apr 17 12:16 41_custom
-rw-r--r-- 1 root root  483 Apr 17 12:16 README



/boot detected in the fstab of sdb6: UUID=fc9483be-8c9e-4ff6-bfda-586bbdd96d5d (sdb2)

=================== dmesg | grep EFI :
This installed-session is not EFI-compatible.
[    1.295811] EFI Variables Facility v0.08 2004-May-17



=================== PARTITIONS & DISKS:
sdb6    : sdb,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    haswinload,    no-recov-nor-hid,    bootmgr,    no-grldr,    Boot/BCD,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb1.
sdb2    : sdb,    is-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /boot.
sdb7    : sdb,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /home.
sdg1    : sdg,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /media/PENDRIVE.
sdd1    : sdd,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /media/DSC_LABEL.

sdb    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    63 sectors * 512 bytes
sda    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    63 sectors * 512 bytes
sdg    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-correctEFI,     usb-disk,    32 sectors * 512 bytes
sdd    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-correctEFI,     usb-disk,    32 sectors * 512 bytes

=================== parted -l:

Model: ATA WDC WD2500JS-75M (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  250GB  250GB  primary  ntfs         boot


Model: ATA Maxtor 6L200P0 (scsi)
Disk /dev/sdb: 204GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      32.3kB  103GB  103GB   primary   ntfs            boot
2      103GB   104GB  300MB   primary   ext4
3      104GB   204GB  100GB   extended
5      104GB   106GB  1999MB  logical   linux-swap(v1)
6      106GB   114GB  7999MB  logical   ext4
7      114GB   204GB  90.3GB  logical   ext4


Model: Generic USB CF Reader (scsi)
Disk /dev/sdd: 4030kB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  3998kB  3981kB  primary               boot



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label

Model: PNY USB 2.0 FD (scsi)
Disk /dev/sdg: 4052MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      16.4kB  4052MB  4052MB  primary  fat32        boot, lba


=================== mount:
/dev/sdb6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb2 on /boot type ext4 (rw)
/dev/sdb7 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/garon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=garon)
/dev/sdg1 on /media/PENDRIVE type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0 on /media/Boot-Repair-Disk type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)
/dev/sdd1 on /media/DSC_LABEL type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/fd0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb5 sdb6 sdb7 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd1 size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdg (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdg1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dvd dvdrw ecryptfs fb0 fd fd0 full fuse hidraw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null nvidia0 nvidiactl oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdb2 sdb3 sdb5 sdb6 sdb7 sdc sdd sdd1 sde sdf sdg sdg1 sg0 sg1 sg2 sg3 sg4 sg5 sg6 sg7 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 vga_arbiter zero
ls /dev/mapper:  control
ls: cannot access : No such file or directory
ls /mnt/boot-sav/sda1: WINDOWS VC_RED.MSI vcredist.bmp VC_RED.cab tmp Information Volume System RECYCLER Files Program pagefile.sys NVIDIA install.res.3082.dll install.res.2052.dll install.res.1049.dll install.res.1042.dll install.res.1041.dll install.res.1040.dll install.res.1036.dll install.res.1033.dll install.res.1031.dll install.res.1028.dll install.ini install.exe globdata.ini eula.3082.txt eula.2052.txt eula.1049.txt eula.1042.txt eula.1041.txt eula.1040.txt eula.1036.txt eula.1033.txt eula.1031.txt eula.1028.txt Settings and Documents BackupOn.8.14.2012
ls /mnt/boot-sav/sdb1: Windows Users Information Volume System RECYCLER $Recycle.Bin Files Program ProgramData ntldr NTDETECT.COM msdownld.tmp MSDOS.SYS IO.SYS IDT.log hiberfil.sys Settings and Documents config.sys BOOTSECT.BAK boot-sav bootmgr boot.ini Boot $AVG autoexec.bat

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb6      ext4      7.5G  6.8G  320M  96% /
udev           devtmpfs  1.4G   12K  1.4G   1% /dev
tmpfs          tmpfs     555M  1.1M  554M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.4G   80K  1.4G   1% /run/shm
/dev/sdb2      ext4      284M  107M  163M  40% /boot
/dev/sdb7      ext4       84G   42G   39G  53% /home
/dev/sdg1      vfat      3.8G   40K  3.8G   1% /media/PENDRIVE
/dev/sr0       iso9660   346M  346M     0 100% /media/Boot-Repair-Disk
/dev/sdd1      vfat      3.8M  3.0M  876K  78% /media/DSC_LABEL
/dev/sda1      fuseblk   233G   72G  162G  31% /mnt/boot-sav/sda1
/dev/sdb1      fuseblk    97G   13G   84G  14% /mnt/boot-sav/sdb1

=================== fdisk -l:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd2e2d2e2

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488279609   244139773+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0a2c65c6

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   201872789   100936363+   7  HPFS/NTFS/exFAT
/dev/sdb2       201873408   202459135      292864   83  Linux
/dev/sdb3       202461182   398295039    97916929    5  Extended
/dev/sdb5       202461184   206364671     1951744   82  Linux swap / Solaris
/dev/sdb6       206366720   221988863     7811072   83  Linux
/dev/sdb7       221990912   398295039    88152064   83  Linux

Disk /dev/sdg: 4051 MB, 4051697664 bytes
128 heads, 42 sectors/track, 1472 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *          32     7913471     3956720    c  W95 FAT32 (LBA)

Disk /dev/sdd: 4 MB, 4030464 bytes
2 heads, 32 sectors/track, 123 cylinders, total 7872 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          32        7807        3888    1  FAT12


sdg1 EFI part (detected by BIS but not in fstab) in a USB disk
sdd1 EFI part (detected by BIS but not in fstab) in a USB disk
grub-efi not selected by default because: [efi not on GPT] [efi on USB] [no sure efi] [no other efi OS]
sdg1 EFI part (detected by BIS but not in fstab) in a USB disk
sdd1 EFI part (detected by BIS but not in fstab) in a USB disk
grub-efi not selected by default because: [efi not on GPT] [efi on USB] [no sure efi] [no other efi OS]
sdg1 EFI part (detected by BIS but not in fstab) in a USB disk
sdd1 EFI part (detected by BIS but not in fstab) in a USB disk
grub-efi not selected by default because: [efi not on GPT] [efi on USB] [no sure efi] [no other efi OS]

=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sdb6 into the MBRs of all disks (except USB without OS).
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 2
Fixed /mnt/boot-sav/sda1/boot.ini

Reinstall the GRUB of sdb6 into all MBRs of disks with OS or not-USB

Reinstall the GRUB of sdb6 into the MBR of sda
grub-install (GRUB) 1.99-21ubuntu3.1
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
grub-install --recheck /dev/sda: Installation finished. No error reported.
exit code of grub-install /dev/sda:0

Reinstall the GRUB of sdb6 into the MBR of sdb
grub-install (GRUB) 1.99-21ubuntu3.1
grub-install --recheck /dev/sdb: Installation finished. No error reported.
exit code of grub-install /dev/sdb:0

update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /memtest86+.bin
Found Windows Vista (loader) on /dev/sdb1
Unhide GRUB boot menu in sdb6/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (204GB) disk!

After that, I tried Windows Vista and it said something like "load needed dlls for kernel." 
```[FONT=Arial]
[/FONT]

---

### Post by oldfred on 2012-09-01
If you set BIOS to boot from sdb or the 204GB drive does it now boot?

Which Windows is in sda & which is in sdb? Windows normally moves all boot files from second install to the first and converts the PBR or partition boot sector to the newer type.

But you have a boot.ini in both sda1 & sdb1.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

But your PBR's seem reversed. NTFS has two versions. One spells out to boot with bootmgr for Vista or 7 and the other uses ntldr for XP. If you want to separately boot you may have to repair PBR and move boot files to correct version.

For quick overview of how Windows multi-boots review pictures.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by YannBuntu on 2012-09-03
> **oldfred said:**
> Which Windows is in sda & which is in sdb?

According to post#1, XP is in sda.

[QUOTE=Mathman87]After that, I tried Windows Vista and it said something like "load needed dlls for kernel."[/QUOTE]

At reboot, the GRUB menu appears, doesn't it? can you boot Ubuntu?

If yes, you need to:
1) boot on a Vista disk to fix the dll problem (maybe the fixboot command will help). Then you should get direct access to Windows, and no more GRUB menu.
2) then you can use Boot-Repair to recover the GRUB menu.

---

### Post by oldfred on 2012-09-03
@Yann
I just wanted to confirm which system is where as it seems the PBR (Partition boot sectors)  are reversed to which version of Windows. PBR has to match system booted as PBR will specify boot file ntldr or bootmgr.

Boot sector type: Windows Vista/7: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows XP

Boot sector type: Windows XP: NTFS
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows Vista

---

### Post by YannBuntu on 2012-09-03
ok.
@Mathman87: please could you confirm ?

---

### Post by Mathman87 on 2012-09-08
Just to make things clear, the sda hard drive only contains Windows XP and nothing else. sdb, however, has Windows Vista and Ubuntu. I copied ntldr and NTDETECT.COM from the Windows XP disk to sda. I deleted boot.ini from sdb1. I tried booting into vista and and an error occurred again saying "Disk read error. press control alt delete to restart". I tried to boot into sda (windows XP) and it just brought me back to grub. I went back into Ubuntu and ran boot repair again and it generated this report:

   Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info August 2nd 2012]
```


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 2 for /grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/grub on this drive.
 => Windows is installed in the MBR of /dev/sdg.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /NTLDR /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /ntldr /NTDETECT.COM

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /etc/fstab

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdg1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   488,279,609   488,279,547   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   201,872,789   201,872,727   7 NTFS / exFAT / HPFS
/dev/sdb2         201,873,408   202,459,135       585,728  83 Linux
/dev/sdb3         202,461,182   398,295,039   195,833,858   5 Extended
/dev/sdb5         202,461,184   206,364,671     3,903,488  82 Linux swap / Solaris
/dev/sdb6         206,366,720   221,988,863    15,622,144  83 Linux
/dev/sdb7         221,990,912   398,295,039   176,304,128  83 Linux


Drive: sdg _____________________________________________________________________

Disk /dev/sdg: 127 MB, 127451136 bytes
33 heads, 32 sectors/track, 235 cylinders, total 248928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdg1    *             32       248,926       248,895   4 FAT16 <32M


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        A82E654E2E65171A                       ntfs       From_Work_250WD_JS
/dev/sdb1        01C9B5EC5A0731A0                       ntfs       MxtrBkup_Vista_100GB
/dev/sdb2        fc9483be-8c9e-4ff6-bfda-586bbdd96d5d   ext4       
/dev/sdb5        a4693448-8851-4d68-94db-4f71b2fdc923   swap       
/dev/sdb6        37db65d7-d268-4d0f-b21d-18427bc01dbf   ext4       
/dev/sdb7        e969ceec-53d2-4a3a-a716-4e6929eb0d1b   ext4       
/dev/sdg1                                               vfat       GARONS DISK
/dev/sr0                                                iso9660    WINLITE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb2        /boot                    ext4       (rw)
/dev/sdb6        /                        ext4       (rw,errors=remount-ro)
/dev/sdb7        /home                    ext4       (rw)
/dev/sdg1        /media/GARONS DISK       vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr0         /media/WINLITE           iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(1)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
--------------------------------------------------------------------------------

============================= sdb2/grub/grub.cfg: ==============================

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
set root='(hd1,msdos6)'
search --no-floppy --fs-uuid --set=root 37db65d7-d268-4d0f-b21d-18427bc01dbf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos2)'
  search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux    /vmlinuz-3.2.0-29-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    echo    'Loading Linux 3.2.0-29-generic-pae ...'
    linux    /vmlinuz-3.2.0-29-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-29-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux    /vmlinuz-3.2.0-27-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    echo    'Loading Linux 3.2.0-27-generic-pae ...'
    linux    /vmlinuz-3.2.0-27-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-27-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux    /vmlinuz-3.2.0-26-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-26-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    echo    'Loading Linux 3.2.0-26-generic-pae ...'
    linux    /vmlinuz-3.2.0-26-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-26-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux    /vmlinuz-3.2.0-23-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /vmlinuz-3.2.0-23-generic-pae root=UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set=root fc9483be-8c9e-4ff6-bfda-586bbdd96d5d
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root A82E654E2E65171A
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 01C9B5EC5A0731A0
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

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  96.272395134 = 103.371697152  grub/core.img                                  1
            ?? = ??             grub/grub.cfg                                  1
  96.330539703 = 103.434129408  initrd.img-3.2.0-23-generic-pae                1
  96.436023712 = 103.547392000  initrd.img-3.2.0-26-generic-pae                1
  96.377440453 = 103.484488704  initrd.img-3.2.0-27-generic-pae                3
  96.455567360 = 103.568376832  initrd.img-3.2.0-29-generic-pae                2
  96.281040192 = 103.380979712  vmlinuz-3.2.0-23-generic-pae                   1
  96.290800095 = 103.391459328  vmlinuz-3.2.0-26-generic-pae                   1
  96.302519798 = 103.404043264  vmlinuz-3.2.0-27-generic-pae                   2
  96.384550095 = 103.492122624  vmlinuz-3.2.0-29-generic-pae                   1

=============================== sdb6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=37db65d7-d268-4d0f-b21d-18427bc01dbf /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb2 during installation
UUID=fc9483be-8c9e-4ff6-bfda-586bbdd96d5d /boot           ext4    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=e969ceec-53d2-4a3a-a716-4e6929eb0d1b /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=a4693448-8851-4d68-94db-4f71b2fdc923 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  98.598145485 = 105.868952576  initrd.img                                     2
  98.520018578 = 105.785064448  initrd.img.old                                 3
  98.527128220 = 105.792698368  vmlinuz                                        1
  98.445097923 = 105.704619008  vmlinuz.old                                    2

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb3

00000000  93 b8 9f 78 d4 59 1d 73  d3 89 19 e0 16 5d 71 15  |...x.Y.s.....]q.|
00000010  f7 9f 5d 71 26 9f 55 72  b9 75 54 a4 54 f8 00 00  |..]q&.Ur.uT.T...|
00000020  01 1e 12 73 17 58 b2 74  ff 05 35 5e 09 3a 26 61  |...s.X.t..5^.:&a|
00000030  86 ae ee ef 06 a2 0e 5c  e4 18 9f 10 2f 09 74 5c  |.......\..../.t\|
00000040  57 23 da 9e ef 34 cf e0  fb c6 e6 72 c9 d3 a9 f4  |W#...4.....r....|
00000050  24 dc 3e ee f1 28 99 c9  80 ed b1 e7 9d da 3a cd  |$.>..(........:.|
00000060  bc 7e 06 ef 2d ce 55 ce  a1 46 44 4a e2 33 cd 11  |.~..-.U..FDJ.3..|
00000070  1d 5c 27 33 b1 9e 17 78  b1 90 63 2c e9 39 75 79  |.\'3...x..c,.9uy|
00000080  ae ee 17 26 f3 64 1f 92  40 92 45 ba e1 19 aa 4d  |...&.d..@.E....M|
00000090  39 8a d4 1f 77 99 90 ee  01 fd de 37 4f 78 d4 c2  |9...w......7Ox..|
000000a0  fb ab 3a b8 9b b9 e3 2f  06 b6 07 ec fb 77 16 61  |..:..../.....w.a|
000000b0  d7 75 c5 cc cd 9e 0c fd  d4 13 38 78 e2 7d ea 61  |.u........8x.}.a|
000000c0  17 84 a2 67 0e e0 76 16  c7 70 91 c6 49 10 03 e9  |...g..v..p..I...|
000000d0  c9 fa 7c 23 de 12 64 ce  e5 80 8a 40 f5 e1 58 4c  |..|#..d....@..XL|
000000e0  9b a2 83 6f dc cb 32 90  8e 1a 30 93 80 da 82 85  |...o..2...0.....|
000000f0  43 28 a0 b4 55 80 b2 ec  08 b5 b0 5c 9a e2 bb de  |C(..U......\....|
00000100  6c 85 71 96 f5 af 1e e8  87 0f b3 e4 d3 82 c0 e9  |l.q.............|
00000110  87 e0 39 44 e6 91 26 f1  f9 68 f8 9f 4e 65 ba d7  |..9D..&..h..Ne..|
00000120  9a 60 fc 4f 88 97 4e 1f  87 5e 0b 76 29 c0 6a 3a  |.`.O..N..^.v).j:|
00000130  87 06 f2 1c f4 50 5e 06  b4 4b 60 d0 cc 91 a9 1e  |.....P^..K`.....|
00000140  51 c1 cc 17 0a 3c 52 b8  ee 26 48 50 5d 83 a7 ff  |Q....<R..&HP]...|
00000150  de 3d 93 12 63 d8 70 0f  a0 19 d9 c3 d4 3a ec fa  |.=..c.p......:..|
00000160  e2 66 00 77 71 28 6b 9c  07 6b b0 6a 00 73 d6 06  |.f.wq(k..k.j.s..|
00000170  a6 3c cb bc 5a 26 0a b7  01 ac 44 31 71 6b c0 78  |.<..Z&....D1qk.x|
00000180  76 38 5d c9 13 78 d4 4c  e1 30 a2 78 7c e2 09 d1  |v8]..x.L.0.x|...|
00000190  e1 f7 5c 47 00 5d 78 6b  24 91 75 cd d4 f5 5c 44  |..\G.]xk$.u...\D|
000001a0  6e a5 c7 53 89 be 00 00  01 00 01 5a 92 eb b8 00  |n..S.......Z....|
000001b0  00 01 b5 83 32 23 04 00  00 00 01 01 12 57 00 fe  |....2#.......W..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 3b 00 00 fe  |............;...|
000001d0  ff ff 05 fe ff ff 02 90  3b 00 00 68 ee 00 00 00  |........;..h....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdg1

00000000  eb 3c 90 2c 27 2f 62 6e  49 48 43 00 02 04 01 00  |.<.,'/bnIHC.....|
00000010  02 00 02 00 00 f8 f4 00  20 00 21 00 20 00 00 00  |........ .!. ...|
00000020  3f cc 03 00 80 00 29 00  00 00 00 4e 4f 20 4e 41  |?.....)....NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-09-08__20h20 ===================
boot-repair version : 3.193-0ppa1~precise
boot-sav version : 3.193-0ppa2~precise
glade2script version : 0.3.2.1-0ppa7~precise
boot-sav-nonfree version : 3.18-0ppa20~precise
boot-repair updated
boot-repair is executed in installed-session (Ubuntu 12.04.1 LTS, precise, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit

=================== os-prober:
/dev/sdb6:The OS now in use - Ubuntu 12.04.1 LTS CurrentSession:linux
/dev/sda1:Microsoft Windows XP Home Edition:Windows:chain
/dev/sdb1:Windows Vista (loader):Windows1:chain

=================== blkid:
/dev/sda1: LABEL="From_Work_250WD_JS" UUID="A82E654E2E65171A" TYPE="ntfs"
/dev/sr0: LABEL="WINLITE" TYPE="iso9660"
/dev/sdb1: LABEL="MxtrBkup_Vista_100GB" UUID="01C9B5EC5A0731A0" TYPE="ntfs"
/dev/sdb2: UUID="fc9483be-8c9e-4ff6-bfda-586bbdd96d5d" TYPE="ext4"
/dev/sdb5: UUID="a4693448-8851-4d68-94db-4f71b2fdc923" TYPE="swap"
/dev/sdb6: UUID="37db65d7-d268-4d0f-b21d-18427bc01dbf" TYPE="ext4"
/dev/sdb7: UUID="e969ceec-53d2-4a3a-a716-4e6929eb0d1b" TYPE="ext4"
/dev/sdg1: SEC_TYPE="msdos" LABEL="GARONS DISK" TYPE="vfat"


2 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"





=================== /etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul  3 08:29 grub.d
total 56
-rwxr-xr-x 1 root root 6715 Apr 17 12:16 00_header
-rwxr-xr-x 1 root root 5522 Apr 17 11:53 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17 01:22 10_linux
-rwxr-xr-x 1 root root 6335 Apr 17 12:16 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 Apr 17 12:16 30_os-prober
-rwxr-xr-x 1 root root  214 Apr 17 12:16 40_custom
-rwxr-xr-x 1 root root   95 Apr 17 12:16 41_custom
-rw-r--r-- 1 root root  483 Apr 17 12:16 README



/boot detected in the fstab of sdb6: UUID=fc9483be-8c9e-4ff6-bfda-586bbdd96d5d (sdb2)

=================== dmesg | grep EFI :
This installed-session is not EFI-compatible.



=================== PARTITIONS & DISKS:
sdb6    : sdb,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-has-goodBOOT,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    NTLDR,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    haswinload,    no-recov-nor-hid,    bootmgr,    no-grldr,    Boot/BCD,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sdb1.
sdb2    : sdb,    is-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /boot.
sdb7    : sdb,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /home.
sdg1    : sdg,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    is-correct-EFI,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    no-grldr,    no-b-bcd,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /media/GARONS DISK.

sdb    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    63 sectors * 512 bytes
sda    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    63 sectors * 512 bytes
sdg    : MSDos,    not-GPT,    BIOSboot-not-needed,    has-correctEFI,     usb-disk,    32 sectors * 512 bytes

=================== parted -l:

Model: ATA WDC WD2500JS-75M (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  250GB  250GB  primary  ntfs         boot


Model: ATA Maxtor 6L200P0 (scsi)
Disk /dev/sdb: 204GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      32.3kB  103GB  103GB   primary   ntfs            boot
2      103GB   104GB  300MB   primary   ext4
3      104GB   204GB  100GB   extended
5      104GB   106GB  1999MB  logical   linux-swap(v1)
6      106GB   114GB  7999MB  logical   ext4
7      114GB   204GB  90.3GB  logical   ext4



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label

Model: LEXAR JUMPDRIVE SPORT (scsi)
Disk /dev/sdg: 127MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      16.4kB  127MB  127MB  primary  fat16        boot


=================== mount:
/dev/sdb6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdb2 on /boot type ext4 (rw)
/dev/sdb7 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/garon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=garon)
/dev/sr0 on /media/WINLITE type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)
/dev/sdg1 on /media/GARONS DISK type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /mnt/boot-sav/sdb1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/fd0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb5 sdb6 sdb7 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdg (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdg1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dvd dvdrw ecryptfs fb0 fd fd0 full fuse hidraw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null nvidia0 nvidiactl oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdb2 sdb3 sdb5 sdb6 sdb7 sdc sdd sde sdf sdg sdg1 sg0 sg1 sg2 sg3 sg4 sg5 sg6 sg7 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 vga_arbiter zero
ls /dev/mapper:  control
ls: cannot access : No such file or directory
ls /mnt/boot-sav/sda1: WINDOWS VC_RED.MSI vcredist.bmp VC_RED.cab tmp Information Volume System RECYCLER Files Program pagefile.sys NVIDIA NTLDR NTDETECT.COM install.res.3082.dll install.res.2052.dll install.res.1049.dll install.res.1042.dll install.res.1041.dll install.res.1040.dll install.res.1036.dll install.res.1033.dll install.res.1031.dll install.res.1028.dll install.ini install.exe globdata.ini eula.3082.txt eula.2052.txt eula.1049.txt eula.1042.txt eula.1041.txt eula.1040.txt eula.1036.txt eula.1033.txt eula.1031.txt eula.1028.txt Settings and Documents boot-sav boot.ini BackupOn.8.14.2012
ls /mnt/boot-sav/sdb1: Windows Users Information Volume System RECYCLER $Recycle.Bin Files Program ProgramData ntldr NTDETECT.COM msdownld.tmp MSDOS.SYS IO.SYS IDT.log hiberfil.sys Settings and Documents config.sys BOOTSECT.BAK boot-sav bootmgr Boot $AVG autoexec.bat

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb6      ext4      7.5G  6.7G  381M  95% /
udev           devtmpfs  1.4G   12K  1.4G   1% /dev
tmpfs          tmpfs     555M  1.2M  554M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.4G   76K  1.4G   1% /run/shm
/dev/sdb2      ext4      284M  107M  163M  40% /boot
/dev/sdb7      ext4       84G   42G   39G  53% /home
/dev/sr0       iso9660   525M  525M     0 100% /media/WINLITE
/dev/sdg1      vfat      122M   32M   90M  26% /media/GARONS DISK
/dev/sda1      fuseblk   233G   72G  162G  31% /mnt/boot-sav/sda1
/dev/sdb1      fuseblk    97G   13G   84G  14% /mnt/boot-sav/sdb1

=================== fdisk -l:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd2e2d2e2

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488279609   244139773+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0a2c65c6

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   201872789   100936363+   7  HPFS/NTFS/exFAT
/dev/sdb2       201873408   202459135      292864   83  Linux
/dev/sdb3       202461182   398295039    97916929    5  Extended
/dev/sdb5       202461184   206364671     1951744   82  Linux swap / Solaris
/dev/sdb6       206366720   221988863     7811072   83  Linux
/dev/sdb7       221990912   398295039    88152064   83  Linux

Disk /dev/sdg: 127 MB, 127451136 bytes
33 heads, 32 sectors/track, 235 cylinders, total 248928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *          32      248926      124447+   4  FAT16 <32M


sdg1 EFI part (detected by BIS but not in fstab) in a USB disk
grub-efi not selected by default because: [efi not on GPT] [efi on USB] [no sure efi] [no other efi OS]
User choice: Is sdb (204GB) a removable disk? no
sdg1 EFI part (detected by BIS but not in fstab) in a USB disk
grub-efi not selected by default because: [efi not on GPT] [efi on USB] [no sure efi] [no other efi OS]
sdg1 EFI part (detected by BIS but not in fstab) in a USB disk
grub-efi not selected by default because: [efi not on GPT] [efi on USB] [no sure efi] [no other efi OS]
sdg1 EFI part (detected by BIS but not in fstab) in a USB disk
grub-efi not selected by default because: [efi not on GPT] [efi on USB] [no sure efi] [no other efi OS]

=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sdb6 into the MBRs of all disks (except USB without OS).
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 2

Reinstall the GRUB of sdb6 into all MBRs of disks with OS or not-USB

Reinstall the GRUB of sdb6 into the MBR of sda
grub-install (GRUB) 1.99-21ubuntu3.1
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
grub-install --recheck /dev/sda: Installation finished. No error reported.
exit code of grub-install /dev/sda:0

Reinstall the GRUB of sdb6 into the MBR of sdb
grub-install (GRUB) 1.99-21ubuntu3.1
grub-install --recheck /dev/sdb: Installation finished. No error reported.
exit code of grub-install /dev/sdb:0

update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-27-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-27-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sda1
Found Windows Vista (loader) on /dev/sdb1
Unhide GRUB boot menu in sdb6/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sdb (204GB) disk!

The boot files of [The OS now in use - Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)
```(By the way, sdg is my xp install disk) If it is a PBR problem then how would I fix it because I see it does look reversed.

---

### Post by oldfred on 2012-09-08
I am not sure if fixBoot works. In anther thread it did not. I now think fixBoot only restores the backup and does not create a new boot sector.

I would try chkdsk, but use XP for the XP install and Windows 7 for the 7 install.

If chkdsk does not work you can run this from the Windows 7 repairCD.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by Mathman87 on 2012-09-09
I tried to boot into Windows Recovery Console from the XP disk and it returned this error:
[IMG]http://i47.tinypic.com/8wgrux.jpg[/IMG]

I think Ubuntu must have screwed up Windows interpretation of ntfs.

---

### Post by oldfred on 2012-09-09
It just maybe that XP does not properly see the Windows 7 partitions. The Windows 7 PBR is different than the XP verison. I did use a Windows 7 repairUSB to run chkdsk on my XP, but it converted it to a Windows 7 PBR. I then had to run the commands I posted above to convert PBR back to an XP version.

---

### Post by Mathman87 on 2012-09-10
A few days ago I tried to fix the master boot record of sda and sdb with lilo. Today, I restarted my computer and tried the Windows XP install disc, the windows Vista install disk, and boot-repair. They all failed. I tried to boot into sda and it said ntldr is missing. I tried to boot into sdb. Nothing happened. All I got was a black screen. I have no clue why none of my cds worked or why grub isn't showing up. The only clue I have is it keeps saying there are problems with the file system and ntfs. Now I'm using my laptop.

---

### Post by oldfred on 2012-09-10
Boot -Repair will not fix most Windows issues.

But Windows should. But if you repair a Vista install with an XP disk you will have the wrong Boot Sector and it will try to boot with XP's ntldr when it needs bootmgr to boot Vista.

Often running chkdsk repairs Windows also.

I know you can do this from a Windows 7 repairCD. Not sure if Vista is identical or not.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by Mathman87 on 2012-09-11
The problem with using bootrec.exe is that it's impossible for me to run it. Every time I try to run my Vista disk, the first screen that comes up is an error screen saying that I have to reboot. With Windows xp disk, I'm able to get as far as the setup screen but then it complains about errors with ntfs. Since nothing seems to be working I might have to just take out the drive and reformat it since grub won't boot up.

---

### Post by Mathman87 on 2012-09-13
Today I ran memtest86+ half way and got over 600,000 errors and I tried to install windows 8 and got IRQL_Not_Less_Or_Equal. Does this mean I have a memory problem?

---

### Post by oldfred on 2012-09-13
Why were you even trying to install Windows with defective memory?

You might try removing it and seeing if one or more banks is ok and the other is defective. That is if it is more than one memory bank.

---

### Post by jerome1232 on 2012-09-14
I would also pull out a can-o-air and do some reseating just to see, it's rare but things can wiggle out of place in there.

---

### Post by Mathman87 on 2012-09-14
I just made a bootable usb drive containing lubuntu and guess what it actually worked! I typing this using lubuntu right now. Does this mean Ubuntu and Ubuntu variants only work on my computer now? 
I also tried my sda hard drive and now it says hal.dll is missing. I put in my Recovery CD for xp and got this error with ntfs.sys: PAGE_FAULT_IN_NONPAGED_AREA. I see that's another memory error.

---

### Post by oldfred on 2012-09-14
You said you had Vista, but hal.dll errors are usually a error in XP's boot.ini.

Did you check your memory and clean it as posted above?

---

### Post by Mathman87 on 2012-09-15
I logged into Lubuntu through my bootable disk and changed the boot.ini rdisk number from 1 to 0. Now when I boot into xp it displays a prompt to coose between safe mode, last known configuration that was good, and start windows normally. All of them just restart my computer.

---

### Post by Mathman87 on 2012-09-16
Success! I randomly removed a RAM module, tonight and tried booting up xp. This time chkdsk ran and did something then restarted and I booted up again and suddenly it worked. I guess my problem was bad ram. Thanks for all the help guys.

---

