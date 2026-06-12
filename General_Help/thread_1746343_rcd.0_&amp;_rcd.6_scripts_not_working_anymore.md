---
title: "rcd.0 &amp; rcd.6 scripts not working anymore?"
date: 2011-05-01
forum: General Help
---

### Post by deckoff on 2011-05-01
I connect my NFS in /etc/fstab. there is a known bug, when connected through wireless, the system will have hang on shutdown screen when trying to shutdown  or restart  for 5-10 minutes. That is why I run his script

mountcfs
```

#!/bin/bash
#
# mountcifs - Unmounts samba-cifs filesystems
# -> convenience script to be called in the shutdown/reboot sequence of Ubuntu Dapper 
#    as K02umountcifs
# Written by Max Durden
# max.durden@gmail.com
#

umount -f /media/MyBookLive

exit 0

```It is set in /etc/int.d/ with symlinks K02mountcfs in /etc/rc0.d and /etc/rc6.d
It used to run ok in Kubuntu 10.10 , but for a reason it just stopped after upgrade???
Probably due to upstart update, any idea how to fix it?

---

