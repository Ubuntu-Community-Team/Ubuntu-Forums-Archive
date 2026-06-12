---
title: "chmod weirdness"
date: 2011-03-03
forum: General Help
---

### Post by redcodefinal on 2011-03-03
Ok, So I have been having a lot of trouble configuring my usb drive to boot KATANA and now I've hit a whole new weird issue. Before it wasn't letting me run scripts (I found that I cant just use ./script.sh to run a script but sh ./script.sh to run any script on my drive. ) Now I hit a new piece of weirdness. Every time I change the permissions of a file it tell me me it has been successfully changed but, the file still has the same exact permissions. I then tried to use the GUI too. (Right-click on script-> properties -> permissions) but when I changed a value it would IMMEDIATELY CHANGE BACK.  Anyways this thing is driving me nuts. 

Any help is appreciated

-Ian

---

### Post by mwray on 2011-03-03
The partition is mounted Read Only, so changes don't stay. It's also possible that it's mounted read write, but only for root. 

the mount command by itself on the commandline can show how a filesystem is mounted.
mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /nfssys type ext4 (rw,commit=0)
/dev/sdc1 on /home type ext4 (rw,commit=0)

shows that I have several devices mounted rw.

"fdisk -l" will show attached recognized partitions. 
usb devices can show as /dev/sd? where ? is a, b, c, or d.
or some other number.removing the device and plugging it back in may show you which one it is, and if it shows "ro" in the mount command instead of rw then you cannot make changes.

umount /dev/sd? 
mount /dev/sd? /mnt/mountpoint -o rw 
where ? is replaced by the partition listed in mount command ex:
my usb dev would show up as sdd w/ 1 partion

umount /dev/sda1
mount /dev/sda1 /mnt/sda1 -o rw

(/mnt/sda1 must exist before mounting, it's just a directory.)

Also possible, your usb device may have a physical write protect switch turned on.

---

### Post by mcduck on 2011-03-03
> **redcodefinal said:**
> Ok, So I have been having a lot of trouble configuring my usb drive to boot KATANA and now I've hit a whole new weird issue. Before it wasn't letting me run scripts (I found that I cant just use ./script.sh to run a script but sh ./script.sh to run any script on my drive. ) Now I hit a new piece of weirdness. Every time I change the permissions of a file it tell me me it has been successfully changed but, the file still has the same exact permissions. I then tried to use the GUI too. (Right-click on script-> properties -> permissions) but when I changed a value it would IMMEDIATELY CHANGE BACK.  Anyways this thing is driving me nuts. 

Any help is appreciated

-Ian
Are the files located on a drive/partition that's formatted into FAT or NTFS filesystem? 

Those filesystems don't support ownerships and permissions as Linux uses them, and therefore the permissions are set for the whole partition at the time it's mounted and trying to chmod or chown anything will just revert back to the set permissions.

(same applies to optical media, regardless of if it's a RW disc or not, the filesystem used on them is read-only)

What comes to *./somefile.sh* versus *sh somefile.sh*, the difference is that in the first case you are executing the script itself, while on the second one you are executing the shell, and giving it the script as a parameter, so the script doesn't have to be executable.

---

### Post by redcodefinal on 2011-03-04
Thank you that fixed it
> **mwray said:**
> The partition is mounted Read Only, so changes don't stay. It's also possible that it's mounted read write, but only for root. 

the mount command by itself on the commandline can show how a filesystem is mounted.
mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /nfssys type ext4 (rw,commit=0)
/dev/sdc1 on /home type ext4 (rw,commit=0)

shows that I have several devices mounted rw.

"fdisk -l" will show attached recognized partitions. 
usb devices can show as /dev/sd? where ? is a, b, c, or d.
or some other number.removing the device and plugging it back in may show you which one it is, and if it shows "ro" in the mount command instead of rw then you cannot make changes.

umount /dev/sd? 
mount /dev/sd? /mnt/mountpoint -o rw 
where ? is replaced by the partition listed in mount command ex:
my usb dev would show up as sdd w/ 1 partion

umount /dev/sda1
mount /dev/sda1 /mnt/sda1 -o rw

(/mnt/sda1 must exist before mounting, it's just a directory.)

Also possible, your usb device may have a physical write protect switch turned on.

---

