---
title: "booting a ubcd4win boot cd(WinPEbased ) thro grub2 menu"
date: 2011-01-06
forum: General Help
---

### Post by kasinath on 2011-01-06
hello,

iam using a hcl ME laptop with 4gb ram and 500gb hard disk.

I first installed win7 home premium with 4 disk partitions.
then kubuntu 10.10 in a partition linux lvm 20gb

500mb swap memory.

my boot options are

1) kubuntu generic 
2) kubuntu fail safe mode
3) kubutu memory mode
4) windows 7 dev partition.

I tried to boot the system with ubcd4win 3.60 .
It booted ,windows xp logo ran ,then it thrown a error message with error code 

STOP 0x0000007B (0xF78CE528) (0xC0000034) (0x00000000) (0x00000000)

kindly advice how to boot and run in my system.


But I could boot successfully ubcd5.03 linux cd and system rescue cd.

Kindly help me how to add a WinPE based boot cd to boot thro bootloader menu(grub2) in kubuntu 10.10


kindly advice HOW CAN i run successfully UBCD4win 3.6 and take disk backup image using softwares like driveimagexml...


kasinath

---

### Post by dandnsmith on 2011-01-06
You seem to be trying to complicate things by asking about Windows based system tools in a Linux forum.

Is it possible to boot Kubuntu by booting from the system hard disk (not CD)?

If not, what happens when you try?

Do you have an installation CD for the Kubuntu which you can boot from?

---

### Post by kasinath on 2011-01-06
hello sir,

kubutu is installed in the hard disk only.

I could boot from any linux based rescue cds like system rescuecd,

ubcd 5.03 ,bootitNG etc....

The hard disk contains partitions installed with windows 7 premium

kubutu and windows7 premium successfully able to run using initial bootloader menu.


As there is enty in the grub2 menu to load windows 7

likewise can a entry be created for booting a window based rescue boot cd.

It seems that if I directly try to boot the windows based rescue cd ,by selecting the "boot from  cd" option in the BIOS,
the windows based rescue cd after booting could not able to see the partitions ,may due to MBR changes kubutu's grub loader made.

kasinath

---

### Post by dandnsmith on 2011-01-07
> **kasinath said:**
> 
The hard disk contains partitions installed with windows 7 premium
kubutu and windows7 premium successfully able to run using initial bootloader menu.

As there is entry in the grub2 menu to load windows 7
likewise can a entry be created for booting a window based rescue boot cd?

It seems that if I directly try to boot the windows based rescue cd ,by selecting the "boot from  cd" option in the BIOS,
the windows based rescue cd after booting could not able to see the partitions ,may due to MBR changes kubutu's grub loader made.

**No**, none of any changes made to the MBR can stop a CD booting, or affect the visibility of the partitions - for that you need to look to different causes.
One of them is that the versions of the rescue disks cannot cope with the partition usage - I'm thinking of the start of the actual partition information, which changed when Windows 7 PCs appeared.

If you can download and run [the bootscript](http://sourceforge.net/projects/bootinfoscript/), and post the results, then someone here may be able to suggest a path of action.

Do you actually have a real problem with booting which needs solving, or is there another problem with your system (which might be amenable to a different line of attack)?

---

### Post by kasinath on 2011-01-08
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda4 and 
                       looks at sector 893835424 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   104,857,253   104,855,206   7 HPFS/NTFS
/dev/sda2         104,859,648   136,312,831    31,453,184   c W95 FAT32 (LBA)
/dev/sda3         136,312,832   874,367,111   738,054,280   7 HPFS/NTFS
/dev/sda4         874,371,070   976,771,071   102,400,002   f W95 Ext d (LBA)
/dev/sda5         874,371,072   935,811,071    61,440,000   7 HPFS/NTFS
/dev/sda6         935,813,120   936,837,119     1,024,000  82 Linux swap / Solaris
/dev/sda7         936,839,168   976,771,071    39,931,904  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9E7E57F17E57C127                       ntfs       HCL_DISK1                     
/dev/sda2        0F12-17E6                              vfat       HCL_DISK2                     
/dev/sda3        22ECE3A0ECE36D0B                       ntfs       HCL_DISK3                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        6092F3AD92F385B6                       ntfs       HCL_DISK4                     
/dev/sda6        80636f8b-3707-4c0f-91e3-b0e3cb85bc3c   swap                                     
/dev/sda7        168ff8ea-330f-46e2-b41a-0bb9c0a96e79   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext3       (rw,errors=remount-ro,commit=0)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 168ff8ea-330f-46e2-b41a-0bb9c0a96e79
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 168ff8ea-330f-46e2-b41a-0bb9c0a96e79
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 168ff8ea-330f-46e2-b41a-0bb9c0a96e79
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=168ff8ea-330f-46e2-b41a-0bb9c0a96e79 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 168ff8ea-330f-46e2-b41a-0bb9c0a96e79
	echo	'Loading Linux 2.6.35-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-22-generic-pae root=UUID=168ff8ea-330f-46e2-b41a-0bb9c0a96e79 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 168ff8ea-330f-46e2-b41a-0bb9c0a96e79
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 168ff8ea-330f-46e2-b41a-0bb9c0a96e79
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 9e7e57f17e57c127
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=80636f8b-3707-4c0f-91e3-b0e3cb85bc3c none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 485.0GB: boot/grub/core.img
 484.9GB: boot/grub/grub.cfg
 484.9GB: boot/initrd.img-2.6.35-22-generic-pae
 484.9GB: boot/vmlinuz-2.6.35-22-generic-pae
 484.9GB: initrd.img
 484.9GB: vmlinuz

```

---

### Post by kasinath on 2011-01-14
Hello Mr.dandnsmith,

I have posted my bootscript ran on my system .

Kindly look in to that ,awating you help


kasinath

---

