---
title: "Problem getting 2nd NTFS hard drive detected"
date: 2010-11-21
forum: General Help
---

### Post by kanadabis on 2010-11-21
After looking through the forums, I haven't been able to find anything to properly help me. I am trying to mount a 2nd NTFS storage disk in my new installation on Ubuntu 10.10, I can see it in the disk manager, but cannot access the files, I tried following the steps on this on another thread and i got the following error:
[IMG]http://a.yfrog.com/img33/3166/screenshotcu.png[/IMG]
can anyone shed any light?

---

### Post by kanadabis on 2010-11-21
anyone?? this is really confusing ;(

---

### Post by oldfred on 2010-11-21
You have already made the mount point or directory. It remembers until you delete it.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

I do not like the GUI tools as I have had them put settings that I did not want and had to edit anyway.
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm](http://ubuntuforums.org/showthread.php?t=872197&highlight=pysdm)
Storage Device Manager - Worry-Free Fstab Configuration
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by kanadabis on 2010-11-21
Thank you for your reply fred, but I'm afraid I can't make sense out of this to do what i want. after reading through these pages i don't get how to unmount to drive i have! it doesn't seem to be listed in the dir of the terminal, but i can still see in disk manager, when i just click mount drive there, it says
 Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdb1 is already mounted on /
mount failed

This is rather confusing :(

---

### Post by oldfred on 2010-11-21
If you clicked on a drive to auto mount it, it shows twice in the left panel one with the triangle over a bar icon and one without. The second is pretty worthless but to unmount you have to use the one with the icon.

type this at terminal to see what is mounted.

```
mount
```

---

### Post by kanadabis on 2010-11-21
```
smurfy@Bluebox:~$ mount
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/smurfy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=smurfy)
/dev/sda1 on /mnt type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
```[FONT=monospace]


does this only mean that i have only 1 drive detected??
[/FONT]

---

### Post by oldfred on 2010-11-21
That only shows what is mounted. You have your root mounted on sdb1 and you have sda1 mounted on fuseblk which is other devices like NTFS. All the rest are internal.

To see all your partitions and drives:
```

sudo fdisk -lu
```

---

### Post by kanadabis on 2010-11-21
Thanks alot frank, after spending a few hours reading through those links and trying things over a bunch of times i finally got it to display, but the problem is now I cannot change the permissions of the whole drive, and thus cannot share it on the network, do you know what would be causing that?

---

### Post by oldfred on 2010-11-21
IF it is NTFS you cannot change permissions. Only by the mount in fstab or manually do you set permissions.

I gave up on Samba after several years as every update to windows or Ubuntu seemed to force me to reinstall. Usually the issue was Windows, firewalls, permissions etc. I ended up converting my portable to Ubuntu also and use NFS, a lot easier in my mind once I understood the settings.

---

