---
title: "Using mount to connect to Windows share"
date: 2011-01-03
forum: General Help
---

### Post by wolfgangmcq on 2011-01-03
I am trying to connect to a Windows share. In Nautilus, I can select File>Connect to server..., choose Windows share, then connect. However, I want to mount the share to a folder on the filesystem, and connecting in Nautilus doesn't do this. It would work if I could use mount from the command line, like:
```
sudo mount -t ntfs -o username=winuser,password=winpass,uid=ubuntuuser smb://server/path/to/share/ /winshare/

```
But I can't get this to work, mostly because I can't figure out how to specify the server on the network. I tried looking this up on the internet, all I can find is how to mount a drive on /dev/sdaN.

---

### Post by TSJason on 2011-01-03
You need to connect using the cifs fs type since ntfs is not a network filesystem. Something like this:


```
sudo mount -t cifs -o username=winuser,password=winpass,uid=ubuntuuser //server/path/to/share/ /winshare

```

---

### Post by wolfgangmcq on 2011-01-04
```
$ sudo mount -t cifs -o username=winuser,password=winpass,uid=ubuntuuser //server/path/to/share/ /winshare
mount: wrong fs type, bad option, bad superblock on //server/path/to/share/,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```dmesg|tail turns up one relevant entry:```
CIFS VFS: cifs_mount failed w/return code = -22
```So I tried installing the package cifs-utils, and it works!
Thanks for your help!

---

