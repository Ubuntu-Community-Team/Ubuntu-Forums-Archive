---
title: "rsync problem when backing up to Windows PC on LAN"
date: 2010-10-10
forum: General Help
---

### Post by malleeblue on 2010-10-10
I would like assistance backing up from my Ubuntu computer to my Windows computer. In [this post]("http://ubuntuforums.org/showthread.php?p=9946396") I found out how to navigate the directories of my Windows computer. I thought that I'd be able to figure the backup process out but it hasn't happened.

This is test command line argument
```
sudo rsync -r -t -v --progress -u -i ssh /media/externalDrive1/folder1/ /home/username/.gvfs/windowsPC\ on\ winxppc/UbuntuBackup/folder1/
```

When I run it I get
```
sending incremental file list
rsync: link_stat "/ssh" failed: No such file or directory (2)
rsync: ERROR: cannot stat destination "/home/martin/.gvfs/windowsPC on winxppc/UbuntuBackup/folder1/": Permission denied (13)
rsync error: errors selecting input/output files, dirs (code 3) at main.c(573) [Receiver=3.0.7]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
```

I've tried it both with and without the "ssh" but no joy. What have I missed or, if I'm using the wrong thing, what do I need to do to make this work?

Thanks.

---

### Post by dcstar on 2010-10-10
> **malleeblue said:**
> I would like assistance backing up from my Ubuntu computer to my Windows computer. In [this post]("http://ubuntuforums.org/showthread.php?p=9946396") I found out how to navigate the directories of my Windows computer. I thought that I'd be able to figure the backup process out but it hasn't happened.

This is test command line argument
```
sudo rsync -r -t -v --progress -u -i ssh /media/externalDrive1/folder1/ /home/username/.gvfs/windowsPC\ on\ winxppc/UbuntuBackup/folder1/
```

When I run it I get
```
sending incremental file list
rsync: link_stat "/ssh" failed: No such file or directory (2)
rsync: ERROR: cannot stat destination "/home/martin**/.gvfs**/windowsPC on winxppc/UbuntuBackup/folder1/": Permission denied (13)
rsync error: errors selecting input/output files, dirs (code 3) at main.c(573) [Receiver=3.0.7]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
```

I've tried it both with and without the "ssh" but no joy. What have I missed or, if I'm using the wrong thing, what do I need to do to make this work?

Thanks.

You cannot copy Linux filenames to foreign filesystems that do not fully support them, like NTFS.

---

### Post by malleeblue on 2010-10-10
> **dcstar said:**
> You cannot copy Linux filenames to foreign filesystems that do not fully support them, like NTFS.

Thanks David, much appreciated. However could you explain something to me please? I already backup locally to an external HDD with is NTFS formatted. Why would I not be able to do what seems to be the same thing but instead over a LAN?

---

### Post by SeijiSensei on 2010-10-10
rsync creates temporary "dot" or "hidden" files while it copies an item, then renames it when the copy is complete.  NTFS can't handle those. The .gvfs directory in your file list is another example of a file without an NTFS equivalent.  In addition, you won't be able to preserve directory permissions, symlinks, or other *nix-specific filesystem objects.

You could use tar to create a compressed "tarball" of the directories you wish to back up and use cp to copy that.

tar cjvpf backup.tar.bz2 /directory [/directory [...]]

Type "man tar" at a terminal prompt for the full list of options.

---

