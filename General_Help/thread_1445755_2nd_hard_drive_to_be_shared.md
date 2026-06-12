---
title: "2nd hard drive to be shared"
date: 2010-04-03
forum: General Help
---

### Post by cliftonbazaar on 2010-04-03
My Ubuntu server has been serving me well for the last couple of months, now I wish to use it as a back up service for my family.

I have installed a 2nd hard drive, formated it and put several folders on it; but I cannot give permissions for other computers to access these folders.  Note that I can see the folders via Samba but it keeps telling me that the permissions are incorrect.
I have tried to change the permissions of the hard drive but they simply 'correct' themselves (I change it to anyone can 'read and write', it then changes it straight back).
All the folders have full permissions for guests.

---

### Post by sparky-steve on 2010-04-03
Navigate to one of the directories on the server hard drive that you wish to share and paste the output of 

```
ls -lash
```

Also, paste the section of your /etc/samba/smb.conf file that shares the above drive.


SS

---

### Post by cliftonbazaar on 2010-04-03
> **sparky-steve said:**
> Navigate to one of the directories on the server hard drive that you wish to share and paste the output of 

```
ls -lash
```


It's not the server hard drive I wish to share, it's another hard drive.  I also don't know how to change hard drives in the terminal :(

---

### Post by sparky-steve on 2010-04-03
Ok....

Hard drives are mounted to a location within /

So first and foremost, is the drive mounted. ie have you been using this second hard drive???

To see what is mounted, and where, you can type

```
mount
```

If you've not started to use the drive, and it hasn't been mounted, then the first thing you'll need to do is mount it. But there are alot of questions before you mount it for the first time.... Is it a brand new drive, or from a windows box? Does it have data you want to keep... If so, what FS is the drive? NTFS, FAT, EXT3, EXT4 ?  Would you like to format the drive?

Sorry but we've gone back a step, and need to do that before we can resume.

Good luck

SS

---

### Post by cliftonbazaar on 2010-04-03
Hard drive was wiped to use for the purposes of back ups.

I formatted it via File Browser and each time I go into File Browser it says that it is mounted

Going into Terminal and typing mount gives me 
```
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
none on /var/lib/ureadahead/debugfs type debugfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/www/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=www)
/dev/sdb1 on /media/Back Ups type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

```If i go into File Browser I can create a folder on the back up drive and then make it a share folder (full permissions for guests) but if I try to access it via another computer I can see the folder name but cannot enter it as it tells me that I don't have the permission.
If I try to change the permissions then I it changes them straight back :(

UPDATE - I have changed the name of the hard drive from 'Back Ups' to BackUps (deleted the space).

UPDATE - I reformatted the hard drive into ext4 format and everything works fine now.

---

