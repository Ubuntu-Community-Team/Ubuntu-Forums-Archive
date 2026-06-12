---
title: "grsync/10.04"
date: 2012-04-15
forum: General Help
---

### Post by squrl on 2012-04-15
Can someone tell me if grsync can be used to backup to a network drive?
Thanks

---

### Post by papibe on 2012-04-15
Hi squrl.

Yes, but it has to be over ssh, or the rsync daemon has to be installed on the network drive's host.

If the network drive's host is a Linux machine, the usual way is to install the ssh server package:
```
sudo apt-get install openssh-server
```
Nevertheless, if it is Windows' share or a samba share, you can temporally mount the drive, and use grsync as you were syncing local directories.

I hope that helps, and tell us if you need more help.
Regards.

---

