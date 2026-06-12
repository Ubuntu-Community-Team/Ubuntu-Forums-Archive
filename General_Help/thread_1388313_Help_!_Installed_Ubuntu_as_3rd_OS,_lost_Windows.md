---
title: "Help ! Installed Ubuntu as 3rd OS, lost Windows"
date: 2010-01-22
forum: General Help
---

### Post by Amamba on 2010-01-22
I used to dual-boot XP and Suse (both on same disk, different partitions).

Just added Ubuntu 9.10, hoping to make it a 3rd boot option. Immediately lost XP.

My device.map file has the following:

(hd0)	/dev/sda
(hd1)	/dev/sdb

Windows is on /dev/sdb1 and Suse on /dev/sdb6 partitions, Ubuntu on /dev/sda.

I added 11_Windows to /etc/grub.d as such:

#! /bin/sh -e
echo "Adding Windows" >&2
cat << EOF
menuentry "Windows XP" {
set root=(hd1,1)
chainloader +1
}
EOF

and ran update-grub2:

sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-17-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found openSUSE 11.2 (i586) on /dev/sdb6
done

No Windows...

What do I do now ?

---

### Post by ranch hand on 2010-01-23
Run;
```

sudo update-grub

```
This should pick up MS.

---

### Post by Amamba on 2010-01-23
> **ranch hand said:**
> Run;
```

sudo update-grub

```
This should pick up MS.

No, it gives me the same output as sudo update-grub2

sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-17-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found openSUSE 11.2 (i586) on /dev/sdb6
done

---

### Post by ranch hand on 2010-01-23
In that case you had better run this script and post the result text that will be on your desktop;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by Amamba on 2010-01-23
> **ranch hand said:**
> In that case you had better run this script and post the result text that will be on your desktop;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

OK, it's rather long:

