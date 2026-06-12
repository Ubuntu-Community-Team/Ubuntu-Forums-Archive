---
title: "sync folders to a samba storage router (rsync)"
date: 2010-11-04
forum: General Help
---

### Post by gandaran on 2010-11-04
how do I go about using rsync or grsync to sync folders to a samba share in my storage router?
the samba share ip is [COLOR="DimGray"]smb://192.168.0.1/usb1-c/[/COLOR] tried using grsync but it says cant find smb!

---

### Post by CharlesA on 2010-11-04
You'd have to mount it on that machine.

If you are using Ubuntu desktop, just connect to the share with "connect to share" and then run rsync to sync it up.

The only transfer method that rsync supports is over SSH.

---

### Post by gandaran on 2010-11-04
the drive is mounted, I have full read/write access to it.
> The only transfer method that rsync supports is over SSH
this is something I don't know anything about it! how do I use SSH?

---

### Post by CharlesA on 2010-11-04
I meant that the share would need to be mounted, not the local drive.

I don't know if that router supports SSH or not, but the syntax is:

```
rsync user@host:source destination
```

---

### Post by gandaran on 2010-11-04
CharlesA
tried you command, doesn't work, this is th output error
> The source and destination cannot both be remote.
I don't understand it, the source is in my user directory!
using grsync gives this error
> ssh: Could not resolve hostname smb: Name or service not known
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
Rsync process exit status: 12
I don't know if this has anything to do with the problem but the thing is the samba share is password protected, its supposed to ask for the username and password when mounting the drive but in ubuntu 10.04 and 10.10 this no longer works, it just mounts the drive strait away while in windows it asks for the username and password!
another interesting fact is that in windows xp I have a backup program thats works backuping files without mounting the drive and no password but if I browse the drive then the username and password is required, funny how these drive shares work!
anyway I'm giving up for today, I will continue on this some other day,
and thanks for the answers.

---

### Post by CharlesA on 2010-11-04
> **gandaran said:**
> CharlesA
tried you command, doesn't work, this is th output error

I don't understand it, the source is in my user directory!
using grsync gives this error

I don't know if this has anything to do with the problem but the thing is the samba share is password protected, its supposed to ask for the username and password when mounting the drive but in ubuntu 10.04 and 10.10 this no longer works, it just mounts the drive strait away while in windows it asks for the username and password!
another interesting fact is that in windows xp I have a backup program thats works backuping files without mounting the drive and no password but if I browse the drive then the username and password is required, funny how these drive shares work!
anyway I'm giving up for today, I will continue on this some other day,
and thanks for the answers.

If it's already mounted, see where it is mounted by running this command:

```
mount
```

The syntax I gave you for rsync is for transfering files over SSH, the normal syntax is:

```
rsync source destination
```

---

### Post by gandaran on 2010-11-04
> If it's already mounted, see where it is mounted by running this command:
heres the output from mount command
> mfp@MSI:~$ mount
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
/dev/sda3 on /home type ext4 (rw,commit=0)
/dev/sda4 on /disco type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mfp/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mfp)
mfp@MSI:~$  
so in fact theres no mount point for the share drive, how would I mount it but temporally only, I don't want to add it to fstab, I am using mobile broadband now and only switch on the router to backup my files.

---

### Post by CharlesA on 2010-11-04
I think it's this, but not sure:

```
mount -t cifs -o username=server_user,password=secret //192.168.44.100/share /path_to/mount
```

From here: [http://opensuse.swerdna.org/susesambacifs.html](http://opensuse.swerdna.org/susesambacifs.html)

---

### Post by gandaran on 2010-11-04
> **CharlesA said:**
> I think it's this, but not sure:

```
mount -t cifs -o username=server_user,password=secret //192.168.44.100/share /path_to/mount
```

From here: [http://opensuse.swerdna.org/susesambacifs.html](http://opensuse.swerdna.org/susesambacifs.html)
thank you, that link is very good!
I used this one
> mount -t cifs -o guest //192.168.44.100/share /path_to/mount
mounts the drive without password and rsync now works beautifully!
but I'm a bit disappointed how this works, having to type the mount command (with sudo) in terminal to use the share drive, maybe its not worth using rsync at all, I am thinking its still better to just use copy and paste files to the local share drive!

---

### Post by CharlesA on 2010-11-04
> **gandaran said:**
> 
mounts the drive without password and rsync now works beautifully!
but I'm a bit disappointed how this works, having to type the mount command (with sudo) in terminal to use the share drive, maybe its not worth using rsync at all, I am thinking its still better to just use copy and paste files to the local share drive!

Yeah. If you can just mount the drive and throw files on it, why bother with rsync?

---

