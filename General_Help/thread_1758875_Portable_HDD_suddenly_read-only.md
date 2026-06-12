---
title: "Portable HDD suddenly read-only"
date: 2011-05-15
forum: General Help
---

### Post by evilbrent on 2011-05-15
My portable HDD is suddenly saying that I don't have write permission anymore.

properties>permissions says that I have full read/write permission over the top folder of the drive. After looking in the permissions I'm out of ideas.

I checked the properties of the drive itself and it said "Permissions could not be determined"

I haven't changed the permissions deliberately - I use this hard drive every other day to move movies across to my TV.

Can anyone help me get my drive back?

---

### Post by ambdeep on 2011-05-15
you can install storage device manager and change the properties from there.

---

### Post by evilbrent on 2011-05-15
Thanks. 

Installed storage device manager. Stupid question - how do I run the program? It's not showing up in Applications?

Any idea why the permissions would have gone kerflui in the first place?

---

### Post by Adacis on 2011-05-15
What Filesystem does your mobile HDD have? 
If it is NTFS it was propably not save unmounted and is now in dirty condition. Maybe ntfsfix helps or try moounting it with the force option.

---

### Post by evilbrent on 2011-05-15
vfat.

I try to be careful unplugging it from my computer, but I guess it could easily have been unplugged unsafely.

---

### Post by ajgreeny on 2011-05-15
Look at the mount point of the drive, rather than any folder within the drive itself, and change the permissions of that.

Neither fat32 or ntfs will allow linux permissions, so any changes need to be made on the mount folder.

---

### Post by evilbrent on 2011-05-15
I checked the properties of the drive itself and it said "Permissions could not be determined".

---

### Post by ajgreeny on 2011-05-15
> **evilbrent said:**
> I checked the properties of the drive itself and it said "Permissions could not be determined".
Did you look in /mnt or /media, or wherever the disk is mounted?

Is the disk automounted or do you use fstab to mount it at boot time?

---

### Post by evilbrent on 2011-05-15
I used Places>Computer and right-clicked Properties from that window. I guess it automounts, because I just plug it in and it shows up in Nautilus (I download movies then walk across my loungeroom to plug the HDD into the telly. So it is unplugged a lot in its life)

Also, I ran Mount with this output.

> brent@Bertha:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,user_xattr)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/brent/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brent)
**/dev/sdb1 on /media/x type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)**
/dev/sda2 on /media/867CF7DF7CF7C847 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)Doesn't that rw mean I've got read/write permissions?

---

### Post by ajgreeny on 2011-05-15
That output is exactly the same as I get when I plug in a fat32 usb disk, so I am now out of my depth, I'm afraid.

Are you sure the disk is still OK, eg on other machines or windows if you have a chance to test it somewhere else?

---

### Post by evilbrent on 2011-05-15
:-) no worries. Thanks anyway.

I guess I can try it at work tomorrow. 

Cheers.

---

### Post by evilbrent on 2011-05-15
I figured out how to run storage device manager, but it wasn't obvious how to use it to make my drive writeable.

I have discovered that if I unmount, then remount the drive, then as long as it's the first thing I do I can create a folder on the drive, and a folder within that one, but then I go into a pre-exisitng drive and get no such luck.

---

