---
title: "ubuntu is not booting"
date: 2009-12-11
forum: General Help
---

### Post by srisar on 2009-12-11
hi all,
im very new to ubunt and i really like it. much better than windows for me.. but there is this small problem, i have 2 hdds, one is 80Gb and other is 320gb, i have my ubuntu is on 80gb. the problem is some times 320gb doesnt show up correctly on ubuntu, so when i remove it and starts the computer, it is saying boot failure, insert a boot disk and press enter..

what shall i do, i thought that 320gb is nothing to do with my ubuntu's 80gb hdd. how can i solve this

---

### Post by byStanderone on 2009-12-12
...is your 80gb hdd formatted in ext3 or ext4?

---

### Post by oldfred on 2009-12-12
It sounds like the bootloader - grub is on the 320GB drive ever though the 80GB drive has Ubuntu.

The best way to see how you are booting is make sure both drives are plugged in and run this script.

Boot Info Script 0.41 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 

Instructions
  louieb's 
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
cd to directory saved to: 
chmod 755 boot_info_script041.sh 
sudo ./boot_info_script041.sh 
or as example if on desktop from liveCD download 
sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

When I jsut ran ver 41 it put results in my home directory even though that was not where I had downloaded it to.

---

### Post by srisar on 2009-12-12
i80gb -  ext4 single partition( ubuntu created swap insude it)

320gb has 4 partitons all NTFS

---

### Post by srisar on 2009-12-12
as u aksed im pasing the results here

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=7aff42f1-0b30-48e2-9d42-6fea7cc0225c)/boot/grub.
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x54316acf

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   163,846,934   163,846,872   7 HPFS/NTFS
/dev/sda2         163,846,935   327,693,869   163,846,935   7 HPFS/NTFS
/dev/sda3         327,693,870   471,057,929   143,364,060   7 HPFS/NTFS
/dev/sda4         471,057,930   625,137,344   154,079,415   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91439143

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   154,191,869   154,191,807  83 Linux
/dev/sdb2         154,191,870   160,826,714     6,634,845   5 Extended
/dev/sdb5         154,191,933   160,826,714     6,634,782  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sdb1: UUID="7aff42f1-0b30-48e2-9d42-6fea7cc0225c" TYPE="ext4" 
/dev/sdb5: UUID="31c559c7-0386-4fce-bd3e-d0a981e9ee38" TYPE="swap" 
/dev/sda1: UUID="1A0C89E70C89BDEF" LABEL="APPZ_LAB" TYPE="ntfs" 
/dev/sda2: UUID="306244F96244C576" LABEL="MEDIA_LAB" TYPE="ntfs" 
/dev/sda3: UUID="28FA95CDFA959820" LABEL="WORKS_LAB" TYPE="ntfs" 
/dev/sda4: UUID="6CA69B81A69B4B0A" LABEL="KNOL_LAB" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
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
none on /var/lib/ureadahead/debugfs type debugfs (rw)
/dev/sda4 on /media/KNOL_LAB type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /media/WORKS_LAB type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /media/MEDIA_LAB type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/APPZ_LAB type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/saravana/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=saravana)
/dev/sr0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=saravana)


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
search --no-floppy --fs-uuid --set 7aff42f1-0b30-48e2-9d42-6fea7cc0225c
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 7aff42f1-0b30-48e2-9d42-6fea7cc0225c
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=7aff42f1-0b30-48e2-9d42-6fea7cc0225c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 7aff42f1-0b30-48e2-9d42-6fea7cc0225c
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=7aff42f1-0b30-48e2-9d42-6fea7cc0225c ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=7aff42f1-0b30-48e2-9d42-6fea7cc0225c / ext4 errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=31c559c7-0386-4fce-bd3e-d0a981e9ee38 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda4 /media/KNOL_LAB ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda3 /media/WORKS_LAB ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /media/MEDIA_LAB ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda1 /media/APPZ_LAB ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-16-generic
    .0GB: boot/vmlinuz-2.6.31-16-generic
    .0GB: initrd.img
    .0GB: vmlinuz
```

---

### Post by srisar on 2009-12-12
please can anyone help me to solve this..

---

### Post by john newbuntu on 2009-12-12
bump

---

### Post by oldfred on 2009-12-12
If you can boot from the external just reinstall windows to the internal drive.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

You may want to do this first to make sure it boots from the external when you have it plugged in.
reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc

---

