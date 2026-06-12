---
title: "grub rescue prompt (and missing grub2 options)"
date: 2011-10-19
forum: General Help
---

### Post by RossL on 2011-10-19
Earlier today I upgraded from 11.04 to 11.10. Upon completion my boot options were:

Ubuntu 11.1
Ubuntu 11.1 (recovery)
Ubuntu 11.1
Ubuntu 11.1(recovery)
memtest
memtest (recovey)
windows 7

I attempted to remove the duplicated 11.1 entires (the second pair). After using grub customizer I reboot and found I only had the memtests and windows 7 as options. During my attempts to follow repair advice fromt eh ubuntuforums, clearly I screwed something up as now I get the "grub rescue" prompt unless I am booting 11.04 off of my USB stick.

Is there any way I can fix the grub resue problem (and then the grub2 options problem).

Any help is very much appreciated!

Oh and I ran the "boot_info_script.sh "after the grub rescue issue started. here are results:


           ```
       Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 7 for .
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 60982 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   467,716,095   467,714,048   7 NTFS / exFAT / HPFS
/dev/sda2         467,716,096   488,390,655    20,674,560   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   198,416,183   198,414,136   7 NTFS / exFAT / HPFS
/dev/sdb2         198,416,382   488,396,799   289,980,418   5 Extended
/dev/sdb5         335,124,480   482,062,335   146,937,856  83 Linux
/dev/sdb6         482,064,384   488,396,799     6,332,416  82 Linux swap / Solaris
/dev/sdb7         198,416,384   326,739,967   128,323,584  83 Linux
/dev/sdb8         326,742,016   335,116,287     8,374,272  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 8019 MB, 8019509248 bytes
20 heads, 16 sectors/track, 48947 cylinders, total 15663104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             80    15,663,103    15,663,024   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       ba552232-83ee-ba44-a6c3-02909ddb941e   ext2       casper-rw
/dev/sda1        5BC57A4C491E7C41                       ntfs       OS
/dev/sda2        9890DD0B90DCF12C                       ntfs       RECOVERY
/dev/sdb1        12DEDEA9DEDE83FF                       ntfs       DATA
/dev/sdb5        7839a0b0-2935-43fc-8b50-c11f9e8458f3   ext4       
/dev/sdb6        5d236169-ba0b-4cbb-94f0-0daf1c121184   swap       
/dev/sdb7        20b71c03-0f4a-4c00-b368-c4bab9f20ab5   ext4       
/dev/sdb8        12ab3c65-c79e-41ce-aeae-f4eee93abfd7   swap       
/dev/sdc1        1DFB-3760                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /mnt                     ext4       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 7839a0b0-2935-43fc-8b50-c11f9e8458f3
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=800x600
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos5)'
search --no-floppy --fs-uuid --set=root 7839a0b0-2935-43fc-8b50-c11f9e8458f3
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Ubuntu, with Linux 2.6.38-10-generic-pae" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 7839a0b0-2935-43fc-8b50-c11f9e8458f3
    linux    /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=7839a0b0-2935-43fc-8b50-c11f9e8458f3 ro splash vga=789  quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic-pae
}
menuentry "Ubuntu, with Linux 2.6.38-10-generic-pae (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 7839a0b0-2935-43fc-8b50-c11f9e8458f3
    echo    'Loading Linux 2.6.38-10-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-10-generic-pae root=UUID=7839a0b0-2935-43fc-8b50-c11f9e8458f3 ro single splash vga=789
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic-pae
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 7839a0b0-2935-43fc-8b50-c11f9e8458f3
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos5)'
    search --no-floppy --fs-uuid --set=root 7839a0b0-2935-43fc-8b50-c11f9e8458f3
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 5BC57A4C491E7C41
    chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=7839a0b0-2935-43fc-8b50-c11f9e8458f3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=5d236169-ba0b-4cbb-94f0-0daf1c121184 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 163.939735413 = 176.028950528  boot/grub/core.img                             1
 163.963947296 = 176.054947840  boot/grub/grub.cfg                             1
 169.441932678 = 181.936889856  boot/initrd.img-2.6.35-22-generic-pae          2
 170.637561798 = 183.220686848  boot/initrd.img-2.6.35-23-generic-pae          2
 174.456054688 = 187.320762368  boot/initrd.img-2.6.35-28-generic-pae          2
 160.680271149 = 172.529127424  boot/initrd.img-2.6.38-10-generic-pae          2
 159.995117188 = 171.793448960  boot/initrd.img-2.6.38-8-generic-pae           2
 163.935806274 = 176.024731648  boot/vmlinuz-2.6.35-22-generic-pae             1
 163.943920135 = 176.033443840  boot/vmlinuz-2.6.35-23-generic-pae             1
 164.053932190 = 176.151568384  boot/vmlinuz-2.6.35-28-generic-pae             1
 160.354923248 = 172.179787776  boot/vmlinuz-2.6.38-10-generic-pae             1
 172.546325684 = 185.270206464  boot/vmlinuz-2.6.38-8-generic-pae              1
 160.680271149 = 172.529127424  initrd.img                                     2
 159.995117188 = 171.793448960  initrd.img.old                                 2
 160.354923248 = 172.179787776  vmlinuz                                        1
 172.546325684 = 185.270206464  vmlinuz.old                                    1

=========================== sdb7/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd1,msdos7)'
search --no-floppy --fs-uuid --set=root 20b71c03-0f4a-4c00-b368-c4bab9f20ab5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos7)'
  search --no-floppy --fs-uuid --set=root 20b71c03-0f4a-4c00-b368-c4bab9f20ab5
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+_proxy ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 20b71c03-0f4a-4c00-b368-c4bab9f20ab5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root 20b71c03-0f4a-4c00-b368-c4bab9f20ab5
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 5BC57A4C491E7C41
    chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###

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

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=20b71c03-0f4a-4c00-b368-c4bab9f20ab5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=12ab3c65-c79e-41ce-aeae-f4eee93abfd7 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 118.738552094 = 127.494549504  boot/grub/core.img                             1
 138.745773315 = 148.977139712  boot/grub/grub.cfg                             1
 138.018554688 = 148.196294656  boot/initrd.img-2.6.38-11-generic-pae          2
 138.123622894 = 148.309110784  boot/initrd.img-3.0.0-12-generic-pae           2
  95.651798248 = 102.705336320  boot/vmlinuz-2.6.38-11-generic-pae             1
 137.011276245 = 147.114737664  boot/vmlinuz-3.0.0-12-generic-pae              1
 138.018554688 = 148.196294656  initrd.img.old                                 2
 137.011276245 = 147.114737664  vmlinuz                                        1
  95.651798248 = 102.705336320  vmlinuz.old                                    1

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected
```

