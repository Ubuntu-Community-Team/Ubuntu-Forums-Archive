---
title: "mounting vfat for a user"
date: 2011-04-25
forum: General Help
---

### Post by doccpu on 2011-04-25
How can i mount a dev (/dev/sdb1) of type vfat so i as a user can use it at boot. if i change /video to owner david i can use it at boot. But if fstab says mount /dev/sdb1 at /video it becomes owned by root and wont let root change owners.  even if fstab says rw,user i still cant mount or unmount /dev/sdb1 at /video

how do i mount a drive that motion can use to store files on?
[email]dhorner@usa.net[/email]

---

### Post by sisco311 on 2011-04-29
You can use the uid, gid, umask, dmask and fmask options to set the ownership and permissions of the files.

```
UUID="uuid-of-the-partition"   /mount/point    vfat   defaults,uid=username,gid=group,dmask=027,fmask=137   0   0
```


From [thread=283131]How to fstab[/thread]:
> **bodhi.zazen said:**
> 
**_VFAT/NTFS_**:

**Ownership and permissios of vfat / ntfs are set at the time of mounting**. This is often a source of confusion.
 
uid= Sets owner. Syntax: may use user_name or user ID #.
gid= sets group ownership of mount point. Again may use group_name or GID #.

umask can be used to set permissions if you wish to change the default.
Syntax is "odd" at first.
To set a permissions of 777, umask=000
To set permissions of 700, umask=077

[COLOR=blue]Best is to set directories with executable permissions and file with read write. To do this, use fmask and dmask (rather then umask):
dmask=027
fmask=137

With these options files are not executable (all colored green in a terminal w/ ls)[/COLOR]


---

