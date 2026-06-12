---
title: "Cryptsetup throwing warnings during upgrades"
date: 2012-04-03
forum: General Help
---

### Post by gcaplan on 2012-04-03
Hi

I have a Precise server running on a Xen VM. On upgrade, I frequently get the following warning from aptitude:

cryptsetup: WARNING: failed to detect canonical device of /dev/xvda1
cryptsetup: WARNING: could not determine root device from /etc/fstab

I haven't meddled with anything to do with disks and mounts, though my (highly experienced) ISP has added a mount for their backup system.

I'm not a sysadmin so any advice would be appreciated. Is this something that should concern me? If so, how do I fix it?

Here's a copy of /etc/fstab:

/dev/xvda1 /    ext3 noatime,errors=remount-ro 1 1
/dev/xvda2 none swap sw                        0 0
//backup-access-02.myhost.com/MyServer /backup/ cifs noauto,ro,user=MyServer 0 0

---

