---
title: "uShare - Help with external HDD sharing"
date: 2011-05-17
forum: General Help
---

### Post by disco.sleeze on 2011-05-17
I have an external HDD called "My Passport". I'd like uShare to share the entire hard drive to stream media with my Xbox 360.

I have uShare running right now using a folder on my laptop's built in hard drive, but how would I go about finding the path to add to the config file so I can just stream the whole Passport?

---

### Post by blueridgedog on 2011-05-17
The command "mount" will give you the path that the passport external is mounted to and you can use that in your config file.

---

### Post by disco.sleeze on 2011-05-17
Okay, here is the output of my "mount" command in terminal:


> aron@aron-laptop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,user_xattr)
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
gvfs-fuse-daemon on /home/aron/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aron)
/dev/sdb1 on /media/My Passport_ type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

I tried a cd to /dev/sdb1 and /dev/sdb1/media/My Passport_ and to just /media/My Passport_

Every time I do one with "My Passport_" it says:
> bash: cd: /media/My: No such file or directory

So obviously the space is throwing it off. How much of that path do I use in the uShare config file, and how to I manage the space?

---

### Post by disco.sleeze on 2011-05-17
Okay, here is the output of my "mount" command in terminal:


> aron@aron-laptop:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,user_xattr)
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
gvfs-fuse-daemon on /home/aron/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aron)
/dev/sdb1 on /media/My Passport_ type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

I tried a cd to /dev/sdb1 and /dev/sdb1/media/My Passport_ and to just /media/My Passport_

Every time I do one with "My Passport_" it says:
> bash: cd: /media/My: No such file or directory

So obviously the space is throwing it off. How much of that path do I use in the uShare config file, and how to I manage the space?

---

### Post by blueridgedog on 2011-05-18
how about 

```
cd "/media/My Passport_"
```

I can help you mount it in a saner location if that interests you.  I don't know if uShare will take a mount path with spaces.

It is as simple as:

```
sudo umount /dev/sdb1
mkdir /home/USER/media
mount /dev/sdb1 /home/USER/media
```

(change USER to your user name and you can also change the path to a location that suits you).

If you get it working to your satisfaction, I can show you how to mount it that way every time you boot your system.

---

