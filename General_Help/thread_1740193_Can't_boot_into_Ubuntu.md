---
title: "Can't boot into Ubuntu"
date: 2011-04-26
forum: General Help
---

### Post by MegaLoler on 2011-04-26
I was on Ubuntu last night when the power went out.  I restarted the computer and it went into grub rescue mode.  I don't think it was the power outtage that caused it though, because I remember earlier that day I deleted some old partitions in gparted an they were giving strange errors.  I can't remember exacly what but it said something about overlapping cylinders I think.

Anyway, I burned a SystemRescueCD CD and gparted does not detect any partitions at all.  I looked at TestDisk but i don't think it is saying anything is wrong.  It detects all of my partitions and my files fine as far as I can tell.  I can even mount the different partitions and access them perfectly fine.  However the Windows partition, which is marked as the primary bootable, if that has to do with anything, only mounts as read only, if that has to do with anything.

I also used the SystemRescueCD's option to boot a linux kernel installed on the disk, and that worked - except it booted CrunchBang instead of Ubuntu.  I would be happy if there was an option to choose just which kernel to boot.

So all I want to do is boot into Ubuntu.  At least that, anyway.  Even if it doesn't fix the problem.
Can anyone help, please?  Thanks

---

### Post by Dutch70 on 2011-04-26
If you've got overlapping partitions you could have some serious problems & your files may never be safe, but it's your system. :)
So we'll need to see your boot info script. I'm not sure it will help though.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] [ /CODE] tags. 
Do not skip this step or you will lose the formatting & I doubt if anyone will even look at it.

---

### Post by MegaLoler on 2011-04-26
Thank you for your response.

Here are the results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #12 for (,msdos12)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  CrunchBang Linux statler
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda3 and 
                       looks at sector 116394752 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #3 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    94,751,359    94,751,297   7 HPFS/NTFS
/dev/sda2          94,752,768   114,242,087    19,489,320  83 Linux
/dev/sda3         114,243,584   129,079,295    14,835,712  83 Linux
/dev/sda4         129,079,314   160,842,779    31,763,466   f W95 Ext d (LBA)
/dev/sda5         129,081,344   129,853,423       772,080  82 Linux swap / Solaris
/dev/sda6         129,853,458   131,475,937     1,622,480  82 Linux swap / Solaris
/dev/sda7         131,476,086   136,359,717     4,883,632  83 Linux
/dev/sda8         136,359,783   136,713,126       353,344  82 Linux swap / Solaris
/dev/sda9         147,189,760   160,143,359    12,953,600  83 Linux
/dev/sda10        160,145,408   160,835,567       690,160  82 Linux swap / Solaris

