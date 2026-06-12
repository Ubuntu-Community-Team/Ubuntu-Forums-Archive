---
title: "DBus error: Getting stuck on boot"
date: 2012-01-06
forum: General Help
---

### Post by dcabbar on 2012-01-06
Hi everyone,

While the machine is booting, the last thing I see is:

> 
/dev/sdb5: clean, 335375/27475968 files, 2111047/109889024 blocks (check in 3 mounts)
/dev/md1: clean, 4290219/57999360 files, 8601015/231982814 blocks


And, it gets stuck here forever. If I click on CTRL+ALT+DEL at this point, it says:

> 
unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory


But, continues with the boot process and everything seems normal!... 

My /run and /run/lock directories are already sym linked to /var/* (it was already like that). I changed the permissions as suggested, tried reinstalling dbus, tried removing /run/dbus/* before the reboot, but nothing helped!  It always gets stucked there after FS check???

This is driving  me crazy, and any help is appreciated.

Below is the full boot.log:

> 
fsck from util-linux 2.19.1
fsck from util-linux 2.19.1
fsck from util-linux 2.19.1
OS: clean, 73381/3055616 files, 1492685/12206574 blocks
/dev/sdb5: clean, 335375/27475968 files, 2111047/109889024 blocks (check in 3 mounts)
/dev/md1: clean, 4290219/57999360 files, 8601015/231982814 blocks
unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
 * Asking all remaining processes to terminate...       ^[[128G ^M^[[122G[ OK ]
mountall: Event failed
 * All processes ended within 1 seconds....       ^[[128G ^M^[[122G[ OK ]
 * Deconfiguring network interfaces...       ^[[128G ^M^[[122G[ OK ]
 * Starting AppArmor profiles       ^[[128G ^M^[[122G[ OK ]
 * Starting in-memory queueing server beanstalkd       ^[[128G ^M^[[122G[ OK ]
Starting memcached: memcached.
Starting MySQL
... *
Starting nginx: nginx.
 * Starting the Winbind daemon winbind       ^[[128G ^M^[[122G[ OK ]
 * Starting MD monitoring service mdadm --monitor       ^[[128G ^M^[[122G[ OK ]
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Fri Jan 06 17:43:36 2012] [warn] NameVirtualHost *:81 has no VirtualHosts
 * Starting web server apache2       ^[[128G ^M^[[122G[ OK ]


---

### Post by dcabbar on 2012-01-07
bump?

---

