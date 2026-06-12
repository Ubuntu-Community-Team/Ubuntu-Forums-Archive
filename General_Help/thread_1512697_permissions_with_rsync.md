---
title: "permissions with rsync"
date: 2010-06-18
forum: General Help
---

### Post by Neezer on 2010-06-18
I'm trying to learn how rsync works to backup my system. I tried
```

rsync -azvv /home /media/Elements

```

I get a folder called home on my external hard drive but when I use ls -l to see the permissions they are all wrong. 

On my /home folder the permissions for /nathan are
drwxr-xr-x 48 nathan nathan

The permissions on the backup /nathan folder are
drwx------ 1 nathan nathan

I also tried using the long version of -a which is -rlptgoD and that didn't work either. 

What do the 48 and 1 mean when I used ls -l?

When I look in the /nathan folder the permissions are all screwed up too. A lot of the files are backed up as executables and the permissions are all screwed up. Any suggestions?

Oh yeah...I also ran it with sudo, and that didn't work either. The permissions were still screwed up and ownership is messed up too.

---

### Post by gzarkadas on 2010-06-18
Check first that you haven't set a 077 umask either in /etc/profile or in your ~/.profile. Use:
```

cat /etc/profile | grep umask
cat ~/.profile | grep umask

```and inspect the output.

Then check whether your external hard drive is ntfs-formatted; it may be an issue with the ntfs driver. Use rsync to copy your /home to a location in your filesystem such as /tmp/some-folder and inspect the permissions.

---

### Post by Neezer on 2010-06-18
> **gzarkadas said:**
> Check first that you haven't set a 077 umask either in /etc/profile or in your ~/.profile. Use:
```

cat /etc/profile | grep umask
cat ~/.profile | grep umask

```and inspect the output.

Then check whether your external hard drive is ntfs-formatted; it may be an issue with the ntfs driver. Use rsync to copy your /home to a location in your filesystem such as /tmp/some-folder and inspect the permissions.

I checked the umask stuff and it was 022. What is umask anyways? I put the backup to just /tmp and the permissions carried through. My external drive was ntfs. Is it most likely an ntfs issue?

If I use a drive that is ext3 or ext4 it should work then right?

---

### Post by gzarkadas on 2010-06-19
umask affects the permissions on files that you create. Its value is subtracted from 777 (that is rwxrwxrwx) to give the resulting permissions. Note that for files the x bits are off by default. Examples:

umask=022:   777 - 022 = 755  (rwxr-xr-x) for a directory ; 644 (rw-r--r--) for a file.
umask=077:   777 - 077 = 700  (rwx------) for a directory ; 600 (rw-r--r--) for a file.

The ntfs driver mounts drives by default with rwx------ permissions. You can try to change the umask of the drive to 022 when mounting. See [http://www.linux-ntfs.org/doku.php?id=ntfs-en#common_mount_options](http://www.linux-ntfs.org/doku.php?id=ntfs-en#common_mount_options). 

This may still give some issues with files that have different permissions (such as ssh keys, etc); they will become readable by other users on your system and you'll have to manually change permissions after restore. But those are usually minor annoyances in a single-user or family computer.

If you are not going to use the drive with other operating systems converting it to ext4 is probably the best option.

---