/dev/sda4 ends after the last sector of /dev/sda

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       f48a32c8-6b02-4f00-910e-a92eb81252fe   swap                                     
/dev/sda1        5E7CF2FC7CF2CE31                       ntfs                                     
/dev/sda2        2341437f-42d3-49f0-a310-f7c52448633e   ext3                                     
/dev/sda3        b9fb82ec-e643-4d9c-82e3-252c41cea53a   ext4                                     
/dev/sda4: PTTYPE="dos" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0xf" PART_ENTRY_NUMBER="4" 
/dev/sda5        8435cd6b-a6ea-4f29-912e-c600e5a014c1   swap                                     
/dev/sda6        8fe8d7c5-7cd8-4b81-9309-84161d95eecd   swap                                     
/dev/sda7        2854963d-21fb-446e-ac6e-10e40d4752f6   ext3                                     
/dev/sda8        6215a975-a9b1-4c53-af00-4afa351cf4f4   swap                                     
/dev/sda9        8375fb21-212c-482c-b683-7937450f8985   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
none             /                        aufs       (rw,noatime,si=626f2722)
/dev/sr0         /livemnt/boot            iso9660    (ro,relatime,mode=0644)
/dev/loop0       /livemnt/squashfs        squashfs   (ro,relatime)
/dev/sda1        /mnt                     ntfs       (ro)
/dev/sda3        /mnt                     ext4       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos12)'
search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos12)'
search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=b9fb82ec-e643-4d9c-82e3-252c41cea53a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=b9fb82ec-e643-4d9c-82e3-252c41cea53a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b9fb82ec-e643-4d9c-82e3-252c41cea53a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b9fb82ec-e643-4d9c-82e3-252c41cea53a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5e7cf2fc7cf2ce31
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "CrunchBang Linux, with Linux 2.6.32-5-amd64 (on /dev/sda11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set 2341437f-42d3-49f0-a310-f7c52448633e
    linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=2341437f-42d3-49f0-a310-f7c52448633e ro quiet splash
    initrd /boot/initrd.img-2.6.32-5-amd64
}
menuentry "CrunchBang Linux, with Linux 2.6.32-5-amd64 (recovery mode) (on /dev/sda11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set 2341437f-42d3-49f0-a310-f7c52448633e
    linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=2341437f-42d3-49f0-a310-f7c52448633e ro single
    initrd /boot/initrd.img-2.6.32-5-amd64
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 2854963d-21fb-446e-ac6e-10e40d4752f6
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda6
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 2b684352-1bd4-46a0-899e-9f009fd2fd7e
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=2b684352-1bd4-46a0-899e-9f009fd2fd7e ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 2b684352-1bd4-46a0-899e-9f009fd2fd7e
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=2b684352-1bd4-46a0-899e-9f009fd2fd7e ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 2b684352-1bd4-46a0-899e-9f009fd2fd7e
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=2b684352-1bd4-46a0-899e-9f009fd2fd7e ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 2b684352-1bd4-46a0-899e-9f009fd2fd7e
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=2b684352-1bd4-46a0-899e-9f009fd2fd7e ro single
    initrd /boot/initrd.img-2.6.32-24-generic
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda12 during installation
UUID=b9fb82ec-e643-4d9c-82e3-252c41cea53a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda13 during installation
UUID=8435cd6b-a6ea-4f29-912e-c600e5a014c1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   1.1GB: boot/grub/core.img
   6.7GB: boot/grub/grub.cfg
   1.1GB: boot/grub/stage2
   6.9GB: boot/initrd.img-2.6.35-22-generic
   6.9GB: boot/initrd.img-2.6.35-28-generic
   1.7GB: boot/vmlinuz-2.6.35-22-generic
   1.7GB: boot/vmlinuz-2.6.35-28-generic
   6.9GB: initrd.img
   6.9GB: initrd.img.old
   1.7GB: vmlinuz
   1.7GB: vmlinuz.old

=========================== sda2/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
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

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set 2341437f-42d3-49f0-a310-f7c52448633e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set 2341437f-42d3-49f0-a310-f7c52448633e
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
set timeout=5
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos11)'
search --no-floppy --fs-uuid --set 2341437f-42d3-49f0-a310-f7c52448633e
insmod png
if background_image /usr/share/images/desktop-base/grub-splash-crunchbang.png ; then
  set color_normal=light-gray/black
  set color_highlight=black/white
else
  set menu_color_normal=light-gray/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'CrunchBang Linux, with Linux 2.6.32-5-amd64' --class debian --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set 2341437f-42d3-49f0-a310-f7c52448633e
    echo    'Loading Linux 2.6.32-5-amd64 ...'
    linux    /boot/vmlinuz-2.6.32-5-amd64 root=UUID=2341437f-42d3-49f0-a310-f7c52448633e ro  quiet splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-amd64
}
menuentry 'CrunchBang Linux, with Linux 2.6.32-5-amd64 (recovery mode)' --class debian --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set 2341437f-42d3-49f0-a310-f7c52448633e
    echo    'Loading Linux 2.6.32-5-amd64 ...'
    linux    /boot/vmlinuz-2.6.32-5-amd64 root=UUID=2341437f-42d3-49f0-a310-f7c52448633e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-5-amd64
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5e7cf2fc7cf2ce31
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 2854963d-21fb-446e-ac6e-10e40d4752f6
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda6
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda11 during installation
UUID=2341437f-42d3-49f0-a310-f7c52448633e /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda10 during installation
UUID=56227194-4fd2-4183-89c0-713bfa5e9325 none            swap    sw              0       0
# swap was on /dev/sda5 during installation
UUID=8fe8d7c5-7cd8-4b81-9309-84161d95eecd none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=6215a975-a9b1-4c53-af00-4afa351cf4f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sda2: Location of files loaded by Grub: ===================


  48.5GB: boot/grub/core.img
  48.5GB: boot/grub/grub.cfg
  48.5GB: boot/initrd.img-2.6.32-5-amd64
  48.5GB: boot/vmlinuz-2.6.32-5-amd64
  48.5GB: initrd.img
  48.5GB: vmlinuz

