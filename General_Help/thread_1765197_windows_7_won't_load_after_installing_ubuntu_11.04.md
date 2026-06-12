---
title: "windows 7 won't load after installing ubuntu 11.04"
date: 2011-05-22
forum: General Help
---

### Post by geppo80 on 2011-05-22
Hi all, first.

I've got this issue.
The history of this notebook is:

came up with windows vista preinstalled with a recovery partition.

Installed windows 7 without removing the vista recovery partition. While doing this partitioned the hd in this way:

/dev/sda1 recovery
/dev/sda2 windows 7
/dev/sda3 backup space (ntfs)

then..

installed ubuntu 11.04 from cd.

removed /dev/sda3 partition and from this i've made:
/dev/sda5 backup space (fat32) (formatted but not mounted in ubuntu installation)
/dev/sda6 / (logical)
/dev/sda7 /home (logical)
/dev/sda8 swap (logical)

device boot loader (grub) on MBR.

After installation ubuntu works, windows 7 is in the grub list but after choosing it screen comes back to grub list. Vista recovery partition (but from here i cannot fix mbr.. is a vaio thing) is in this list as well and it starts.

this is my boot info script 6.0 logs:

[PHP]
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda2 
                       and looks at sector 588430424 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disco /dev/sda: 320.1 GB, 320072933376 byte
255 testine, 63 settori/tracce, 38913 cilindri, totale 625142448 settori
UnitÃ  = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    18,272,255    18,270,208  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     18,272,256   420,341,751   402,069,496   7 NTFS / exFAT / HPFS
/dev/sda3         420,341,758   625,141,759   204,800,002   5 Extended
/dev/sda5         420,341,760   586,078,207   165,736,448   b W95 FAT32
/dev/sda6         586,080,256   605,609,983    19,529,728  83 Linux
/dev/sda7         605,612,032   621,234,175    15,622,144  83 Linux
/dev/sda8         621,236,224   625,141,759     3,905,536  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        9670FE5270FE3917                       ntfs       Recovery
/dev/sda2        92C65C38C65C1EB3                       ntfs       
/dev/sda5        BE1E-8289                              vfat       <µÁýçE'ó&#142;
/dev/sda6        7c9f72fb-24fa-4291-b7d0-0c7d41817ef2   ext4       
/dev/sda7        7f7d2327-21a9-47e0-8fa4-ac9f9d024129   ext4       
/dev/sda8        ae197cb7-decc-4374-8af7-9663334187e8   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /home                    ext4       (rw,commit=0)


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
search --no-floppy --fs-uuid --set=root 7c9f72fb-24fa-4291-b7d0-0c7d41817ef2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 7c9f72fb-24fa-4291-b7d0-0c7d41817ef2
set locale_dir=($root)/boot/grub/locale
set lang=it_IT
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
menuentry 'Ubuntu, con Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 7c9f72fb-24fa-4291-b7d0-0c7d41817ef2
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=7c9f72fb-24fa-4291-b7d0-0c7d41817ef2 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, con Linux 2.6.38-8-generic (modalitÃ  ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 7c9f72fb-24fa-4291-b7d0-0c7d41817ef2
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=7c9f72fb-24fa-4291-b7d0-0c7d41817ef2 ro single 
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
    search --no-floppy --fs-uuid --set=root 7c9f72fb-24fa-4291-b7d0-0c7d41817ef2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 7c9f72fb-24fa-4291-b7d0-0c7d41817ef2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9670FE5270FE3917
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 92C65C38C65C1EB3
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
UUID=7c9f72fb-24fa-4291-b7d0-0c7d41817ef2 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=7f7d2327-21a9-47e0-8fa4-ac9f9d024129 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=ae197cb7-decc-4374-8af7-9663334187e8 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 280.585517883 = 301.276405760  boot/grub/core.img                             1
 281.864501953 = 302.649704448  boot/grub/grub.cfg                             1
 281.219264984 = 301.956886528  boot/initrd.img-2.6.38-8-generic               2
 280.634151459 = 301.328625664  boot/vmlinuz-2.6.38-8-generic                  1
 281.219264984 = 301.956886528  initrd.img                                     2
 280.634151459 = 301.328625664  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 0b fe ff ff 02 00  00 00 00 f0 e0 09 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 f0  e0 09 00 08 2a 01 00 00  |............*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

[/PHP]
  

any help is welcome :)

---

### Post by garvinrick4 on 2011-05-22
You put grub into sda2 instead of sda.
Use your Windows disk and with a couple of commands like in this link put Windows grub
back in place.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 

Now with Ubuntu install Cd boot from and use Try UBuntu and then open a terminal
and copy and paste these.
```
sudo mount /dev/sda6 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
```sudo reboot into Ubuntu and in a terminal:
```
sudo update-grub
```Will put windows in grub-config and as a menu entry in grub also. Done takes about 15 minutes total.

---

### Post by oldfred on 2011-05-22
The fixboot command in windows should repair the sda2 Windows boot sector that has grub2's boot loader, but has to to have windows.

If you do not have windows repair console you can repair it with testdisk also from a backup it has.
Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by geppo80 on 2011-05-23
ok.

I downloaded the windows 7 repair cd (64 bit).. though it is telling me that the repair cd is not the same version of the operative system installed.

I'll try with the 32 bit version..

if it fails again i'll go with the vista 32 bit one, that is the OS originally preinstalled.

by the way i did NOT install grub on sda2.. it installed there by its self, I choose /dev/sda on installation .

---

### Post by Quackers on 2011-05-23
The repair disc has to be the same architecture as the installation (32 bit/64 bit) to fix it.
Regarding grub, somewhere along the line you have told grub to install to sda2. Maybe it wasn't there originally. It could have happened trying to fix the problem. Grub installation defaults to /dev/sda and that only changes with user input.

---

### Post by geppo80 on 2011-05-23
> **garvinrick4 said:**
> Done takes about 15 minutes total.

it took a bit more but it worked :)


@Quackers: I'm more than secure I choose /dev/sda on the installation, but.. ok all is fine now :)

thanks all :)

---

### Post by vergenzt on 2011-06-10
:( Could you please post the section of your grub.cfg that has the menuentry for Windows 7?  I've tried reinstalling grub exactly as detailed above and it still just loops back to the Grub menu when I select Windows 7.  My problem sounds identical to yours.

Here's what mine looks like:

```
[Ubuntu 11.04, recovery mode, memtest, etc.]...

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root A0D45669D4564228
	chainloader +1
}

... [continues on with the recovery partition, etc.]
```

---

### Post by oldfred on 2011-06-10
@[vergenzt]("http://ubuntuforums.org/member.php?find=lastposter&t=1765197")
This thread is solved, so not many will look at it. If the solutions above have not solved your problem & boot issues are almost always unique, then start a new thread & post the full boot_info script. You may just need more windows repairs or others fixes.

---

