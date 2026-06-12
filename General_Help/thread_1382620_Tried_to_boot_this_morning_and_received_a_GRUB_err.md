---
title: "Tried to boot this morning and received a GRUB error"
date: 2010-01-16
forum: General Help
---

### Post by OldGriff on 2010-01-16
Good morning,

I have been dual booting ubuntu and VistaWin7 for a little while now. This morning when I attempted to boot I received the following:

GRUB loading.
Error: no such disk
Grub rescue>

I am a novice to Linux/GNU/etc.  I have tested the devices and they ae recognized and working. I then booted from the install CD I made and can see the two hard drives in my system from Gpart.  

No clue how/where to proceed from here. 

I am in the process of backing up files to an extrenal drive in case the worst happens. Wish they had Quicken/Turbo Tax for ubuntu. I'd remove the dual boot then.

Any help would be greatly appreciated!

---

### Post by OldGriff on 2010-01-16
Frustrated.   
Seems like I have 
/dev/sda1 - was Vista drive bootable
/dev/sda2 - recovery partition

/dev/sdb2 - other hard drive, only shows 1/2 of the space on drive

This was displayed using sudo fdisk -l

When I attempted to enter sudo grub into Terminal I received 
sudo: grub: command not found

I am attempting to read and discover how to fix this but, being a novice to ubuntu and Linux, it seems insurmountable.

---

### Post by Leppie on 2010-01-16
welcome to the community :)
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by OldGriff on 2010-01-16
To prive my ignorance,  What would I run this from/under? Sorry just so dang new to this

---

### Post by OldGriff on 2010-01-16
Well OK,  downloaded file. Saved in downloads folder,  using sudo bash boot_info_script048.sh   nothing seems to happen, where would the results be placed?

---

### Post by Leppie on 2010-01-16
if you saved to the downloads folder, you have to amend the location of the script:
```
sudo bash ~/Downloads/boot_info_script*.sh
```

---

### Post by OldGriff on 2010-01-16
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks for 
    (UUID=8a4390ef-9d3c-497d-878a-91ae1739c7ad)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   683,742,464   683,742,402   7 HPFS/NTFS
/dev/sda2         683,742,465   703,277,504    19,535,040   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4ea146ae

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   370,780,199   370,778,152   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="5EB49420B493F8AB" LABEL="HP" TYPE="ntfs" 
/dev/sda2: UUID="949CA48C9CA46A86" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sdb1: UUID="083222A5322297A8" LABEL="HP2" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
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
/dev/sda1 on /media/HP type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb1 on /media/HP2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by Leppie on 2010-01-16
it looks like your ubuntu partition has been removed from your sytem.
you could try to recover the partition using a tool like this: [http://www.ptdd.com/recoverdeletedpartition.htm](http://www.ptdd.com/recoverdeletedpartition.htm)

---

### Post by OldGriff on 2010-01-16
Wow,  wasn't expecting that. I will attempt to try to recover or just reinstall Win7 and play with ubuntu on an old laptop I have. 

I appreciate all of your help. Its what makes a great user community.

Regards,

Old Griff

---