=========================== sda3/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos12)'
search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos12)'
search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=b9fb82ec-e643-4d9c-82e3-252c41cea53a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=b9fb82ec-e643-4d9c-82e3-252c41cea53a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b9fb82ec-e643-4d9c-82e3-252c41cea53a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=b9fb82ec-e643-4d9c-82e3-252c41cea53a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos12)'
    search --no-floppy --fs-uuid --set b9fb82ec-e643-4d9c-82e3-252c41cea53a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 5e7cf2fc7cf2ce31
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "CrunchBang Linux, with Linux 2.6.32-5-amd64 (on /dev/sda11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set 2341437f-42d3-49f0-a310-f7c52448633e
    linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=2341437f-42d3-49f0-a310-f7c52448633e ro quiet splash
    initrd /boot/initrd.img-2.6.32-5-amd64
}
menuentry "CrunchBang Linux, with Linux 2.6.32-5-amd64 (recovery mode) (on /dev/sda11)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos11)'
    search --no-floppy --fs-uuid --set 2341437f-42d3-49f0-a310-f7c52448633e
    linux /boot/vmlinuz-2.6.32-5-amd64 root=UUID=2341437f-42d3-49f0-a310-f7c52448633e ro single
    initrd /boot/initrd.img-2.6.32-5-amd64
}
menuentry "Ubuntu 9.04 (9.04) (on /dev/sda6)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 2854963d-21fb-446e-ac6e-10e40d4752f6
    linux /boot/vmlinuz-2.6.28-11-generic root=/dev/sda6
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 2b684352-1bd4-46a0-899e-9f009fd2fd7e
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=2b684352-1bd4-46a0-899e-9f009fd2fd7e ro quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-25-generic (recovery mode) (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 2b684352-1bd4-46a0-899e-9f009fd2fd7e
    linux /boot/vmlinuz-2.6.32-25-generic root=UUID=2b684352-1bd4-46a0-899e-9f009fd2fd7e ro single
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 2b684352-1bd4-46a0-899e-9f009fd2fd7e
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=2b684352-1bd4-46a0-899e-9f009fd2fd7e ro quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, with Linux 2.6.32-24-generic (recovery mode) (on /dev/sda9)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos9)'
    search --no-floppy --fs-uuid --set 2b684352-1bd4-46a0-899e-9f009fd2fd7e
    linux /boot/vmlinuz-2.6.32-24-generic root=UUID=2b684352-1bd4-46a0-899e-9f009fd2fd7e ro single
    initrd /boot/initrd.img-2.6.32-24-generic
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda12 during installation
UUID=b9fb82ec-e643-4d9c-82e3-252c41cea53a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda13 during installation
UUID=8435cd6b-a6ea-4f29-912e-c600e5a014c1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  59.6GB: boot/grub/core.img
  65.2GB: boot/grub/grub.cfg
  59.5GB: boot/grub/stage2
  65.4GB: boot/initrd.img-2.6.35-22-generic
  65.4GB: boot/initrd.img-2.6.35-28-generic
  60.2GB: boot/vmlinuz-2.6.35-22-generic
  60.2GB: boot/vmlinuz-2.6.35-28-generic
  65.4GB: initrd.img
  65.4GB: initrd.img.old
  60.2GB: vmlinuz
  60.2GB: vmlinuz.old

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=2854963d-21fb-446e-ac6e-10e40d4752f6 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=976cfcf7-d508-43b0-b11c-4038239d1815 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  68.9GB: boot/vmlinuz-2.6.28-11-generic
  68.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  a9 93 74 72 30 a2 18 ca  0e 3f a0 b6 40 12 1c 09  |..tr0....?..@...|
