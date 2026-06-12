---
title: "locked out of a HDD sudo wont work"
date: 2009-11-11
forum: General Help
---

### Post by jwflammer on 2009-11-11
i have a TB drive and it has an older ubuntu Linux and when i updated it, the TB crashed. live disk sees all the files but i can't copy or back them up. sudo nautilus wont let me eather nor will terminal commands alone with just sudo cp and sudo makedir help me these are important school files !!

---

### Post by alphaniner on 2009-11-11
When you have the drive mounted (ie. you can see the files on the drive) what is the output of **mount** in the terminal?

---

### Post by jwflammer on 2009-11-11
output of mount in the terminal? ok how do i do that ??

---

### Post by jwflammer on 2009-11-11
right now im looking at ubuntu@ubuntu:/$ in terminal and i can with out sudo view the hole drive but cant make changes or copy

---

### Post by alphaniner on 2009-11-11
Type 'mount' then press Enter.  Copy the output and paste it here in code tags (the # button in the message formatting tools)

---

### Post by jwflammer on 2009-11-11
```

ubuntu@ubuntu:/$ mount
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
/dev/sdg1 on /media/cf2bd90b-0cef-4aa1-9e14-377d2d5b62c5 type ext4 (rw,nosuid,nodev,uhelper=devkit)
/dev/sda1 on /media/42B9-F63B type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
ubuntu@ubuntu:/$ 

```

---

### Post by alphaniner on 2009-11-11
OK, which drive are you having trouble with:

/dev/sdg1 on /media/cf2bd90b-0cef-4aa1-9e14-377d2d5b62c5

or

/dev/sda1 on /media/42B9-F63B

?

---

### Post by jwflammer on 2009-11-11
/dev/sda1 on /media/42B9-F63B

i cant mkdir or cp to back things up i mean i see all my files but nothings allowing me to copy them over to another device also i want to back up to it since it is a TB HDD

---

### Post by alphaniner on 2009-11-11
So are you trying to copy things *from* /media/42B9-F63B?  Or *to* it?

/media/42B9-F63B is formatted vfat so you shouldn't have any trouble writing to it.

On the other hand, /media/cf2bd90b-0cef-4aa1-9e14-377d2d5b62c5 is formatted ext4 so it wouldn't be surprising if you have trouble writing to it.

---

### Post by jwflammer on 2009-11-11
yeah i know im completely shocked i cant copy make new folders or back things up to another drive from files on it !! i dont know !! and no its the fat drive that's giving me problems

---

### Post by jwflammer on 2009-11-11
im getting this read out when i do mkdir in root 

```

root@ubuntu:/media/42B9-F63B/backup# mkdir laptop-backup
mkdir: cannot create directory `laptop-backup': Read-only file system

```

---

### Post by alphaniner on 2009-11-11
> **jwflammer said:**
> im getting this read out when i do mkdir in root 

```

root@ubuntu:/media/42B9-F63B/backup# mkdir laptop-backup
mkdir: cannot create directory `laptop-backup': Read-only file system

```

That doesn't make any sense to me either.  The output of **mount** shows that it is mounted read-write:

```
/dev/sda1 on /media/42B9-F63B type vfat (**rw**,nosuid...)
```

---

### Post by jwflammer on 2009-11-11
yeah i knoe all the other document ive read says take the steps ive done could it be a bad load of the live disk ??

---

### Post by jwflammer on 2009-11-11
ok ill be back im going to put in the live cd of the os thats on here !!

---

### Post by alphaniner on 2009-11-11
Well, I kinda doubt it's the LiveCD.  You said there was a crash at some point, right?  It seems more likely that the filesystem got a bit messed up.

---

