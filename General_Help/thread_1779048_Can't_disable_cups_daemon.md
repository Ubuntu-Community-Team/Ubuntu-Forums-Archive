---
title: "Can't disable cups daemon"
date: 2011-06-09
forum: General Help
---

### Post by ububaton on 2011-06-09
Fresh install of 10.04 x86_64.

I've tried to disable cups service from sysvinit scripts, but why cups is still starting with the computer?

```
root@computer:/home/user# update-rc.d cups disable
update-rc.d: warning: cups start runlevel arguments (none) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: cups stop runlevel arguments (none) do not match LSB Default-Stop values (1)
 Disabling system startup links for /etc/init.d/cups ...
 Removing any system startup links for /etc/init.d/cups ...
   /etc/rc1.d/K80cups
   /etc/rc2.d/S50cups
   /etc/rc3.d/S50cups
   /etc/rc4.d/S50cups
   /etc/rc5.d/S50cups
 Adding system startup for /etc/init.d/cups ...
   /etc/rc1.d/K80cups -> ../init.d/cups
   /etc/rc2.d/K50cups -> ../init.d/cups
   /etc/rc3.d/K50cups -> ../init.d/cups
   /etc/rc4.d/K50cups -> ../init.d/cups
   /etc/rc5.d/K50cups -> ../init.d/cups
```

---

### Post by andrewthomas on 2011-06-09
I answered your question at LQ.

[http://www.linuxquestions.org/questions/linux-newbie-8/cant-disable-cups-daemon-on-ubuntu-10-04-a-885505/](http://www.linuxquestions.org/questions/linux-newbie-8/cant-disable-cups-daemon-on-ubuntu-10-04-a-885505/)

---

### Post by ububaton on 2011-06-10
Your solution doesn't work, after reboot cups is still alive. 

```

$ ls -l /etc/rc.local 
-rwxr-xr-x 1 root root 324 2011-06-10 15:57 /etc/rc.local
$
$ cat /etc/rc.local 
#!/bin/sh -e
service cups stop
exit 0
```

after reboot:
```
$ ps -ae | grep -i cups
 1301 ?        00:00:00 cupsd
```

I'd like to know what config/program forces cups to autostart?

??

---