============================= Boot Info Summary: ==============================
```

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Welcome to openSUSE 11.2 
                       "Emerald" - Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 45.0 GB, 45020602368 bytes
255 heads, 63 sectors/track, 5473 cylinders, total 87930864 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x35113484

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    84,228,794    84,228,732  83 Linux
/dev/sda2          84,228,795    87,923,744     3,694,950   5 Extended
/dev/sda5          84,228,858    87,923,744     3,694,887  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf5bfe447

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    40,965,749    40,965,687   7 HPFS/NTFS
/dev/sdb2          40,965,750   154,432,844   113,467,095   f W95 Ext d (LBA)
/dev/sdb5          40,965,813    44,082,359     3,116,547  82 Linux swap / Solaris
/dev/sdb6          44,082,423    86,028,074    41,945,652  83 Linux
/dev/sdb7          86,028,138   154,432,844    68,404,707  83 Linux
/dev/sdb3    *    154,432,845 1,465,144,064 1,310,711,220   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4d4023ce-1fcd-4aeb-a800-6ec830bcaf98" TYPE="ext4" 
/dev/sda5: UUID="bdce95fb-131d-4b63-87e5-c2831a897fe8" TYPE="swap" 
/dev/sdb1: UUID="1014574D14573546" LABEL="SYSTEM" TYPE="ntfs" 
/dev/sdb3: UUID="4E6EEAA743691C54" LABEL="DATA+PROG" TYPE="ntfs" 
/dev/sdb5: UUID="4a0b08ef-df4d-4faf-a8d1-b9ff8f1c4a32" TYPE="swap" 
/dev/sdb6: UUID="4411d0cf-9156-4afc-b438-4471e82febbc" TYPE="ext3" 
/dev/sdb7: LABEL="35" UUID="78004033-a2c8-4d12-9d10-f9e6945be582" SEC_TYPE="ext2" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/kotopus/.Private on /home/kotopus type ecryptfs (ecryptfs_sig=21646d6f1593f03a,ecryptfs_fnek_sig=c85f1637bd7817c8,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/kotopus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kotopus)
/dev/sdb6 on /media/4411d0cf-9156-4afc-b438-4471e82febbc type ext3 (rw,nosuid,nodev,uhelper=devkit)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root=(hd0,1)
search --no-floppy --fs-uuid --set 4d4023ce-1fcd-4aeb-a800-6ec830bcaf98
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
menuentry "Ubuntu, Linux 2.6.31-17-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4d4023ce-1fcd-4aeb-a800-6ec830bcaf98
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=4d4023ce-1fcd-4aeb-a800-6ec830bcaf98 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-17-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4d4023ce-1fcd-4aeb-a800-6ec830bcaf98
    linux    /boot/vmlinuz-2.6.31-17-generic-pae root=UUID=4d4023ce-1fcd-4aeb-a800-6ec830bcaf98 ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "openSUSE 11.2 - 2.6.31.8-0.1 (pae) (on /dev/sdb6)" {
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 4411d0cf-9156-4afc-b438-4471e82febbc
    linux /boot/vmlinuz-2.6.31.8-0.1-pae root=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part6 repair=1 resume=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part5 splash=silent quiet showopts vga=0x31a
    initrd /boot/initrd-2.6.31.8-0.1-pae
}
menuentry "Failsafe -- openSUSE 11.2 - 2.6.31.8-0.1 (pae) (on /dev/sdb6)" {
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 4411d0cf-9156-4afc-b438-4471e82febbc
    linux /boot/vmlinuz-2.6.31.8-0.1-pae root=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part6 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.31.8-0.1-pae
}
menuentry "openSUSE 11.2 - 2.6.31.8-0.1 (default) (on /dev/sdb6)" {
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 4411d0cf-9156-4afc-b438-4471e82febbc
    linux /boot/vmlinuz-2.6.31.8-0.1-default root=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part6 repair=1 resume=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part5 splash=silent quiet showopts vga=0x31a
    initrd /boot/initrd-2.6.31.8-0.1-default
}
menuentry "Failsafe -- openSUSE 11.2 - 2.6.31.8-0.1 (default) (on /dev/sdb6)" {
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 4411d0cf-9156-4afc-b438-4471e82febbc
    linux /boot/vmlinuz-2.6.31.8-0.1-default root=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part6 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.31.8-0.1-default
}
menuentry "SUSE LINUX (on /dev/sdb6)" {
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 4411d0cf-9156-4afc-b438-4471e82febbc
    linux /boot/vmlinuz root=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part6 repair=1 resume=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part5 splash=silent quiet showopts vga=0x31a
    initrd /boot/initrd
}
menuentry "Failsafe -- SUSE LINUX (on /dev/sdb6)" {
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 4411d0cf-9156-4afc-b438-4471e82febbc
    linux /boot/vmlinuz root=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part6 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=4d4023ce-1fcd-4aeb-a800-6ec830bcaf98 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=bdce95fb-131d-4b63-87e5-c2831a897fe8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-17-generic-pae
    .0GB: boot/vmlinuz-2.6.31-17-generic-pae
    .0GB: initrd.img
    .0GB: vmlinuz

=========================== sdb6/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Tue Jan 19 18:06:41 EST 2010
# THIS FILE WILL BE PARTIALLY OVERWRITTEN by perl-Bootloader
# Configure custom boot parameters for updated kernels in /etc/sysconfig/bootloader

default 6
timeout 8
gfxmenu (hd1,5)/boot/message

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.2 - 2.6.31.8-0.1 (pae)
    root (hd1,5)
    kernel /boot/vmlinuz-2.6.31.8-0.1-pae root=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part6 repair=1 resume=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part5 splash=silent quiet showopts vga=0x31a
    initrd /boot/initrd-2.6.31.8-0.1-pae

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.2 - 2.6.31.8-0.1 (pae)
    root (hd1,5)
    kernel /boot/vmlinuz-2.6.31.8-0.1-pae root=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part6 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.31.8-0.1-pae

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.2 - 2.6.31.8-0.1 (default)
    root (hd1,5)
    kernel /boot/vmlinuz-2.6.31.8-0.1-default root=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part6 repair=1 resume=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part5 splash=silent quiet showopts vga=0x31a
    initrd /boot/initrd-2.6.31.8-0.1-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.2 - 2.6.31.8-0.1 (default)
    root (hd1,5)
    kernel /boot/vmlinuz-2.6.31.8-0.1-default root=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part6 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.31.8-0.1-default

###Don't change this comment - YaST2 identifier: Original name: linux###
title SUSE LINUX 
    root (hd1,5)
    kernel /boot/vmlinuz root=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part6    repair=1 resume=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part5 splash=silent quiet showopts vga=0x31a
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- SUSE LINUX 
    root (hd1,5)
    kernel /boot/vmlinuz root=/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part6 showopts apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd

###Don't change this comment - YaST2 identifier: Original name: windows 1###
title windows 1
    rootnoverify (hd0,0)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 2###
title windows 2
    map (hd1) (hd0)
    map (hd0) (hd1)
    rootnoverify (hd1,0)
    makeactive
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name: windows 3###
title windows 3
    map (hd1) (hd0)
    map (hd0) (hd1)
    rootnoverify (hd1,2)
    makeactive
    chainloader +1

=============================== sdb6/etc/fstab: ===============================

/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part6 /                    ext3       acl,user_xattr        1 1
/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part7 /home                ext3       acl,user_xattr        1 2
/dev/disk/by-id/ata-WDC_WD450AA-00BAA0_WD-WMA2E1207655-part1 /windows/C           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part3 /windows/E           ntfs-3g    users,gid=users,fmask=133,dmask=002,locale=en_US.UTF-8 0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
/dev/disk/by-id/ata-ST3750640AS_5QD4GTDF-part1 /windows/D           ntfs-3g    users,gid=users,fmask=133,dmask=022,locale=en_US.UTF-8 0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sdb6: Location of files loaded by Grub: ===================


  22.5GB: boot/grub/menu.lst
  22.5GB: boot/grub/stage2
  22.5GB: boot/initrd
  22.5GB: boot/initrd-2.6.31.8-0.1-default
  22.5GB: boot/initrd-2.6.31.8-0.1-pae
  22.5GB: boot/vmlinuz
  22.5GB: boot/vmlinuz-2.6.31.8-0.1-default
  22.5GB: boot/vmlinuz-2.6.31.8-0.1-pae
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf
```

