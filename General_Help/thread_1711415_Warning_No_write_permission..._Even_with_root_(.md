---
title: "Warning: No write permission... Even with root :("
date: 2011-03-21
forum: General Help
---

### Post by mkhurram92 on 2011-03-21
hello all,

i am using Ubuntu 10.10 and login using root on terminal
but when i want to edit any file i get this error
 
"Warning: No write permission"

Also see the result of dhcp restart

root@webmin:~# /etc/init.d/dhcp3-server restart
 * Stopping DHCP server dhcpd3                                                                                                                                            [fail]
 * Starting DHCP server dhcpd3                                                                                                                                                   chown: changing ownership of `/var/lib/dhcp3': Read-only file system
chown: changing ownership of `/var/lib/dhcp3/dhcpd.leases': Read-only file system
chown: changing ownership of `/var/lib/dhcp3/dhcpd.leases~': Read-only file system
 * check syslog for diagnostics.


My System was working fine in the morning...
what happened i dont know and i m very confused about this situation 

Pls Help

Best Regards

---

### Post by WorMzy on 2011-03-21
If the filesystem encounters a serious error, it will remount the partition as read-only; I think this is probably what has happened.

I think the best thing for you to do is save any unsaved documents to a flashdrive or something, then reboot with the following command to force fsck to check the partition for errors (and fix them if possible)

```
sudo shutdown -rF now
```

---

