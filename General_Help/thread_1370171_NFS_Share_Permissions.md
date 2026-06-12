---
title: "NFS Share Permissions"
date: 2010-01-01
forum: General Help
---

### Post by Validatorian on 2010-01-01
Here's my situation -- I've got WHS running VMWare Workstation, which is running Ubuntu, which is running a program that demands a lot of storage. I want to put the files onto my main WHS drive, so I set up an NFS on the WHS, and linked to it from Ubuntu, so I can now access it via File Browser at:
smb://192.168.1.50/sharename

However, I cannot put an smb protocol link in as a directory to store files, so I mounted it to a folder using:
mount -t cifs //192.168.1.50/sharename /mnt/media -o user=username,password=password

This puts the mount in the folder just fine -- but read-only.

I need the functionality of the smb:// link (read/write) in the folder-structure that 'mount' provides. I have given access to everything I can think of on the windows side of things, but it doesn't seem to help.

---

### Post by Validatorian on 2010-01-02
This is the guide I used to set up NFS on WHS, if that helps.
[http://www.mediasmartserver.net/2009/12/11/guide-setting-up-nfs-in-whs/](http://www.mediasmartserver.net/2009/12/11/guide-setting-up-nfs-in-whs/)

---

### Post by Validatorian on 2010-01-02
I was able to link the HDD directly to Ubuntu using the fstab, but the changes seem to be local (not adding to the HDD, just a cache of the structure or something) so that's not working. If anyone can help me get Ubuntu correctly hooked up to an NFS, I'd really appreciate it.

---