00000010  17 c5 12 95 92 3f f8 fe  a1 ba c0 58 3d 30 8d 60  |.....?.....X=0.`|
00000020  f8 b0 6f 92 75 e7 04 e6  f1 16 fe 07 8b 82 a3 00  |..o.u...........|
00000030  3a 63 04 d3 80 7b 8c 2f  8f bd fb 46 e2 ee 32 22  |:c...{./...F..2"|
00000040  59 bb 04 13 86 f4 95 58  c8 94 f1 ee 29 c0 ef 0f  |Y......X....)...|
00000050  69 a3 fa d4 ce 82 80 be  05 09 0f 20 7d 6b 66 3c  |i.......... }kf<|
00000060  e3 07 70 18 78 20 f4 9a  56 2d 69 b1 34 7d 86 69  |..p.x ..V-i.4}.i|
00000070  ad 4c 0e 66 11 cd ad cf  e2 25 2d 6c 27 a2 5b 1f  |.L.f.....%-l'.[.|
00000080  9c 1e ab 6b c1 a0 2a 6e  93 fc 74 57 f2 cc 80 66  |...k..*n..tW...f|
00000090  12 2a 33 f3 16 32 04 af  3a 61 a5 f1 8a 2b d9 78  |.*3..2..:a...+.x|
000000a0  a4 df ad cb 8d 34 1f de  70 b9 c2 dc ac ee 19 02  |.....4..p.......|
000000b0  44 26 9b 42 5d 91 63 83  ab f4 ff b7 c4 9c 7b 2b  |D&.B].c.......{+|
000000c0  94 98 6b 5c 6b 6a 7c dd  78 04 21 c9 60 de 71 29  |..k\kj|.x.!.`.q)|
000000d0  79 37 c9 8b 79 3b 8b 25  07 13 f1 27 8a e4 a2 73  |y7..y;.%...'...s|
000000e0  1c 90 43 a5 20 a5 df 41  db 84 11 dc cb 37 e5 79  |..C. ..A.....7.y|
000000f0  ed f5 72 34 86 ac 01 43  7b cf 3d 86 b4 7b 18 e9  |..r4...C{.=..{..|
00000100  21 b0 e8 0b a3 af 39 f9  78 02 9f f7 c5 f5 f4 fc  |!.....9.x.......|
00000110  76 25 90 47 13 b9 d5 79  42 52 2b 8a 96 a5 d6 8f  |v%.G...yBR+.....|
00000120  f1 d6 b1 e7 de 8d 35 40  82 b5 5a 67 58 6a b3 be  |......5@..ZgXj..|
00000130  32 ca 27 eb 26 64 ec 28  0d c8 72 c9 a0 8d 4e af  |2.'.&d.(..r...N.|
00000140  fe 1e fa 0f b7 b4 3c 3d  f6 90 a0 a8 9a 36 3d db  |......<=.....6=.|
00000150  92 89 61 5c 0d a3 4e 99  c0 58 0f 8e 8e 43 9d 98  |..a\..N..X...C..|
00000160  62 86 91 26 b6 17 94 2e  95 31 bd d7 20 99 8b 1f  |b..&.....1.. ...|
00000170  a2 27 4c 81 a6 d1 b3 7f  ec fc b4 62 70 d2 b0 be  |.'L........bp...|
00000180  27 2a 5c 24 24 8b 58 35  ba eb 47 da 51 a3 18 94  |'*\$$.X5..G.Q...|
00000190  d2 e4 c2 0f b8 1f ef de  c3 9e 35 93 d8 8b f7 07  |..........5.....|
000001a0  b2 bc 11 32 94 fa 05 f4  a2 0e c3 33 a8 3c 83 72  |...2.......3.<.r|
000001b0  7a 48 dd 45 eb 34 71 85  cc cb 2e ac 05 ec 00 fe  |zH.E.4q.........|
000001c0  ff ff 82 fe ff ff ee 07  00 00 f0 c7 0b 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff ff cf  0b 00 d1 c1 18 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automatically

```

---

### Post by Dutch70 on 2011-04-26
**[COLOR="Red"]First, I strongly suggest you let someone that can help you fix this right take a look at it, and then fix it right. I may know of someone if you want to wait.[/COLOR]**

Wow! Where do I start. I'm no pro at boot scripts, but I've never seen anything like that before. First of all, grub is looking in sda12, and you do not even have an sda12. Must be one that you deleted.

sda1 says it's ntfs, windows XP file system but OS says Ubuntu 10.10 :confused:

sda3 has grub legacy installed with 10.10
[COLOR="Red"]I'm not sure you can just install Grub2 overtop of that or not, which is what the directions below would be doing.
[/COLOR]
and you've got 4 swap partitions. 

You may get it to boot by reinstalling grub to sda3. I'm really not sure how you ended up with grub legacy installed there though. So I'm not going to advise you. I will give you a link to help you try it if you want to. However, If your computer blows up, catches your house on fire and burns down your house & your winning lottery ticket, don't blame me. :)
[[COLOR="Red"]https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

If you install it to sda3, your commands to run from the live cd would be...
```
sudo mount /dev/sda3 /mnt
```
and...
```
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by MegaLoler on 2011-04-26
Grub works now!  Thanks.  But it goes to a command prompt.  How can I get into Ubuntu from there or fix grub so that it does what it used to and give a list of OS's to boot from?

Also, the terminal output from the grub-install command is this:
```
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda

```

I tried grub-setup just to see what would happen:
```
error: cannot open `/dev/fd0' while attempting to get disk size.
zsh: segmentation fault  grub-setup /dev/sda3

```

---

### Post by Dutch70 on 2011-04-26
If you mean you're getting to a command prompt such as...
```
megaloler@ubuntu ~ $ 
```
You can try typing. 
```
sudo startx
```

If you get to a GUI, run this command...
```
sudo update-grub
``` 
and it should pick up your other OS's.

Dont forget to update your system before rebooting.
```
sudo apt-get update && sudo apt-get upgrade 
```

Let us know if it works.

---

### Post by MegaLoler on 2011-04-26
Oops, I didn't mean that kind of command prompt, sorry.  I meant a grub command prompt.  It said mini bash at the top I think.  You enter grub commands.

---

### Post by Dutch70 on 2011-04-26
Try hitting (Cntl+Alt+F1) or (Cntl+Alt+F7) to see if you get an actual command prompt. If so, then do what I posted above. 
Other than that, I really don't know what to tell you.

I'll say this again, you need to back up your data if possible & fix your computer right or you will continue to have problems even if you get past this one.

---

### Post by MegaLoler on 2011-04-26
Well, those didn't work.  I think it is because the OS is not booted.  It is just still in grub.  I don't know how to get it to boot into Ubuntu from there.  I googled around and got these commands right, I think:  root (hd0, 2)   setup (hd0)      but I don't know what to do next.   I did this both in the terminal's grub command and in actual grub.  But when I reboot I still am in grub.

Sorry for being unclear.  I think you read that as I got passed grub and into Ubuntu.

---

### Post by MegaLoler on 2011-04-26
Okay, so I found out that whenever I do```
 configfile (hd0,2)/boot/grub/menu.lst
``` it says file not found.  [s]But it is definitely there[/s].
EDIT: Okay, it ISN'T there...  I accidentally cd'd to the wrong partition when I checked.  I wonder if I could create one?
 I also found that whenever I load the kernel with ```
kernel (hd0,2)/boot/vmlinuz-2.6.35-28-generic
boot
```  It loads it but doesn't get very far before it hangs.

---

### Post by Dutch70 on 2011-04-26
I believe menu.lst from Grub Legacy was replace with grub.cfg in Grub2. That's all I got.

---

### Post by Quackers on 2011-04-26
Gparted won't recognise any partitions because your extended partition extends beyond the end of the disc! Not possible :-)
```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, [COLOR="Red"]total 160836480[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    94,751,359    94,751,297   7 HPFS/NTFS
/dev/sda2          94,752,768   114,242,087    19,489,320  83 Linux
/dev/sda3         114,243,584   129,079,295    14,835,712  83 Linux
/dev/sda4         129,079,314   [COLOR="Red"]160,842,779[/COLOR]    31,763,466   f W95 Ext d (LBA)
/dev/sda5         129,081,344   129,853,423       772,080  82 Linux swap / Solaris
/dev/sda6         129,853,458   131,475,937     1,622,480  82 Linux swap / Solaris
/dev/sda7         131,476,086   136,359,717     4,883,632  83 Linux
/dev/sda8         136,359,783   136,713,126       353,344  82 Linux swap / Solaris
/dev/sda9         147,189,760   160,143,359    12,953,600  83 Linux
/dev/sda10        160,145,408   160,835,567       690,160  82 Linux swap / Solaris

[COLOR="Red"]/dev/sda4 ends after the last sector of /dev/sda[/COLOR]
```

You have Ubuntu 10.10 in sda1, in a NTFS/Windows XP type partition, as Dutch70 has said already.
You have Ubuntu 10.10 in sda3 with grub legacy (should be grub2)
You have Ubuntu 9.04 at least partly installed to sda7

Which system are you trying to boot and which system's grub do you want in control?

---

### Post by MegaLoler on 2011-04-26
I am trying to boot into the Ubuntu 10.10 on sda3 and I want that grub in control as well.  If I remember correctly it had grub 2 on it before, but I'm not totally sure because I barely pay attention when booting up. :P

---

### Post by MegaLoler on 2011-04-26
I managed to get into Ubuntu!  I copied the menu.lst file from the live cd and put it onto the sda3 partition and then made changes.  I think the reason it hanged when I entered it manually is because I didn't put root=/dev/sda3 at the end of the kernel command.

Now to clean up like Dutch70 suggested.  Thank you!

---

### Post by Dutch70 on 2011-04-26
Wow...Nice work! 

What I actually suggested was to back up all your important data and see if you can fix your hdd. You can't clean it up until you fix the extended partition.

---

### Post by Quackers on 2011-04-26
Very true Dutch70.

I've had excellent results with Fixparts, which is a program written by forum user srs5694
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by Dutch70 on 2011-04-26
That's who/what I was referring to back in post #4 of this thread, but I couldn't find it & I don't think he was online.

Bookmarked now, Thanks! :KS

---

