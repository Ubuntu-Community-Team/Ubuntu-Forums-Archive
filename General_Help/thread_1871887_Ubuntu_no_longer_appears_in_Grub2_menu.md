---
title: "Ubuntu no longer appears in Grub2 menu"
date: 2011-10-29
forum: General Help
---

### Post by bigred1 on 2011-10-29
My computer can no longer boot into Ubuntu (Oneiric). 

There were too many old kernels listed in the boot menu. The latest kernel, the one I want, was listed twice,  at the top and in the earlier kernels section.

I used Grub Customizer and unchecked all old kernels, including the second appearance of the latest kernel. I left the first appearance of the latest kernel -- it's the only one I need.

Now, when I boot up, no Ubuntu appears at all! I can boot using Live  disk-on-key, but in that version there is no Grub Customizer or StartUp Manager; and though I tried to install Grub customizer,  it failed on permission errors, so I may have to edit config files.

What do I have to do to restore my Ubuntu?

---

### Post by zvacet on 2011-10-30
Use [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") to reinstall grub.When that goes well you can remove old kernels using synaptic.In search box type **linux-image** and you will see all installed kernels.Remove one with lower number of course.Also with kernel-headers.

---

### Post by bigred1 on 2011-10-31
Thank you. I tried Boot Repair, but the boot menu remains as before, with only Windows appearing.

Here is the boot info summary. [http://paste.debian.net/141561](http://paste.debian.net/141561), also copied below.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 1 for ??.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   160,071,659   160,071,597   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    19,535,039    19,534,977  83 Linux
/dev/sdb2         300,576,150   312,576,704    12,000,555   5 Extended
/dev/sdb5         300,576,213   312,576,704    12,000,492  82 Linux swap / Solaris
/dev/sdb3          19,535,040   300,576,149   281,041,110  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        1EC8A6D4C8A6AA0B                       ntfs       Local Disk
/dev/sdb1        d8183543-f97b-4f71-b27f-3fa8426ccfdd   ext4       
/dev/sdb3        f7d87294-1460-459b-a29a-76a8ca85526f   ext4       
/dev/sdb5        6036269d-9307-4ec0-b67e-0d28a0b2f790   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sr0         /live/image              iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root d8183543-f97b-4f71-b27f-3fa8426ccfdd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root d8183543-f97b-4f71-b27f-3fa8426ccfdd
  set locale_dir=($root)/boot/grub/locale
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

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root d8183543-f97b-4f71-b27f-3fa8426ccfdd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root d8183543-f97b-4f71-b27f-3fa8426ccfdd
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 1EC8A6D4C8A6AA0B
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

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=d8183543-f97b-4f71-b27f-3fa8426ccfdd /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=f7d87294-1460-459b-a29a-76a8ca85526f /home           ext4    defaults,user_xattr        0       2
# swap was on /dev/sdb5 during installation
UUID=6036269d-9307-4ec0-b67e-0d28a0b2f790 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-2.6.32-33-generic              2
            ?? = ??             boot/initrd.img-2.6.38-11-generic             78
            ?? = ??             boot/initrd.img-3.0.0-12-generic              64
            ?? = ??             boot/vmlinuz-2.6.32-33-generic                 6
            ?? = ??             boot/vmlinuz-2.6.38-11-generic                 4
            ?? = ??             boot/vmlinuz-3.0.0-12-generic                 23
            ?? = ??             initrd.img.old                                78
            ?? = ??             vmlinuz                                       23
            ?? = ??             vmlinuz.old                                    4

=============================== StdErr Messages: ===============================

File descriptor 3 (pipe:[6883]) leaked on lvscan invocation. Parent PID 12169: bash
File descriptor 7 (pipe:[6883]) leaked on lvscan invocation. Parent PID 12169: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :

```

---

### Post by bigred1 on 2011-11-01
I resolved it, thanks to some advice on the GNU grub emaillist. 

First, I booted up with LiveCD, then mounted my original Ubuntu directory as follows, so that I was in my system almost as if I had booted into it.

```
mount /dev/sdb1 /mnt
mount -o bind /dev /mnt/dev
mount -o bind /sys /mnt/sys
mount -o bind /proc /mnt/proc
chroot /mnt
```

However, *grub-mkconfig* and *update-grub* left things as before.

The deeper problem was that Grub Customizer had overwritten my */etc/grub.d/10_linux* configuration, replacing it with a pointer to  */etc/grub.d/proxifiedScripts/linux*. See [https://answers.launchpad.net/grub-customizer/+faq/1355](https://answers.launchpad.net/grub-customizer/+faq/1355)

Thus, with every attempt to rebuild the Grub2 configuration, whether with Rescatux, Boot Repair, or console commands, these incorrect settings created by Grub Customizer were used.

So, I had to delete  my *10_linux* file,  then *mv /etc/grub.d/proxifiedScripts/linux /etc/grub.d/10_linux*, and only then run */etc/grub.d/10_linux* configuration, replacing it with a pointer to  */etc/grub.d/proxifiedScripts/linux*.

After all this, in my boot menu, the latest kernel still appears twice, the second time as an "Previous Linux versions." This is a bit annoying, but I will live with it instead of trying to fix it again, which is what got me into this situation in the first place!

---

### Post by YannBuntu on 2011-11-09
For information:
if someone else gets the same problem with Grub-Customizer, there should now be a way to fix it via the "Purge and reinstall" option of Boot-Repair.
[https://bugs.launchpad.net/boot-repair/+bug/887761](https://bugs.launchpad.net/boot-repair/+bug/887761)

---

