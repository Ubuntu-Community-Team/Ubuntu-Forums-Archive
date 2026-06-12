---
title: "&quot;GRUB _&quot; Appears At Startup &amp; Fails To Boot"
date: 2010-03-29
forum: General Help
---

### Post by curtissthompson on 2010-03-29
A couple weeks ago I installed Ubuntu Security and Recommended Updates that included an update to Linux Kernel 2.6.31-20.  Upon installing these updates I was prompted to restart my computer for the changes to take effect.  So I rebooted and encountered a [Hyper Transport Sync Flood error]("http://forums.amd.com/forum/messageview.cfm?FTVAR_FORUMVIEWTMP=Threaded&catid=22&threadid=88140") each time I tried to boot, preventing me from booting into the OS.

The above linked forum thread about the error suggested I manually adjust voltage settings in the BIOS to resolve the issue, so I gave it a try to no avail.  Then I decided I would just reset my BIOS settings to the defaults (seeing as I hadn't edited that many settings to begin with).  After doing so, I tried booting only to encounter a black screen with "GRUB _" printed on it.

I have encountered [this issue before]("http://ubuntuforums.org/showthread.php?t=1384711") when I initially installed Ubuntu 9.10 on my system, but I'm not sure whether this occurrence is strictly BIOS setting related or if something effected my bootloader.  (On a side note, resetting my BIOS settings to defaults seemed to, at least for now, eliminate the Hyper Transport Sync Flood error I was getting...and instead leave me with another problem.)

I used [this script]("http://sourceforge.net/projects/bootinfoscript/") created by [meierfra.]("http://ubuntu.ubuntuforums.org/member.php?u=552151") to provide info on my current boot setup, the results of which are displayed below.

```
RESULTS.txt is posted below:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 1110695 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08a4e506

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e62ed

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   281,057,174   281,057,112  83 Linux
/dev/sdc2         281,057,175   293,041,664    11,984,490   5 Extended
/dev/sdc5         281,057,238   293,041,664    11,984,427  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdb1        A49474D89474AE84                       ntfs       Numero Dos                    
/dev/sdc1        6f2b1ef3-87c8-47c0-aeb5-d122d769c94b   ext4                                     
/dev/sdc5        40151307-dd8b-4f1c-b62b-c0bad8fb331c   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sdc1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd2,1)
search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-20-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro single 
	initrd	/boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro single 
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 6f2b1ef3-87c8-47c0-aeb5-d122d769c94b
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdc1 during installation
UUID=6f2b1ef3-87c8-47c0-aeb5-d122d769c94b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc5 during installation
UUID=40151307-dd8b-4f1c-b62b-c0bad8fb331c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


    .5GB: boot/grub/core.img
   7.7GB: boot/grub/grub.cfg
    .6GB: boot/initrd.img-2.6.31-14-generic
   1.3GB: boot/initrd.img-2.6.31-17-generic
   5.9GB: boot/initrd.img-2.6.31-19-generic
   8.6GB: boot/initrd.img-2.6.31-20-generic
    .5GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-17-generic
   4.1GB: boot/vmlinuz-2.6.31-19-generic
   2.2GB: boot/vmlinuz-2.6.31-20-generic
   8.6GB: initrd.img
   5.9GB: initrd.img.old
   2.2GB: vmlinuz
   4.1GB: vmlinuz.old
```

_My System Specs:_
OS: Ubuntu 9.10 Karmic Koala
CPU: AMD Phenom II X4 955 3.2 GHz Black Edition
Motherboard: ASUS M4A79T Deluxe
Memory: [4GB (2 x 2GB) G.SKILL RipjawS Series DDR3 1600]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231303")

Any help in resolving this issue would be greatly appreciated.

---

### Post by oldfred on 2010-03-29
When you reset to defaults did it change your boot to sda since that is the normal default. The grub you have in sda will give the type of errors you are seeing as it has no place to go. Try resetting your boot to sdc.

---

### Post by curtissthompson on 2010-03-30
Thanks for the help, I thought I had boot order correct, but turns out my hard drive order (which is separate from boot order in my BIOS) was out of order due to very similar model numbers on the hard drives I have connected.

Now I can at least start to boot into the OS, but apparently the Hyper Transport sync flood error still persists.  Is there a way to boot into an older version of the Linux kernel (because I think this may have been a problem caused by the kernel update I installed)?  I seem to remember such a feature.

---

### Post by oldfred on 2010-03-30
With grub2 it is the shift key (old grub was the escape key) I think you have to hold it down (not just tap it) from the time BIOS ends until menu appears.

---

### Post by curtissthompson on 2010-03-30
I got to the screen and tried all options for various old versions of the kernel (2.6.31-20, 20.6.31-19, 2.6.31-17, 2.6-14, & 2.6.20 [recovery mode]) None of them got me past that Hyper Transport sync flodd error.  I've never used the recovery mode before though and didn't want to do anything and mess something up.

Any idea of what might have caused this Hyper Transport sync flood error?  Does it sound like something that is OS related, or BIOS related?

---

### Post by oldfred on 2010-03-30
I just looked in google and it is a motherboard/cpu issue. 

[http://www.google.com/#hl=en&source=hp&q=Hyper+Transport+sync+flood&btnG=Google+Search&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=bcdf8cbbf06dc4f](http://www.google.com/#hl=en&source=hp&q=Hyper+Transport+sync+flood&btnG=Google+Search&aq=f&aqi=&aql=&oq=&gs_rfai=&fp=bcdf8cbbf06dc4f)

[http://www.tomshardware.com/forum/265878-30-hyper-transport-sync-flood-error-problem-continues](http://www.tomshardware.com/forum/265878-30-hyper-transport-sync-flood-error-problem-continues)
[http://forums.amd.com/forum/messageview.cfm?catid=22&threadid=88140](http://forums.amd.com/forum/messageview.cfm?catid=22&threadid=88140)

---

### Post by curtissthompson on 2010-03-30
Yeah I just wanted to make sure it wasn't in any way caused by Ubuntu security and recommended updates, as that error occurred right after a required reboot upon installation of some Ubuntu updates.

---

