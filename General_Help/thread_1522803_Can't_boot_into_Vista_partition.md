---
title: "Can't boot into Vista partition?"
date: 2010-07-02
forum: General Help
---

### Post by cAlpha on 2010-07-02
I've got a dual boot system with Ubuntu 9.10 on one partition and Vista on the other.

After selecting the Vista option within GRUB, the boot seems to start as normal and after the Dell scrawl screen, the machine just seems to restart and I end up back at the GRUB menu.  

Booting into Vista recovery mode doesn't resolve the issue.  

The only other oddity I could mention is that I believe an update I did after installing 9.10 updated the linux kernel, because there are now two sets of linux kernel versions available within GRUB, while there was only one present when I first installed, and Vista was still working.

---

### Post by chaosx9 on 2010-07-02
Just as the quickest thing to do, i would say do the following:

Go into ubuntu, then use Alt>F2, and type in

```
gnome-terminal
```

then press enter. Then use:

```
sudo update-grub
```

and insert your password. Then wait for it to do it's stuff. Then try to boot in again. If it doesn't boot in, use:

```
sudo grub-install
```

to reinstall grub, and see if that works.

---

### Post by wilee-nilee on 2010-07-02
Post the bootscript in my signature in code tags as described.

---

### Post by lisati on 2010-07-02
In answer to the question in your thread title: No, I can boot into my Vista partition. :)

But seriously:

The two or more kernels is normal. The update process keeps old versions around when there's an update to the kernel, just in case new versions don't work well with your system for some reason, so that you can boot back into Ubuntu to troubleshoot what went wrong.

As for booting into Vista, some extra info, like the output from the previously mentioned script might be useful for troubleshooting.

---

### Post by cAlpha on 2010-07-02
Alright, contents of the RESULTS.txt file below:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       144,584       144,522  de Dell Utility
/dev/sda2             145,408    21,116,927    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,116,928   129,142,727   108,025,800   7 HPFS/NTFS
/dev/sda4         129,146,535   156,296,384    27,149,850   5 Extended
/dev/sda5         129,146,661   141,615,717    12,469,057   7 HPFS/NTFS
/dev/sda6         141,629,103   155,573,459    13,944,357  83 Linux
/dev/sda7         155,573,523   156,296,384       722,862  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07D8-0716                              vfat       DellUtility                   
/dev/sda2        C8B2A09FB2A0938A                       ntfs       RECOVERY                      
/dev/sda3        52A2A3C3A2A3A9C5                       ntfs       OS                            
/dev/sda5        166540D27756A805                       ntfs       File Share                    
/dev/sda6        13a250c3-3751-4ea4-b4e3-cac6b1b7e1ae   ext3                                     
/dev/sda7        2a8818e8-7924-4ac1-bfad-6922f8bb807d   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,errors=remount-ro)
/dev/sda3        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/File Share        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set 13a250c3-3751-4ea4-b4e3-cac6b1b7e1ae
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 13a250c3-3751-4ea4-b4e3-cac6b1b7e1ae
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=13a250c3-3751-4ea4-b4e3-cac6b1b7e1ae ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 13a250c3-3751-4ea4-b4e3-cac6b1b7e1ae
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=13a250c3-3751-4ea4-b4e3-cac6b1b7e1ae ro single 
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 13a250c3-3751-4ea4-b4e3-cac6b1b7e1ae
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=13a250c3-3751-4ea4-b4e3-cac6b1b7e1ae ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set 13a250c3-3751-4ea4-b4e3-cac6b1b7e1ae
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=13a250c3-3751-4ea4-b4e3-cac6b1b7e1ae ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 52a2a3c3a2a3a9c5
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=6a89445c-f937-4ba9-997c-2b3827f646a9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=44be824a-54fc-4320-8860-e1cd185ac1af none            swap    sw              0       0

# Mount C-drive from Windows
/dev/sda3 /media/OS ntfs defaults 0 0

# Mount File Share
/dev/sda5 /media/File\040Share ntfs defaults 0 0

=================== sda6: Location of files loaded by Grub: ===================


  78.0GB: boot/grub/core.img
  78.1GB: boot/grub/grub.cfg
  78.0GB: boot/initrd.img-2.6.31-14-generic
  78.1GB: boot/initrd.img-2.6.31-22-generic
  78.0GB: boot/vmlinuz-2.6.31-14-generic
  78.1GB: boot/vmlinuz-2.6.31-22-generic
  78.1GB: initrd.img
  78.0GB: initrd.img.old
  78.1GB: vmlinuz
  78.0GB: vmlinuz.old
```

---

### Post by wilee-nilee on 2010-07-02
So you have a bit of a convoluted setup sda1 appears to be the dell firmware sda2 appears to have been a recovery or still is sda3 appears to be the main MS OS. You have a extended sda4 with a ntfs partition inside of it (sda5) and sda6=Ubuntu 9.10 and sda7 the swap.

Normally the ntfs sda5 should be a primary if used as a shared partition. But due to all the other partitions and a HD limitations of only 4 primaries, it is in a extended. 

Also dell computers some times have a dell data safe program that overrides the master boot record, but is part of the MS setup, and generally I think not activated to do it's stuff until you get into the MS setup, if it is even on the computer.

I think you will be best served by one of the more experienced forum members at this point.

---

### Post by cAlpha on 2010-07-04
Any ideas on this?

---

