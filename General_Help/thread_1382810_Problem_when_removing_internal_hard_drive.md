---
title: "Problem when removing internal hard drive"
date: 2010-01-16
forum: General Help
---

### Post by Tryfon on 2010-01-16
Ok. I have two internal hard drives in my computer, both SATAII, both Western Digital, one 500GB and one 1TB. Ubuntu as well as GRUB are on the 500GB. Everything works well up until when I try to remove the 1TB drive. I turn off the computer, remove the hd, then turn it on again and then I get the following message:

```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmd/line)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sdb6 does not exist. Dropping to a shell.
```

---

### Post by RedRat on 2010-01-16
I am interested in this. I had a similar problem with my two SATA DVD/CD units in my machine. Both worked erratically and I thought that there was something wrong with my machine, e.g., BIOS, etc. I could not boot from either drive. 

After some testing and playing around, the tech found that one DVD/CD burner was faulty, it was the older unit a Plextor. When that drive was completely removed and power cable removed, the other drive would work flawlessly, i.e., I could boot from it. 

Needless to say, the tech and I were both surprised at this interconnection between the two drive units. Clearly, there is something in the SATA software that must be at the root of this problem. I will be interested in what others say about this.

---

### Post by ranch hand on 2010-01-16
I am not sure why you are doing this but I do strange things to mine all the time too.

I would edit your device map to just list the drive you have remaining (in grub2 and I believe in grub-legacy this is in /boot/grub).

You should also go to your bios and make sure that the bios have the removed drive as "off" or what ever your bios uses for that.

---

### Post by Tryfon on 2010-01-17
Thanks for the reply, but I can't find the files you mentioned.

---

### Post by ranch hand on 2010-01-17
> **Tryfon said:**
> Thanks for the reply, but I can't find the files you mentioned.
What version of grub are you running?  Give output of;
```

grub-install -v

```
Just so I can check to make sure where the device map is and it may have a different tittle.

---

### Post by Tryfon on 2010-01-17
GNU GRUB 1.97~beta4

---

### Post by ranch hand on 2010-01-17
You should be able to get the device map by;
```

gksudo gedit /boot/grub/device.map

```

---

### Post by Tryfon on 2010-01-17
Ok, in order to help you with helping me I ran the Boot Info Script from [here]("http://sourceforge.net/projects/bootinfoscript/") and it gave me the following results:

```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00004e4d

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,953,520,064 1,953,520,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4f3255e4

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   307,202,047   307,200,000   7 HPFS/NTFS
/dev/sdb2         307,210,995 1,250,258,624   943,047,630   5 Extended
/dev/sdb5         307,211,058   322,826,174    15,615,117  82 Linux swap / Solaris
/dev/sdb6         322,826,238 1,250,258,624   927,432,387  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ffc810

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   563,704,784   563,704,722   b W95 FAT32
/dev/sdc2         563,704,785   625,137,344    61,432,560   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="b5d905dd-9e77-4d2a-80e7-08907cfddf7f" TYPE="ext3" 
/dev/sdb1: UUID="4AF06E48F06E3A79" TYPE="ntfs" 
/dev/sdb5: UUID="487b17ce-d8a0-428a-a0f9-25c17f872778" TYPE="swap" 
/dev/sdb6: UUID="57a22b24-03a6-4c67-b96b-5c0beb40e3b1" TYPE="ext4" 
/dev/sdc1: LABEL="EXTERNAL NO" UUID="4A0F-DB46" TYPE="vfat" 
/dev/sdc2: UUID="09E7F68E740C6D1A" LABEL="External BigFiles" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb6 on / type ext4 (rw,errors=remount-ro)
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
/dev/sdb1 on /media/Vista type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/markos/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=markos)
/dev/sda1 on /media/b5d905dd-9e77-4d2a-80e7-08907cfddf7f type ext3 (rw,nosuid,nodev,uhelper=devkit)
/dev/sdc1 on /media/EXTERNAL NO type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdc2 on /media/External BigFiles type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=========================== sdb6/boot/grub/grub.cfg: ===========================

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
menuentry "Ubuntu, Linux 2.6.31-18-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-18-generic-pae root=/dev/sdb6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-18-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-18-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-18-generic-pae root=/dev/sdb6 ro single 
	initrd	/boot/initrd.img-2.6.31-18-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-17-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	linux	/boot/vmlinuz-2.6.31-17-generic-pae root=/dev/sdb6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-17-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	linux	/boot/vmlinuz-2.6.31-17-generic-pae root=/dev/sdb6 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic-pae
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
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=57a22b24-03a6-4c67-b96b-5c0beb40e3b1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=487b17ce-d8a0-428a-a0f9-25c17f872778 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1 /media/Vista ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sdb6: Location of files loaded by Grub: ===================


 165.2GB: boot/grub/grub.cfg
 165.2GB: boot/initrd.img-2.6.31-17-generic-pae
 165.2GB: boot/initrd.img-2.6.31-18-generic-pae
 165.2GB: boot/vmlinuz-2.6.31-17-generic-pae
 165.2GB: boot/vmlinuz-2.6.31-18-generic-pae
 165.2GB: initrd.img
 165.2GB: initrd.img.old
 165.2GB: vmlinuz
 165.2GB: vmlinuz.old
```

Contents of device.map are:
[HTML](hd0)	/dev/sda[/HTML]

---

### Post by ranch hand on 2010-01-17
OK, you removed the original sda (1Tb) and now you can't boot to your original sdb (500Gb).  I hope I have this right.

If I am correct then your problem is fairly simple.  Your menu is calling your current sda (500Gb) sdb.

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Will allow you to update-grub.

You should also be able to boot directly from your menu into your Ubuntu by selecting the OS and hitting "e" and then editing the entry to read sda instead of sdb.  This would be the easy way as then you could just run "update-grub" from the terminal.

The only problem requiring you to use the live CD would be if there is a uuid problem.  I do not think this is the case at all but that is why I gave that link (you should have it anyway).  If you use that route ignore the directions for editing files as that is not what you need.

---

### Post by Tryfon on 2010-01-17
Ok, I fixed grub through the live cd as you suggested and everything works fine now.

Thanks a lot!

---

### Post by ranch hand on 2010-01-17
That is great news.

Good work.

---

