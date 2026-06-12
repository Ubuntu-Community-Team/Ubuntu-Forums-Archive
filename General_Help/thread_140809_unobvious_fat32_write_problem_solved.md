---
title: "unobvious fat32 write problem solved"
date: 2006-03-07
forum: General Help
---

### Post by vayu on 2006-03-07
I just spent a painful amount of time trying to access a fat32 partition.  I couldn't write to it.  To make a long story short, If you have a directory assigned as "My Documents" it won't have write access in Linux even when fstab has rw,umask=000 in it.  The work around is to use the dos attrib command on the directory from a windows command line.  attrib -r "directoryname" will remove a read only setting that Linux apparently respects (everything I read said the read/write access is supposed to come from the mount/fstab parameters).

---

### Post by dcstar on 2006-03-07
[QUOTE=vayu]I just spent a painful amount of time trying to access a fat32 partition.  I couldn't write to it.  To make a long story short, If you have a directory assigned as "My Documents" it won't have write access in Linux even when fstab has rw,umask=000 in it.  The work around is to use the dos attrib command on the directory from a windows command line.  attrib -r "directoryname" will remove a read only setting that Linux apparently respects (everything I read said the read/write access is supposed to come from the mount/fstab parameters).[/QUOTE]
Well, no.

You are given the option to be able to potentially write to a mount point - or just have read-only access to it, that option will not override attributes set on the individual file structures.

If you wanted to reset the attribute for that particular directory, then you could have as the "owner" of the mount (root, most likely).

---

### Post by vayu on 2006-03-09
[QUOTE=dcstar]Well, no.

You are given the option to be able to potentially write to a mount point - or just have read-only access to it, that option will not override attributes set on the individual file structures.

If you wanted to reset the attribute for that particular directory, then you could have as the "owner" of the mount (root, most likely).[/QUOTE]


Except that I mounted it in fstab with uid and gid set to my user.  A directory listing would confirm that my user was the owner and yet I couldn't access it until I went to dos and used attrib -r on it.

---

