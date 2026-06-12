---
title: "Change filesystem for /var partition then stopped at System Logger"
date: 2012-09-12
forum: General Help
---

### Post by eghost355 on 2012-09-12
I tried this procedure on: [http://ubuntuforums.org/showthread.php?p=12229538](http://ubuntuforums.org/showthread.php?p=12229538)

> **noMaster said:**
> I used *'-xzpvf '* and recovery was successful. Cheer! Thank you! :grin:

I tried but fail. Pls help me to debug. 
My procedures are:

0) already has another non-system partition up and running
1) backup /var by "cd /var; tar -czfvp ~/var.tar.gz ./*" (or "rsync -axS /var/* ~/var/")
2) reboot to rescueCD
3) mkfs.jfs /dev/sdc1 (/var partition)
4) mount -o noatime -t jfs /dev/sdc1 /mnt/var
5) restore /var content by "tar -xvzfp ~/var.tar.gz -C /mnt/var" (or "rsync -axS ~/var/* /mnt/var")
6) update system's /etc/fstab to change /var to JFS
7) reboot back to linux

Then it eventually hangs at "System Logger" then load any further. No viewable error can be seen.

Anything I missed? Thanks! :sad:

---

### Post by eghost355 on 2012-09-17
The error I saw in booting, after JFS the /var:
> **eghost355]
....
Bringing up interface eth0:   Device eth0 does not seem to be present, delaying initialization.&#12288 said:**
> 
Starting system logger:&#12288;&#12288;&#12288;&#12288;&#12288;[FAILED]
Starting system message bus:&#12288;&#12288;&#12288;&#12288;&#12288;[FAILED]
init:  Unable to connect to the system bus: Failed to connect to socket  /var/run/dbus/system_bus_socket: No such file or directory
Starting HAL daemon:&#12288;&#12288;&#12288;&#12288;&#12288;[FAILED]
Starting sshd:&#12288;&#12288;&#12288;&#12288;&#12288;[FAILED]


Do anyone know what could possibly goes wrong?

Thanks a lot!~

---

