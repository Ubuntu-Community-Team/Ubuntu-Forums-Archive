---
title: "NTFS mount issue"
date: 2010-06-22
forum: General Help
---

### Post by bbgarber on 2010-06-22
I must have something wrong, I'm trying to mount, in fstab, a NTFS hard drive with the following entry...

```
UUID=90F451D9F451C260 /media/backup ntfs-3g defaults,locale=en_US.utf8,umask=0    0 0
```

and when I check it with a ls -alF, I see that everything belongs to root:root, with full permissions. However, when I try to change file permissions with sudo chmod, nothing happens. Next I checked how the drive was actually mounted with "mount" and saw the following...

```
/dev/sdb1 on /media/backup type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
```

Also, I'm not sure how to describe this best, but when I look at the files in the /media/backup directory with ls -alF, all of the sub-directories are highlighted in green. With my other drive, the sub-directories are just in blue letters (even if they belong to root:root).

Is this an issue with a NTFS mount, or with the way I've mounted the drive?

Thanks,
Brian

---

### Post by bbgarber on 2010-06-23
Nevermind... according to NTFS-3G Manual at Tuxera... [http://www.tuxera.com/community/ntfs-3g-manual/]("http://www.tuxera.com/community/ntfs-3g-manual/")

> By default, files and directories are owned by the effective user and group of the mounting process and everybody has full read, write, execution and directory browsing permissions. You can also assign permissions to a single user by using the uid and/or the gid options together with the umask,  or fmask and dmask options.

I still don't get the reason why ls shows the directory color as highlighted green. Any insight to that?

Thanks,
Brian

---

### Post by sisco311 on 2010-06-23
> **bbgarber said:**
> 
I still don't get the reason why ls shows the directory color as highlighted green. Any insight to that?


It's because the directories are writable by others. See:
```
man ls | less +/--color
man dircolors
dircolors -p
```

---

