---
title: "os-prober segmentation fault"
date: 2012-07-17
forum: General Help
---

### Post by marianoa on 2012-07-17
Hi everybody,

lately I've been having problems with update-grub. These problems are actually
related to os-prober since if I remove the executable bit to 30_os-prober in /etc/grub.d
then update-grub ignores the Windows installation and runs fine.

When I run 
```

sudo os-prober

```
 
I get
```

Segmentation fault (core dumped)
rmdir: rimozione di "/var/lib/os-prober/mount" non riuscita: Dispositivo o risorsa occupata
Segmentation fault (core dumped)
rmdir: rimozione di "/var/lib/os-prober/mount" non riuscita: Dispositivo o risorsa occupata
Segmentation fault (core dumped)
rmdir: rimozione di "/var/lib/os-prober/mount" non riuscita: Dispositivo o risorsa occupata

```
 which means failed removing  "/var/lib/os-prober/mount": resource or device busy

I'm using Ubuntu Precise.

Thanks

---

### Post by oldfred on 2012-07-17
I do not know if it is an os-prober issue or a partition issue? Os-prober scans entire system looking for systems so it needs to mount everything.

We could uninstall & reinstall grub, but first lets run boot info script and see if it also shows any partitions that cannot mount. 

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

You can download and run this. It also runs script as part of BootInfo & does give a bit more info on booting issues.
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by marianoa on 2012-07-18
Hi odlfred,

Thanks for trying to help me. Here's the output of bootinfoscript

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 testine, 63 settori/tracce, 38913 cilindri, totale 625142448 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    27,262,975    27,260,928  27 Hidden NTFS (Recovery Environment)
/dev/sda2    *     27,262,976    27,467,775       204,800   7 NTFS / exFAT / HPFS
/dev/sda3          27,467,776   352,547,503   325,079,728   7 NTFS / exFAT / HPFS
/dev/sda4         352,548,862   625,141,759   272,592,898   5 Extended
/dev/sda5         352,548,864   613,984,255   261,435,392  83 Linux
/dev/sda6         613,986,304   625,141,759    11,155,456  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        D85EBEC45EBE9AA8                       ntfs       Recovery
/dev/sda2        923C58D73C58B845                       ntfs       System Reserved
/dev/sda3        78AE5B55AE5B0B50                       ntfs       
/dev/sda5        51c99d8d-92cf-4fb6-bc16-519097a87fae   ext4       
/dev/sda6        da934688-062d-4e0c-ae8b-0bae4edfefb0   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /tmp/BootInfo-jsSxdN74/sda1 fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda3        /media/78AE5B55AE5B0B50  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set=root 51c99d8d-92cf-4fb6-bc16-519097a87fae
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 51c99d8d-92cf-4fb6-bc16-519097a87fae
  set locale_dir=($root)/boot/grub/locale
  set lang=it_IT
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
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
menuentry 'Ubuntu, con Linux 3.2.0-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 51c99d8d-92cf-4fb6-bc16-519097a87fae
    linux    /boot/vmlinuz-3.2.0-26-generic-pae root=UUID=51c99d8d-92cf-4fb6-bc16-519097a87fae ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-26-generic-pae
}
menuentry 'Ubuntu, con Linux 3.2.0-26-generic-pae (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 51c99d8d-92cf-4fb6-bc16-519097a87fae
    echo    'Caricamento Linux 3.2.0-26-generic-pae...'
    linux    /boot/vmlinuz-3.2.0-26-generic-pae root=UUID=51c99d8d-92cf-4fb6-bc16-519097a87fae ro recovery nomodeset 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-3.2.0-26-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, con Linux 3.2.0-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 51c99d8d-92cf-4fb6-bc16-519097a87fae
    linux    /boot/vmlinuz-3.2.0-25-generic-pae root=UUID=51c99d8d-92cf-4fb6-bc16-519097a87fae ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-25-generic-pae
}
menuentry 'Ubuntu, con Linux 3.2.0-25-generic-pae (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 51c99d8d-92cf-4fb6-bc16-519097a87fae
    echo    'Caricamento Linux 3.2.0-25-generic-pae...'
    linux    /boot/vmlinuz-3.2.0-25-generic-pae root=UUID=51c99d8d-92cf-4fb6-bc16-519097a87fae ro recovery nomodeset 
    echo    'Caricamento ramdisk iniziale...'
    initrd    /boot/initrd.img-3.2.0-25-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 51c99d8d-92cf-4fb6-bc16-519097a87fae
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 51c99d8d-92cf-4fb6-bc16-519097a87fae
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root D85EBEC45EBE9AA8
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 923C58D73C58B845
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
UUID=51c99d8d-92cf-4fb6-bc16-519097a87fae /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=da934688-062d-4e0c-ae8b-0bae4edfefb0 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 200.819992065 = 215.628824576  boot/grub/core.img                             1
 239.125995636 = 256.759582720  boot/grub/grub.cfg                             1
 261.045898438 = 280.295899136  boot/initrd.img-3.2.0-25-generic-pae           2
 254.896743774 = 273.693294592  boot/initrd.img-3.2.0-26-generic-pae           3
 178.691200256 = 191.868215296  boot/vmlinuz-3.2.0-25-generic-pae              1
 234.691192627 = 251.997749248  boot/vmlinuz-3.2.0-26-generic-pae              2
 254.896743774 = 273.693294592  initrd.img                                     3
 261.045898438 = 280.295899136  initrd.img.old                                 2
 234.691192627 = 251.997749248  vmlinuz                                        2
 178.691200256 = 191.868215296  vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

xz: (stdin): I dati compressi sono danneggiati
./bootinfoscript: riga 2070: 16395 Errore di segmentazione (core dump creato) umount "${mountname}"
./bootinfoscript: riga 2070: 16397 Errore di segmentazione (core dump creato) umount -l "${mountname}"
```

---

### Post by oldfred on 2012-07-18
Boot script looks normal.

You do show some bits of wubi still in your Windows 7 partition. Perhaps it issue is not finding root.disk but seeing the wubi files?

the only issue at the end of the script:
> xz: (stdin): I dati compressi sono danneggiati
./bootinfoscript: riga 2070: 16395 Errore di segmentazione (core dump creato) umount "${mountname}"
./bootinfoscript: riga 2070: 16397 Errore di segmentazione (core dump creato) umount -l "${mountname}"

Which is unmounting something, but it did not show any issue mounting anything and does not say what the issue is. But it looks similar to the os-prober error.

I actually turn os-prober off on my system and add entries to 40_custom for my other systems. I have a lot of older versions of Ubuntu that I do not normally boot, but have not deleted yet, so I do not want all those in my menu.

We can totally uninstall grub2 & reinstall, but I do not think that is the issue since script seemed to also have issue. And script did not say which partition might be the issue. If it had shown a specific partition I would run chkdsk from Windows on all the NTFS partitions and from a liveCD run e2fsck on the Linux partition.

---

### Post by marianoa on 2012-07-19
In the end I unistalled os-prober and added the menu entry by hand in 40_custom

Thanks for helping

---

### Post by oldfred on 2012-07-19
If you just uninstalled it, it may get reinstalled on an update to grub2.

I turn it off in grub by adding this. 

gksu gedit /etc/default/grub

GRUB_DISABLE_OS_PROBER=true

---

