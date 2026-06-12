---
title: "Grub- error no such disk"
date: 2011-09-24
forum: General Help
---

### Post by sansa dude on 2011-09-24
hi

My desktop computer has 3 separate hard drives in it each with their own OS. 250gb SATA with Ubuntu 11.04, 300gb IDE with Windows 7, and a 80gb IDE with Windows XP. 

I can boot into Ubuntu fine, and when I use GRUB Customizer to add the two Windows drives everything is fine. I can see the added options to boot from them in the grub menu but when I click on the windows options they give me errors that there is no such disk. The BIOS reads the disks fine and I can access them in Windows I just can't boot from them in the GRUB menu. 

If I disconnect the Ubuntu drive I can boot from the windows disks without issue, so the MBR is not an issue from what I can see.  

Any suggestions on a solution?

---

### Post by Rubi1200 on 2011-09-24
Hi,
please post the results of the boot info script when all 3 drives are attached so we can see what is going on.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by sansa dude on 2011-09-24
Attached is the RESULTS.txt you specified.

---

### Post by Rubi1200 on 2011-09-24
For those concerned:

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /ntdetect.com

sdc1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586114704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   586,099,394   586,099,332   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   156,232,124   156,232,062   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *          2,048   486,563,839   486,561,792  83 Linux
/dev/sdc2         486,565,886   488,396,799     1,830,914   5 Extended
/dev/sdc5         486,565,888   488,396,799     1,830,912  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3412022B1201F2A2                       ntfs       
/dev/sdb1        868C74808C746D15                       ntfs       80gb disk
/dev/sdc1        82b7030a-8d9c-4f8a-a2e9-f778b90b40f8   ext4       
/dev/sdc5        b46b8e1e-9c1a-4666-8e30-6f6ea21fbe1b   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


================================ sdb1/boot.ini: ================================

--------------------------------------------------------------------------------
[Boot Loader]
Timeout=10
Default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[Operating Systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="XXCLONE: (Cloned Volume) [d:0,p:1] \WINDOWS" /fastdetect /NoExecute=OptIn
--------------------------------------------------------------------------------

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root 82b7030a-8d9c-4f8a-a2e9-f778b90b40f8
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root 82b7030a-8d9c-4f8a-a2e9-f778b90b40f8
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos1)'
search --no-floppy --fs-uuid --set=root 82b7030a-8d9c-4f8a-a2e9-f778b90b40f8
insmod jpeg
if background_image /boot/grub/Mac-OS-X-Lion-Wallpaper.jpg; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_os-prober_proxy ###
menuentry "Windows 7 (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 3412022B1201F2A2
    chainloader +1
}
menuentry "Windows XP Home Edition (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sdb,msdos1)'
    search --no-floppy --fs-uuid --set=root 868C74808C746D15
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/10_os-prober_proxy ###

### BEGIN /etc/grub.d/20_linux_proxy ###
menuentry "Ubuntu 11.04 64-bit, with Linux 2.6.38-11-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdc,msdos1)'
    search --no-floppy --fs-uuid --set=root 82b7030a-8d9c-4f8a-a2e9-f778b90b40f8
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=82b7030a-8d9c-4f8a-a2e9-f778b90b40f8 ro  splash quiet vga=795  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
### END /etc/grub.d/20_linux_proxy ###

### BEGIN /etc/grub.d/30_linux_xen ###
### END /etc/grub.d/30_linux_xen ###
--------------------------------------------------------------------------------

=============================== sdc1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=82b7030a-8d9c-4f8a-a2e9-f778b90b40f8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b46b8e1e-9c1a-4666-8e30-6f6ea21fbe1b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 200.135513306 = 214.893871104  boot/grub/core.img                             1
  75.187725067 = 80.732205056   boot/grub/grub.cfg                             1
  76.270778656 = 81.895124992   boot/initrd.img-2.6.38-10-generic              2
  78.050045013 = 83.805597696   boot/initrd.img-2.6.38-11-generic              2
  74.630435944 = 80.133820416   boot/initrd.img-2.6.38-8-generic               2
  91.157539368 = 97.879662592   boot/vmlinuz-2.6.38-10-generic                 2
  76.719726562 = 82.377179136   boot/vmlinuz-2.6.38-11-generic                 2
 200.133792877 = 214.892023808  boot/vmlinuz-2.6.38-8-generic                  1
  78.050045013 = 83.805597696   initrd.img                                     2
  76.270778656 = 81.895124992   initrd.img.old                                 2
  76.719726562 = 82.377179136   vmlinuz                                        2
  91.157539368 = 97.879662592   vmlinuz.old                                    2

========= Devices which don't seem to have a corresponding hard drive: =========

sdd sde sdf sdg 

=============================== StdErr Messages: ===============================

unlzma: Decoder error


```

---

### Post by sansa dude on 2011-09-24
From what I know the output looks like it should be.

---

