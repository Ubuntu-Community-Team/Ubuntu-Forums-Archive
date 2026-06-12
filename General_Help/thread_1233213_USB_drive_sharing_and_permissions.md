---
title: "USB drive sharing and permissions"
date: 2009-08-06
forum: General Help
---

### Post by banoncom on 2009-08-06
Hi all.

I have come up with a problem and I am hoping there is a way around it.

On an Ubuntu 9.04 desktop running samba server I have an external FAT USB drive which I have shared on the network to be accessed by windows boxes. The share can be seen but it cannot be accessed. WHen attempted it asks for usrename password however it will not accept my credentials.

I have looked at the permissions on the drive when it is mounted, the owner is myself however the group is root and permissions are rwx______ so group and others have no permissions at all.

I have tried to "sudo chown" and "sudo chmod" the mount point (/media/disk1 but it just rejects the commands with permission denied.

I have tried to create a folder in my home directory and mount /dev/sdb1 to it - no probs but when mounted ownership and permissions are set to root:root and rwx______. So I still cant change permissions on it.

There must be a way to mount the drive so that I can change the permissions so the share can be accessed? any ideas?

Cheers.

---

