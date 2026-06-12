---
title: "mount -o bind help"
date: 2010-12-01
forum: General Help
---

### Post by tad1073 on 2010-12-01
I need to automate the process of mounting certain directories into other directories. I have followed some tutorials about adding entries into fstab but it did not work for me. I was getting errors about unable to mount. I wrote a script but it stopped after the first line.

fstab example entry:
```
/media/Media/'My Music' /home/thomas/Music/ none,bind 0 0
```script example:
```
#!/bin/bash
sudo mount -o bind /media/Media/My\Movies /home/thomas/Videos/
sudo mount -o bind /media/Media/My\Music /home/thomas/Music/
sudo mount -o bind /media/Media/Documents /home/thomas/Documents/
sudo mount -o bind /media/Media/Downloads /home/thomas/Downloads/

```

---

### Post by sisco311 on 2010-12-01
In fstab, you have to substitute a space with \040.

```
/media/Media/My**\040**Music    /home/thomas/Music/    none    bind
```

---

### Post by tad1073 on 2010-12-01
> **sisco311 said:**
> In fstab, you have to substitute a space with \040.

```
/media/Media/My**\040**Music    /home/thomas/Music/    none    bind
```

yeah, I copied the entries in mtab,which has "**\40**"over to fstab but still no go.

---

### Post by sisco311 on 2010-12-02
> **tad1073 said:**
> yeah, I copied the entries in mtab,which has "**\40**"over to fstab but still no go.

Please post the error message you get when you try mounting them:
```
sudo mount -a
```

---

### Post by tad1073 on 2010-12-02
no errors...here is what I have in fstab

```
/dev/sdb3    /media/Media    ntfs-3g    defaults    0  0
/media/Media/Documents /home/thomas/Documents none rw,bind 0 0
/media/Media/Downloads /home/thomas/Downloads none rw,bind 0 0
/media/Media/My\040Music /home/thomas/Music none rw,bind 0 0
/media/Media/My\040Movies /home/thomas/Videos none rw,bind 0 0
/media/Media/Pictures /home/thomas/Pictures none rw,bind 0 0

```

---

### Post by sisco311 on 2010-12-02
> **tad1073 said:**
> no errors...


That means the fstab entries are correct.

> **tad1073 said:**
> 
here is what I have in fstab


They look okay.

I think, the problem is that during the boot, mountall tries to mount the bind mounts before sdb3 is mounted, hence it fails. 

Some similar bug reports:
[lpbug]524972[/lpbug]
[lpbug]519380[/lpbug]
[lpbug]459642[/lpbug]
[lpbug]503003[/lpbug]

---

### Post by tad1073 on 2010-12-07
Can some one give me a hand writing a script to automate mount -o bind, putting entries in fstab did not work.

---

### Post by sisco311 on 2010-12-07
Try writing an Upstart job.

/etc/init/mount-bind.conf:
```

#
# bind mounts
#

description "bind"

start on stopped mountall 

script
  mount --bind olddir newdir
  ...
end script

```

---

### Post by WorMzy on 2010-12-07
Have you tried removing the "rw" from the bind fstab entries? That may be confusing mountall, as NTFS partitions do not support Linux file permissions, and once such a partition is mounted, the permissions cannot be modified, especially for individual folders.

This tutorial should help you get past the "everything is owned by root" problem that arises when NTFS partitions are mounted by fstab: [[COLOR="DarkGreen"]HOWTO: Mount NTFS partitions with specific ownership/permissions[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604251")

---

### Post by tad1073 on 2010-12-07
> **sisco311 said:**
> Try writing an Upstart job.

/etc/init/mount-bind.conf:
```

#
# bind mounts
#

description "bind"

start on stopped mountall 

script
  mount --bind olddir newdir
  ...
end script

```

something like this
```
#
# bind mounts
#

description "bind"

start on runlevel [5]

script
  mount -o bind /media/Media/'My Movies' /home/thomas/Videos/
  mount -o bind /media/Media/'My Music' /home/thomas/Music/
  mount -o bind /media/Media/Documents /home/thomas/Documents/
  mount -o bind /media/Media/Downloads /home/thomas/Downloads/
  mount -o bind /media/Media/Pictures /home/thomas/Pictures/
  ...
end script
```

I have tried different combinations of the script and it is still not working.

---

### Post by tad1073 on 2010-12-07
> **WorMzy said:**
> Have you tried removing the "rw" from the bind fstab entries? That may be confusing mountall, as NTFS partitions do not support Linux file permissions, and once such a partition is mounted, the permissions cannot be modified, especially for individual folders.

This tutorial should help you get past the "everything is owned by root" problem that arises when NTFS partitions are mounted by fstab: [[COLOR=DarkGreen]HOWTO: Mount NTFS partitions with specific ownership/permissions[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1604251")

I am not too worried about permissions at the moment, all I am doing really is reducing number of clicks and ftping those files

---

### Post by tad1073 on 2010-12-10
bump

[http://ubuntuforums.org/showpost.php?p=10213342&postcount=10](http://ubuntuforums.org/showpost.php?p=10213342&postcount=10)

---

### Post by tad1073 on 2010-12-11
bump

---