---

### Post by ranch hand on 2010-01-23
That is interesting.  Have you changed the drives around or were you booting from sdb before this install?

I am wondering because usually sda is the drive of choice for booting.

Does your Suse boot with the current setup?

---

### Post by Amamba on 2010-01-23
> **ranch hand said:**
> That is interesting.  Have you changed the drives around or were you booting from sdb before this install?

I am wondering because usually sda is the drive of choice for booting.

Does your Suse boot with the current setup?

Yes, I was booting from sdb. I used to have 2 drives, an old 40GB drive and a master. The master died on me and while I added a new drive I somehow got the old drive as sda. This never caused a problem, and Suse installed and booted right away (also from sdb, and it preserved Windows). I didn't try to boot into Suse after installing Ubuntu though, I was trying to get Windows running first.

---

### Post by ranch hand on 2010-01-23
I think there may be a problem with the generated menu entry(s) on suse.

Try;
```

sudo grub-install /dev/sdb

```
and then
```

sudo update-grub

```
and rerun the script if MS doesn't show up.

---

### Post by Amamba on 2010-01-23
Well, to make a long story short, after screwing around well into the night, I somehow completely mucked up mbr... and ended up (this morning) wiping out Windows and Ubuntu partitions, and am currently in the process of reinstalling XP. 

Once I am done with it, I will repair Suse install using DVD - I've done it several times, I am familiar with the process, and honestly, Suse's graphical Grub Menu manager makes it so much easier than Ubuntu.

For now, I am going to try Ubuntu via Live CD... I don't think I have the guts to attempt another triple boot installation in the nearest future ;)

Thank you for your support ! I really appreciate it.

---

