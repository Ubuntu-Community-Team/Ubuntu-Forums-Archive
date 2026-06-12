---
title: "Hard drive ownership problems"
date: 2011-01-14
forum: General Help
---

### Post by theonetruelord on 2011-01-14
Hi all!

I'm having some problems with my hard drive. I have all my Operating Systems installed on one hard drive, and all my media, documents etc on another. Yesterday I started having problems accessing my 2nd hard drive from Ubuntu. It seems to have become a read-only filesystem, which seems to have occured after using PySDM to try to get the hard drive to automatically mount at start up. This is quite a problem, because now I can't save anything!

I have tried using sudo chown -r (I found a few other threads advising this) but it doesn't seem to have made a difference. Help please!

Nick

---

### Post by XeonBloomfield on 2011-01-14
```
sudo nautilus /media/MOUNT_DIRECTORY
```

Right click on blank space > Properties > Permissions > Select "Group" - your username > Create and delete files

---

### Post by srs5694 on 2011-01-14
XeonBloomfield's suggestion won't help if the partition in question uses NTFS or FAT, as I suspect it does. In fact, his suggestion is equivalent to the "sudo chown" operation you've already attempted, just using a flashy GUI rather than the command-line tool. I'll proceed with the assumption that this is an NTFS or FAT filesystem.

I've never used PySDM, but a quick Google reveals it to be nothing but a point-and-click editor for /etc/fstab. Chances are you ended up creating an /etc/fstab entry that doesn't set the owner or permissions on files. This can be done by using one or more of the following options in the /etc/fstab entry for the partition in question:


[list]
[*]**uid=** -- This sets the user ID number for the owner of all files on the filesystem, as in "uid=1000" to give ownership to whoever has UID 1000 (the default first UID for ordinary users in Ubuntu).
[*]**gid=** -- This sets the group ID number to be associated with all files on the filesystem, much like the "uid=" option.
[*]**umask=** -- This option sets the umask for all files on the filesystem, which determines the permissions for all files and directories. Setting umask=000 gives everybody read/write access to all files; setting umask=027 gives the owner full access, members of the group read-only access, and everybody else no access; and so on. Google "umask" if you need more information.
[*]**fmask=** -- This option works just like umask, but it affects only files, not directories.
[*]**dmask=** -- This option works just like umask, but it affects only directories, not files.
[/list]


Since I've never used PySDM, I can't give you explicit instructions for using it to do the job. In a text editor, you'd edit the /etc/fstab entry for the partition in question, which might look like this:

```

/dev/sdb1      /mnt/wherever  ntfs    users,rw,uid=500    0 0

```

The options are in the fourth field -- "users,rw,uid=500" in this case. You'd add the options you want to use, or change any that might already be present, so you might end up with this:

```

/dev/sdb1      /mnt/wherever  ntfs    users,rw,uid=1000,fmask=113,dmask=002    0 0

```

---

### Post by srs5694 on 2011-01-14
Forum's acting up again and multi-posting.

---

### Post by srs5694 on 2011-01-14
Forum's acting up again and multi-posting!

---