s:

---

### Post by RossL on 2011-10-19
Is there anyway to recover my system to the way it was? either the doubled up 11.10 loaders or even just back to when win7 and 11.04 worked perfectly? I really would like a lot of the data on the windows 7 partition.

---

### Post by drs305 on 2011-10-19
Let's try a simple way first. 

At the grub prompt, run this command:
```

ls (hd1,7)/  # Do you see vmlinuz and initrd.img ?
ls (hd1,7)/boot # Does it see the 3.0 kernel?

```

If so:
```
set prefix=(hd1,7)/boot/grub
set root=(hd1,7)
insmod linux
linux (hd1,7)/vmlinuz root=/dev/sdb7 ro
initrd (hd1,7)/initrd.img
boot
```
If it boots, run:
```
sudo update-grub
```

Actually I lied. The simple thing to try would be to change the BIOS to boot sdb first. It should then boot to 11.04 and you should have that and Windows available. But if you can get 11.10 running with the above it would probably be better.

---

### Post by RossL on 2011-10-19
nevermind I forgot the /, Im running through your steps now. Ill edit when I get to end

---

### Post by drs305 on 2011-10-19
OK. I added a line at the end of the previous post. See if you can change the BIOS to sdb and boot from that drive to 11.04.

Also, the "ls" commands ends with a /, but your USB probably isn't Grub 1.99. Do you have a Natty or Oneiric Live CD (Grub 1.99)?

---

### Post by RossL on 2011-10-19
everything worked up until 

```

grub rescue> insmod linux
error: incompatible license.
grub rescue> 

```

---

### Post by RossL on 2011-10-19
I can only move Notebook Hard Drive above USB Diskette on Key/USB Hard Disk. I dont see an option to specify sdb

---

### Post by drs305 on 2011-10-19
> **RossL said:**
> everything worked up until 

```

grub rescue> insmod linux
error: incompatible license.
grub rescue> 

```

