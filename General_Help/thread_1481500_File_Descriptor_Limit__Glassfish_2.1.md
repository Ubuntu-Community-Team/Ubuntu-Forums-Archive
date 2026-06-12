---
title: "File Descriptor Limit / Glassfish 2.1"
date: 2010-05-12
forum: General Help
---

### Post by natescott on 2010-05-12
I am using Ubuntu Jeos 8.04 in for a production Glassfish deployment.

The applications running in glassfish require an increased number of file descriptors. The glassfish service is running as a standard service user, so it has 1024 file descriptors by default. I have added the following in /etc/security/limits.conf

```

*               hard    nofile          16834
*               soft    nofile          16834

```After doing this, I can run my glassfish start script manually, and the file descriptor limit for the application works properly. However, **when I boot the system and glassfish starts automatically (using init), the default 1024 file limit is still in place**. Once I restart glassfish manually (using the script), it bumps back up to 16k.

So why is glassfish not getting started with the updated file descriptor limits on boot? I'm booting in runlevel 3 with a symlink at rc3.d/S90glassfish-domain1.

File: /etc/init.d/glassfish-domain1
```

#! /bin/sh

GLASSFISHPATH=/opt/glassfish/bin
DOMAINNAME=domain1

case "$1" in
start)
echo "starting glassfish from $GLASSFISHPATH"
sudo -u glassfish $GLASSFISHPATH/asadmin start-domain $DOMAINNAME
;;
restart)
$0 stop
$0 start
;;
stop)
echo "stopping glassfish from $GLASSFISHPATH"
sudo -u glassfish $GLASSFISHPATH/asadmin stop-domain $DOMAINNAME
;;
*)
echo $.usage: $0 {start|stop|restart}.
exit 3
;;
esac
:

```

---

