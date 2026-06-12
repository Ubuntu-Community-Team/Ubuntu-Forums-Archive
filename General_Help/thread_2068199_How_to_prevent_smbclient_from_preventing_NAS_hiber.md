---
title: "How to prevent smbclient from preventing NAS hibernation"
date: 2012-10-08
forum: General Help
---

### Post by stefangr1 on 2012-10-08
I notice that my NAS is no longer hybernating when I have Samba shares mounted from my server. Even when it is not accessing the mount, it is doing 'something' every minute.

I mount it using entries like the following in /etc/fstab:
```
//192.168.1.4/Series	/home/server/synology2/Series	cifs    guest,iocharset=utf8,codepage=unicode,unicode  0  0
```

What I would like is that the samba client *never* checks whether the samba shares are still accessible, but I've no idea how to do that...

---

### Post by stefangr1 on 2012-10-09
I've now written a simple script started by cron every 10 minutes that checks whether there are any users logged on to the system, and if that's not the case, checks whether the shares on the NAS are mounted. If appropriate, they are unmounted.

This works, but it's really second best and if someone knows a real solution I'd be happy to hear it...

---

