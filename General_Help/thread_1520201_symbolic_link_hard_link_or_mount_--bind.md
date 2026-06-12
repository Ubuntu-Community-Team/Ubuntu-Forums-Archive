---
title: "symbolic link hard link or mount --bind"
date: 2010-06-29
forum: General Help
---

### Post by lucacerone on 2010-06-29
Hi everybody,
I'd like to add in the fstab file a mounting point from a folder from
a secondary hd to /home/user directory.

I can mount manully the folder using:
```
sudo mount --bind /media/BckUP/Music /home/luca/Music 
```
and I would like this to be permanent, so I modified
the /etc/fstab file like this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=67d56e3f-a981-46f8-90c9-780b3a17b271 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6c00e4de-cada-429d-9554-366fe9c0d7da none            swap    sw              0       0
/media/BckUP/Music/ /home/luca/Music auto rw,suid,dev,exec,auto,nouser,async 0 0
```

This doesn't work. When I restart I get an error and can go on only skipping the mounting of the folder (ps the /media/BckUP/Music/ folder is on an ntfs filesystem).
Can you give me some help? I really have no idea where to start and what I'm doing wrong.. 
Cheers, -Luca

---

