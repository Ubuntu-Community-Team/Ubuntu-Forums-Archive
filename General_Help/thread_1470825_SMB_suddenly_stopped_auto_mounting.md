---
title: "SMB suddenly stopped auto mounting"
date: 2010-05-03
forum: General Help
---

### Post by seangee on 2010-05-03
I have my "documents" folder pointing to a Samba share on a 9.10 server. (Client is 64 bit 9.10). In /etc/fstab I have
```
//192.168.20.102/sean/Documents /home/sean/Documents cifs credentials=/home/sean/.smbcredentials,uid=1000,gid=1000
```This always used to mount automatically and has suddenly stopped. Same result if I use smbfs instead of cifs. I have worked around this by adding noauto and then mounting it in /etc/rc.local.

Anyone else had this and fixed it so that the share mounts at boot rather than login. I do have some cron tasks that require this to be mounted and assume they will fail unless I login immediately after a reboot.

---

### Post by PaulHuffman on 2010-05-03
I found your post looking for an answer to my similar problem. I have scripts that use smbmount to mount two windows shares that stopped working when I upgraded from 9.10 to 10.04.  I found this: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/563805]("https://bugs.launchpad.net/ubuntu/+source/samba/+bug/563805")

Seems to work for me to +s the /sbin/mount.cifs file.

---

