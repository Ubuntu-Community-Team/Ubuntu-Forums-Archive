---
title: "Unable to run scripts anywhere except for home folder"
date: 2010-11-16
forum: General Help
---

### Post by jsriz on 2010-11-16
I am trying to run a script in another partition of the hdd 
the file name is **new**
I ran ```
chmod +x new 
```both as normal and as sudo
but still get this error....
```

-bash: ./new: Permission denied

```

---

### Post by CharlesA on 2010-11-16
Does it have the noexec flag set?

What's the output of this:

```
mount
```

---

### Post by Tlingit on 2010-11-16
How are you initiating the script? Is the directory that you are in, in your environmental variables? These tell Linux what directories to look for the programs or scripts you want to run in.

post back if you need my help figuring that out.


Are you running chmod as su (root) or are you in the sudoers list?

Have you tried?

```
sudo chmod 755 file
```
```
sudo chown usernamehere file
```

```
man chown
```
```
man chmod
```

---

### Post by jsriz on 2010-11-16
> **CharlesA said:**
> Does it have the noexec flag set?

What's the output of this:

```
mount
```
here is the output of mount
```
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
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
gvfs-fuse-daemon on /home/srinivas/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=srinivas)
/dev/sdc1 on /media/SriZ Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```
the script needs to be run on /dev/sdc1

---

### Post by jsriz on 2010-11-16
> **Tlingit said:**
> How are you initiating the script? Is the directory that you are in, in your environmental variables? These tell Linux what directories to look for the programs or scripts you want to run in.
post back if you need my help figuring that out.
Are you running chmod as su (root) or are you in the sudoers list?
Have you tried?
```
sudo chmod 755 file
``````
sudo chown usernamehere file
``````
man chown
``````
man chmod
```
I just want to run a simple script hence am am going to the location of the file and then trying to use ./filename
i don't want to add it to the environment variables....
and yes i have tried both chown and chmod 755

---

### Post by WorMzy on 2010-11-16
NTFS doesn't support Linux file permissions, so you need to set them at mount time for them to work. After a NTFS partition is mounted, chmod, chown, etc. will not have any effect.

Try reading the following: [[COLOR="DarkGreen"]HOWTO: Mount NTFS partitions with specific ownership/permissions[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604251")

---

