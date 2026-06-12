---
title: "Hot to set save location of bittorrent in a network share folder in windows?"
date: 2011-01-14
forum: General Help
---

### Post by ayet on 2011-01-14
my ubuntu machine disk is already full, i want to set the save location of of bittorrent to a network share in windows is this possible?

---

### Post by cmoraes on 2011-01-14
Double-post: deleted

---

### Post by cmoraes on 2011-01-14
Yes it is.  Mount the Windows share as a directory in Ubuntu. For e.g.
```

mount -t smbfs //192.168.168.253/tmp /mnt/smbshare
```
And then configure bittorrent to save files in /mnt/smbshare.

Remember to create the directory "smbshare" before running the mount command.  FYI - you can create this directory anywhere.  For e.g. instead of /mnt/smbshare, you could use /home/johndoe/torrents

```

mount -t smbfs //192.168.168.253/tmp /home/johndoe/torrents
```

---

### Post by ayet on 2011-01-14
> **cmoraes said:**
> Yes it is.  Mount the Windows share as a directory in Ubuntu. For e.g.
```

mount -t smbfs //192.168.168.253/tmp /mnt/smbshare
```
And then configure bittorrent to save files in /mnt/smbshare.

Remember to create the directory "smbshare" before running the mount command.  FYI - you can create this directory anywhere.  For e.g. instead of /mnt/smbshare, you could use /home/johndoe/torrents

```

mount -t smbfs //192.168.168.253/tmp /home/johndoe/torrents
```

thanks for the reply.
after trying your code heres what appear on terminal.

root@ayet-desktop:~# mount -t smbfs //192.168.1.103/Movies /home/ayet/Desktop/php
mount: wrong fs type, bad option, bad superblock on //192.168.1.103/Movies,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

