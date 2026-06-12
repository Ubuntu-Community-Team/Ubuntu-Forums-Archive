---
title: "Squid / SquidGuard User / Permission Error"
date: 2011-08-10
forum: General Help
---

### Post by rthwm on 2011-08-10
For 48 hours now ive been fighting with Squid / squidGuard trying to get this thing going.
 
Some where during my trial and error runs I managed to screw up some permissions.
 
squid log shows
logfileOpen: opening log /var/log/squid/access.log
FATAL: Cannot open '/var/log/squid/access.log' for writting.
 
(squidGuard): can't write to logfile /var/log/squid/squidGuard.log
(squidGuard): can't open configfile /etc/squid/squid
 
 
I started to get in trouble after reading another forum post somewhere and it recommened doing the following steps:
 
```

sudo chown proxy:proxy /etc/squid/squidGuard.conf
sudo chown -R proxy:proxy /var/lib/squidguard/db
sudo chown -R proxy:proxy /var/log/squid/
 
chmod 644 /etc/squid/squidGuard.conf
chmod -R 640 /var/lib/squidguard/db
chmod -R 644 /var/log/squid/

```
 
Now im not sure how to fix it. The folders show ownership being proxy, but Im not sure how or what the permissions are or how to change them to fix the error.
 
Any help with this would be greatly appreciated. Thanks in advanced.

---

### Post by rthwm on 2011-08-12
Ended up doing a complete re-install of Ubuntu, squid, and squidGuard to reset all the permissions and give me a fresh setup to work with. Have no clue what I did to mess it up before hand but everything appears to be working now.

---

