---
title: "grub error 15"
date: 2010-01-18
forum: General Help
---

### Post by ApEkV2 on 2010-01-18
Just installed ubuntu using a usb card. 
The installation was successful, but now there is a grub error 15 "file not found" on startup.

Now I'm on the usb live cd trying to fix this.
The computer has two hard drives, and here is the output from fdisk -l.
```
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       13985   112294350    7  HPFS/NTFS
/dev/sda3           13986       18846    39045982+   7  HPFS/NTFS
/dev/sda4           18847       19452     4867695    c  W95 FAT32 (LBA)

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x437bcd01

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4658    37415353+  83  Linux
/dev/sdb2            4659        4863     1646662+   5  Extended
/dev/sdb5            4659        4863     1646631   82  Linux swap / Solaris
```

how do I fix this?

---

### Post by audiomick on 2010-01-18
Hi.
You can use the guide here
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
to find out where your grub has been installed to.

There is a reference to the grub error 15 in the grub2 documentation
[https://help.ubuntu.com/community/Grub2#File%20Not%20Found%20%28Error%2015%29](https://help.ubuntu.com/community/Grub2#File%20Not%20Found%20%28Error%2015%29)
that may well be exactly your problem.

---

### Post by ApEkV2 on 2010-01-18
@ audiomick, thanks for the quick reply. That is a cool script.
Followed the instructions on how to restore grub (in the second link).
I am going to reboot and see if it is fixed.

---

### Post by ApEkV2 on 2010-01-18
I still get error 15

---

### Post by audiomick on 2010-01-18
> **ApEkV2 said:**
> I still get error 15

That's a pity. Do the thing in the first link again, and post it back here. If I can't help, which is unfortunately entirely possible, maybe someone else can use the info to help you.

---

### Post by Leppie on 2010-01-18
what version of grub is this? you can check the version number like this:
```
sudo grub-install -v
```

---

### Post by ApEkV2 on 2010-01-18
@ Leppie, GNU GRUB 1.97~beta4


If you want all of the output.......
```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   
```
```
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         80,325   224,669,024   224,588,700   7 HPFS/NTFS
/dev/sda3         224,669,025   302,760,989    78,091,965   7 HPFS/NTFS
/dev/sda4         302,760,990   312,496,379     9,735,390   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x437bcd01

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    74,830,769    74,830,707  83 Linux
/dev/sdb2          74,830,770    78,124,094     3,293,325   5 Extended
/dev/sdb5          74,830,833    78,124,094     3,293,262  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2032 MB, 2032664576 bytes
255 heads, 63 sectors/track, 247 cylinders, total 3970048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003d2e4

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     3,968,054     3,967,992   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0811" TYPE="vfat" 
/dev/sda2: UUID="3AB45CF0B45CAFDD" TYPE="ntfs" 
/dev/sda3: UUID="3414ABDF14ABA27A" LABEL="Backup" TYPE="ntfs" 
/dev/sda4: LABEL="DellRestore" TYPE="vfat" 
/dev/sdb1: UUID="19799881-1a57-45e8-91f0-dc696ec0317f" TYPE="ext4" 
/dev/sdb5: UUID="4295f15a-7954-4ccf-9f78-e200c0f6df73" TYPE="swap" 
/dev/sdc1: LABEL="New Volume" UUID="3253-4C81" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sdc1 on /cdrom type vfat (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect


```
```
=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root=(hd1,1)
search --no-floppy --fs-uuid --set 19799881-1a57-45e8-91f0-dc696ec0317f
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 19799881-1a57-45e8-91f0-dc696ec0317f
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=19799881-1a57-45e8-91f0-dc696ec0317f ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 19799881-1a57-45e8-91f0-dc696ec0317f
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=19799881-1a57-45e8-91f0-dc696ec0317f ro single 
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
menuentry "Dell Utility Partition (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 07d6-0811
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows XP Media Center Edition (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 3ab45cf0b45cafdd
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda4)" {
	insmod fat
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 0000-0000
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=19799881-1a57-45e8-91f0-dc696ec0317f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=4295f15a-7954-4ccf-9f78-e200c0f6df73 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by Leppie on 2010-01-18
issue these commands to install grub2 to the mbr of sda:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

---

### Post by audiomick on 2010-01-18
I think you are seeing the attempt of the entry in red
```
[COLOR="Red"]=> Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.[/COLOR]
[COLOR="Blue"] => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive in partition #1 for /boot/grub.[/COLOR]
 => Syslinux is installed in the MBR of /dev/sdc
```
to boot, where you want the one in blue.

The stuff in 
sdb1/boot/grub/grub.cfg
all looks right, except for this
```
menuentry "Windows NT/2000/XP (on /dev/sda4)" {
	insmod fat
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set 0000-0000
	drivemap -s (hd0) ${root}
	chainloader +1

```
which seems to be pointing at a partition that doesn't have an OS in it.

I think that if you go into bios and put sdb first in the boot sequence, that it might boot for you.

---

### Post by ApEkV2 on 2010-01-19
I still couldn't figure it out, so I reinstalled ubuntu using an actual cd instead of the usb.

Now everything works!

Thanks though for the replies and looking through that long file though.

---

