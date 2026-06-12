---
title: "Grub can't load Win7"
date: 2012-05-13
forum: General Help
---

### Post by Bo Rosén on 2012-05-13
I realise I may be posting in the wrong place here, but as I'm unsure what the problem really  is, well here goes.

I had to clone my entire disk the other day after the computer stared behaving oddly, it turned out it had bad sectors that couldn't be repaired.
I had an identical disk and cloned all the partitions with clonezilla, but did get errors for one partition which I stupidly didn't note on paper.

After swapping the drives Ubuntu runs fine, but Grub won't start Win7. After selecting windows from the grub menu all I get is a black screen with a blinking cursor.
I've tried reinstalling grub, run Boot-Repair even had it repair the MBR, started from the Win7 disc to repair the installation but nothing helps. 

I suspect I'll have to reinstall Win7, but I really don't want to risk messing upp my Skyrim installation unless I really, really have to ;)

Output from bootscriptinfo has the following to say, I notice the worrying last lines...

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid f2649ed9-2167-4e66-a523-d9a89c8e2892 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid f2649ed9-2167-4e66-a523-d9a89c8e2892 root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 huvuden, 63 sektorer/spår, 91201 cylindrar, totalt 1465149168 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   390,627,047   390,625,000   7 NTFS / exFAT / HPFS
/dev/sda2         390,627,326 1,465,147,391 1,074,520,066   5 Extended
/dev/sda5       1,457,149,952 1,465,147,391     7,997,440  82 Linux swap / Solaris
/dev/sda6         390,627,328 1,448,761,343 1,058,134,016  83 Linux
/dev/sda7       1,448,763,392 1,457,143,807     8,380,416  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 huvuden, 63 sektorer/spår, 30401 cylindrar, totalt 488397168 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63   488,392,064   488,392,002  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 203.9 GB, 203928109056 bytes
255 huvuden, 63 sektorer/spår, 24792 cylindrar, totalt 398297088 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   398,283,479   398,283,417  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        DE84C0BF84C09B81                       ntfs       Windows 7
/dev/sda5        7fe6fa2c-b19b-4582-9721-0ae07d08a5b8   swap       
/dev/sda6        f2649ed9-2167-4e66-a523-d9a89c8e2892   ext4       
/dev/sda7        986b5a6d-600b-4093-ab41-4ff080b69f00   swap       
/dev/sdb1        7d2c9875-f851-4e92-98fe-b3e60215d988   ext4       Samsung 250
/dev/sdc1        d26a2d4f-a649-4ef7-b9b2-a30441c9ad16   ext4       Annat

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,user_xattr)
/dev/sdb1        /home/brosen/Video/TV3   ext4       (rw,errors=remount-ro,user_xattr)
/dev/sdc1        /home/brosen/Video/Annat ext4       (rw,errors=remount-ro,user_xattr)


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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root f2649ed9-2167-4e66-a523-d9a89c8e2892
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root f2649ed9-2167-4e66-a523-d9a89c8e2892
  set locale_dir=($root)/boot/grub/locale
  set lang=sv_SE
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
menuentry 'Ubuntu, med Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f2649ed9-2167-4e66-a523-d9a89c8e2892
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=f2649ed9-2167-4e66-a523-d9a89c8e2892 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, med Linux 3.2.0-24-generic-pae (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f2649ed9-2167-4e66-a523-d9a89c8e2892
    echo    'Läser in Linux 3.2.0-24-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=f2649ed9-2167-4e66-a523-d9a89c8e2892 ro recovery nomodeset 
    echo    'Läser in initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, med Linux 3.2.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f2649ed9-2167-4e66-a523-d9a89c8e2892
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=f2649ed9-2167-4e66-a523-d9a89c8e2892 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, med Linux 3.2.0-24-generic (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f2649ed9-2167-4e66-a523-d9a89c8e2892
    echo    'Läser in Linux 3.2.0-24-generic ...'
    linux    /boot/vmlinuz-3.2.0-24-generic root=UUID=f2649ed9-2167-4e66-a523-d9a89c8e2892 ro recovery nomodeset 
    echo    'Läser in initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic
}
menuentry 'Ubuntu, med Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f2649ed9-2167-4e66-a523-d9a89c8e2892
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=f2649ed9-2167-4e66-a523-d9a89c8e2892 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, med Linux 3.2.0-23-generic-pae (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f2649ed9-2167-4e66-a523-d9a89c8e2892
    echo    'Läser in Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=f2649ed9-2167-4e66-a523-d9a89c8e2892 ro recovery nomodeset 
    echo    'Läser in initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, med Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f2649ed9-2167-4e66-a523-d9a89c8e2892
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=f2649ed9-2167-4e66-a523-d9a89c8e2892 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, med Linux 3.2.0-23-generic (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f2649ed9-2167-4e66-a523-d9a89c8e2892
    echo    'Läser in Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=f2649ed9-2167-4e66-a523-d9a89c8e2892 ro recovery nomodeset 
    echo    'Läser in initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, med Linux 3.0.0-17-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f2649ed9-2167-4e66-a523-d9a89c8e2892
    linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=f2649ed9-2167-4e66-a523-d9a89c8e2892 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.0.0-17-generic-pae
}
menuentry 'Ubuntu, med Linux 3.0.0-17-generic-pae (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f2649ed9-2167-4e66-a523-d9a89c8e2892
    echo    'Läser in Linux 3.0.0-17-generic-pae ...'
    linux    /boot/vmlinuz-3.0.0-17-generic-pae root=UUID=f2649ed9-2167-4e66-a523-d9a89c8e2892 ro recovery nomodeset 
    echo    'Läser in initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-17-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f2649ed9-2167-4e66-a523-d9a89c8e2892
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root f2649ed9-2167-4e66-a523-d9a89c8e2892
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root DE84C0BF84C09B81
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
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=f2649ed9-2167-4e66-a523-d9a89c8e2892 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda7 during installation
UUID=986b5a6d-600b-4093-ab41-4ff080b69f00 none            swap    sw              0       0
# Tillagd
UUID=d26a2d4f-a649-4ef7-b9b2-a30441c9ad16 /home/brosen/Video/Annat  ext4    errors=remount-ro,user_xattr
#
# Tillagd
UUID=5ac7369d-e975-41de-a18c-7acd496362df /home/brosen/Video/TV  ext3    errors=remount-ro,user_xattr
#
UUID=7d2c9875-f851-4e92-98fe-b3e60215d988 /home/brosen/Video/TV3 ext4    errors=remount-ro,user_xattr
#

--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 551.058704376 = 591.694778368  boot/grub/core.img                             1
 550.393947601 = 590.981001216  boot/grub/grub.cfg                             1
 508.262859344 = 545.743089664  boot/initrd.img-3.0.0-17-generic-pae           1
 513.373523712 = 551.230623744  boot/initrd.img-3.2.0-23-generic               2
 468.333473206 = 502.869237760  boot/initrd.img-3.2.0-23-generic-pae           2
 513.536590576 = 551.405715456  boot/initrd.img-3.2.0-24-generic               1
 298.005531311 = 319.981002752  boot/initrd.img-3.2.0-24-generic-pae           2
 248.512275696 = 266.838024192  boot/vmlinuz-3.0.0-17-generic-pae              1
 466.117187500 = 500.489519104  boot/vmlinuz-3.2.0-23-generic                  2
 466.235141754 = 500.616171520  boot/vmlinuz-3.2.0-23-generic-pae              2
 334.971328735 = 359.672725504  boot/vmlinuz-3.2.0-24-generic                  2
 335.176548004 = 359.893078016  boot/vmlinuz-3.2.0-24-generic-pae              1
 298.005531311 = 319.981002752  initrd.img                                     2
 513.536590576 = 551.405715456  initrd.img.old                                 1
 335.176548004 = 359.893078016  vmlinuz                                        1
 334.971328735 = 359.672725504  vmlinuz.old                                    2

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt

```

---

### Post by wilee-nilee on 2012-05-13
First thing though before you do anything run this in ubuntu and see if it sets up the windows boot.
  
```
sudo update-grub
```A auto repair in Windows while grub is in the mbr generally does not work, I assume this attempt was to see if windows will boot.

Try in the windows recovery terminal and see if windows will boot on its own.

```
bootrec.exe /fixmbr
```Here is a whole set to repair the windows boot if needed.

```
[FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /fixmbr[/SIZE][/FONT]
chkdsk /r  
[FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /FixBoot (#updates PBR partition boot) [/SIZE][/FONT] 
[FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /ScanOs [/SIZE][/FONT] 
[FONT=Verdana, sans-serif][SIZE=1]BootRec.exe /RebuildBcd [/SIZE][/FONT] 
 
```The script looks a little funny in the lists at the top, if it was me I would purge and reinstall grub, and not use the gui based grub fixers in this situation. This link defaults to a how to chroot in from a live cd and below it  is the purge and reinstall commands. Notice the raid reference in the default you don't have a raid so  treat accordingly. So chroot in then run the purge and reinstall.

[https://help.ubuntu.com/community/Grub2/Installing#ChRoot](https://help.ubuntu.com/community/Grub2/Installing#ChRoot)

So I would reload the windows bootloader to see if windows does boot, the chkdsk will run on the reboot let it run. If windows boots follow the chroot and purge and reinstall grub.

---

### Post by Bo Rosén on 2012-05-13
Thanks for the detailed help, much appreciated. Unfortunately, nothing helped so in the end I decided it would probably be quicker to re-install windows.

---

### Post by wilee-nilee on 2012-05-13
> **Bo Rosén said:**
> Thanks for the detailed help, much appreciated.  Unfortunately, nothing helped so in the end I decided it would probably  be quicker to re-install windows.

Ah, oh well, I always clone my W7 setup on a fresh install after fully updated, the windows updates are slow.

---

