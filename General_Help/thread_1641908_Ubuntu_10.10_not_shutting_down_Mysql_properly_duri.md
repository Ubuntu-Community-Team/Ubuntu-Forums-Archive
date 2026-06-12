---
title: "Ubuntu 10.10 not shutting down Mysql properly during reboot/shutdown?"
date: 2010-12-09
forum: General Help
---

### Post by damang111 on 2010-12-09
I have an mysql innodb ~ 20gigs.
Normally shutting down mysql (service mysql stop) takes a few seconds.
When I reboot Ubuntu with the reboot or shutdown command it just reboots it super fast without mysql logging (/usr/sbin/mysqld: Shutdown complete)
Also during this shutdown the following is failed:
umount2: device or resource busy
/data: device is busy.

mysql is setup to read from /data .
Why is ubuntu not waiting for mysql to properly shutdown before unmounting the filesystem and rebooting?

TIA

---

### Post by damang111 on 2010-12-10
so I found this:
[https://bugs.launchpad.net/ubuntu/+source/mysql-5.1/+bug/688541](https://bugs.launchpad.net/ubuntu/+source/mysql-5.1/+bug/688541)

this is a fairly major bug.
Why is this not getting more attention?

As a work around I have renamed the reboot command and created a new bash script for 'reboot' to shutdown mysql gracefully, wait few seconds, then run the real reboot command.

anyone else know why Ubuntu doesn't wait for mysql to properly terminate before Mysql is stopped?  how can something like this be overlooked so easily?

---

