---
title: "rsync --files-from and --delete options"
date: 2009-08-13
forum: General Help
---

### Post by reem.bs on 2009-08-13
Hey everybody

I'm having a rsync problem that I hope you can help me with

I want to auto backup a few selected dirs and files from my machine to a USB drive I have. I created a partition on the drive, and I want it to contain only the files and dirs I included.

This is the command I use

```
rsync -avr --progress --delete --log-file=/root/logs/$(date +%Y-%m-%d-%H%M)_rsync.log --files-from="/root/.rsync.include" / /media/Backup
```

I don't know if this is by-design or not, but when I use rsync with --files-from option the --delete option does nothing.

Any ideas about why this doesn't work or what I should do to get it working like I want?

Thanks

---

### Post by DaithiF on 2009-08-13
Hi, I believe this is by design ... the --delete option only applies for directories which rsync has been told to copy, basically it says copy its contents and then remove any files on the remote side which aren't in this directory locally.

however when running --files-from you are giving a list of specific files and directories -- the assumption being that it is a selective picklist, and that there are other files / directories in the local (and possibly remote) side that you want to keep.  So --delete doesn't get applied.

---

