---
title: "sudo required to save files to a Windows file server"
date: 2012-02-07
forum: General Help
---

### Post by toontu on 2012-02-07
Hi,

We have a Windows file server in the office. I use samba to connect to it. I can view and download files from the server as a normal user. However, if I want to make changes on the server, I have to prefix sudo before every command.

My question is that is this normal? Is it possible to remove this authentication requirement?

Many thanks.

---

### Post by imachavel on 2012-02-07
linux requires that all important decisions are made as root. It's very normal. I'm surprised you don't know this. I have myself not been able to share files between linux and windows pc. I have looked around for advice to edit samba.conf which I believe is found in bin or etc folder. No luck really. And the samba.conf file that is there, is a practice .conf file, not the real one. Well, I myself don't have a pc with a server operating system handing out dhcp i.p. addresses. So what can I say...

I figured there was a more practical way, through the router, to share files between the two OS using the i.p. address location on the network. But it seems both OS don't enjoy doing that. I'm not sure if samba is to help share files, or if it's only to give a windows computer access to linux, if linux itself is configured as a dhcp server, which I believe you configure using vi? Not sure

---

### Post by lechien73 on 2012-02-07
You don't specify the version of Windows running on your office server, but if it doesn't support CIFS Unix extensions, then - to quote the man page:

> For servers which do not support the CIFS Unix extensions, the default uid (and gid) returned on lookup of existing files will be the uid (gid) of the person who executed the mount (root, except when mount.cifs is configured setuid for user mounts) unless the "uid=" (gid) mount option is specified.

Therefore, to get full read/write access to networked windows shares you need to specify the uid/gid that the share should be mounted as. You probably have read/write access to the Windows share, but the mount point on your Linux box is (by default) owned by root.

How do you mount the share? If you do it from the command line, try the following:

```
mount -t cifs -o username=Windows_User,rw,uid=Linux_User,gid=Linux_Group //Windows_server_name/Share_name /mnt/mount_point
```

Where *Windows_User* is your Windows username, *Linux_User* is your Linux username, *Linux_Group* is the group ID (try 1000), and then change the paths to the server and mount point.

---

### Post by toontu on 2012-02-08
Hi lechien73,

Many thanks for your help. It's indeed very helpful. I have left a supporting message on your membership support thread. Good luck.

Cheers,

toon

---