You can try to run it as
```
insmod (hd1,7)/boot/grub/linux.mod
```
but I'm not sure if that will work. I've seen this error message before and suspect it has something to do with different grub versions; I'm not sure though.

---

### Post by drs305 on 2011-10-19
I'll add another way to go about this since you seem to be having problmes at the grub rescue prompt and I'm awaiting your response.

Boot to 11.04 however you can get there.
Confirm it is using Grub 1.99:
```
grub-install -v
```

We can chroot into your 11.10 installation:
```
sudo mount /dev/sdb7 /mnt
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/$i;  done
sudo chroot /mnt/

```

You will now be at a root prompt and no longer need "sudo". We are going to be installing Grub 2 to sda even though your 11.10 is on sdb. From what you wrote, you can't change the boot order to sdb, so we'll try it this way.
```
grub-install /dev/sda
update-grub
grep "menuentry" /boot/grub/grub.cfg  # You should see several linux entries, memtest and hopefully Windows
exit

```
You should now be back in your 11.04 OS.
Unmount and try rebooting:
```
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt/$i ; done
```

We are not accomplishing all the commands to purge and reinstall Grub2, since we just need to regenerate the grub.cfg file and make sure sda's MBR is pointing to the sdb7 partition.

---

### Post by RossL on 2011-10-19
sorry i had to leave my computer for a minute. I'm booting into 11.04 off of the USB now. The other command gave the same error.

when I grep for menuentry, I only get the memory tests and windows 7, but when i ran update-grub it found memtest, windows 7, windows vista (???), and ubuntu 11.04 (on sdb5)

---

### Post by RossL on 2011-10-19
Good news, I have my Grub2 back. (This is very good news to me)
Bad news, Still just memory test (times 2) and windows 7 as options

---

### Post by drs305 on 2011-10-19
So you are seeing your 11.10 Grub menu and you ran the update-grub command while in chroot?

When you ran the "ls" commands earlier, did they find "vmlinuz" and "initrd.img" in (hd1,7)/ and the full kernel and initrd.img in (hd1,7)/boot?

If so, and the menu appears, it means that the Grub presets should be loaded and you may be able to just load the kernel and initrd image:
```
linux /vmlinuz root=/dev/sdb7 ro
initrd /initrd.img
boot
```

If you are still not able to boot, please rerun the boot info script.

---

### Post by RossL on 2011-10-19
should i still be on the 11.04 from the USB and chroot to 11.1? or should i be at the grub prompt from hitting "c" when the options come up?

---

### Post by drs305 on 2011-10-19
> **RossL said:**
> should i still be on the 11.04 from the USB and chroot to 11.1?

Not if you have already done that once. My impression was that you had done the chroot, rebooted without the USB or CD, and had gotten the 11.10 Grub menu but without any Linux entries.

---

### Post by RossL on 2011-10-19
that is correct, so i should be at the grub2 menu and hit c to get to its prompt

---

### Post by drs305 on 2011-10-19
> **RossL said:**
> that is correct, so i should be at the grub2 menu and hit c to get to its prompt

Yes, and then run the commands in post 12 if the 'ls' commands above located the shortcuts. I was concerned that update-grub is not adding linux to your menu but I see now that your /etc/grub.d/10_linux file is either corrupt, missing or not executable.

Try booting from the Grub prompt, if that doesn't work we will have to chroot again and purge/reinstall grub to make sure the 10_linux file gets put back onto your system in working order.

---

### Post by RossL on 2011-10-19
Thank you! I got into 11.10 and now my Grub2 includes options for 11.1, 11.1 (Recovery), Mem, Mem (serial consol), and windows 7 (and when I pulled up grub customizer the linux_10 had been unchecked accidentally, so i added that back in)

---

### Post by drs305 on 2011-10-19
> **RossL said:**
> Thank you! I got into 11.10 and now my Grub2 includes options for 11.1, 11.1 (Recovery), Mem, Mem (serial consol), and windows 7 (and when I pulled up grub customizer the linux_10 had been unchecked accidentally, so i added that back in)

That would do it!

Please mark this SOLVED via the 'Thread Tools' link near the top right of the first post.

Happy Ubuntu-ing !

---

### Post by RossL on 2012-04-30
Wish I could mark this as solved twice. I made the same mistake of picking the wrong option in grub customizer again when converting from 11.10 to 12.04. Thanks again!

(this time the ls and boot commands in like post #4 worked perfectly)

---

