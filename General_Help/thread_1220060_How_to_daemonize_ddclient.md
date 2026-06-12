---
title: "How to daemonize ddclient?"
date: 2009-07-22
forum: General Help
---

### Post by jerome1232 on 2009-07-22
So I installed ddclient from opendns.org and got it working correctly. However I'm unsure what to do to daemonize it, there is a sample-etc_rc.d_init.d_ddclient.ubuntu which contains
```
#!/bin/sh
#
# Start ddclient that provides support for updating dynamic DNS services.
#
# Submitted by paolo martinelli

DDCLIENT=/usr/sbin/ddclient
CONF=/etc/ddclient/ddclient.conf
PIDFILE=/var/run/ddclient.pid

test -x $DDCLIENT || exit 0
test -f $CONF || exit 0

. /lib/lsb/init-functions

case "$1" in
start)
log_begin_msg "Starting ddclient..."
DELAY=`grep -v '^\s*#' $CONF | grep -i -m 1 "daemon" | awk -F '=' '{print $2}'`
if [ -z "$DELAY" ] ; then
DELAY="-daemon 300"
else
DELAY=''
fi
start-stop-daemon -S -q -p $PIDFILE -x $DDCLIENT -- $DELAY
log_end_msg $?
;;
stop)
if [ -f $PIDFILE ] ; then
log_begin_msg "Stopping ddclient..."
start-stop-daemon -K -q -p $PIDFILE
log_end_msg $?
rm -f $PIDFILE
fi
;;
restart|reload|force-reload)
$0 stop
$0 start
;;
*)
log_success_msg "Usage: $0 {start|stop|restart|reload|force-reload}"
exit 1
;;
esac

exit 0
```

Can I simply rename this to ddclient and copy this to /etc/init.d/ and all is good or is there more to it than that.

---

### Post by t4thfavor on 2009-07-22
It appears that you can. All a daemon is, is a detached from any console process started by the system. It appears to be starting the ddclient application, detaching the process, and getting a pid/lock file to avoid starting it again.

Good luck, let us know how it goes.

---

### Post by bacil on 2009-07-22
i would rather create symlink to /usr/sbin/ddclient in /etc/rc3.d and name it something like S99ddclient

---

### Post by jerome1232 on 2009-07-22
> **bacil said:**
> i would rather create symlink to /usr/sbin/ddclient in /etc/rc3.d and name it something like S99ddclient
After some more googling I copied the above script to /etc/init.d

Then I ended up using the update-rc.d script on /etc/init.d/ddclient which appears to have created symlinks in /etc/rc0.d to /etc/rc5.d, rebooting right now to see if it starts on boot up like I want.


Would creating that symlink you mentioned result in about the same thing?

---

### Post by t4thfavor on 2009-07-22
Yep, if you look in the init.d directory, I believe they are all symlinks.

---

### Post by bacil on 2009-07-22
except my one would start little bit earlier in level 3 instead of 5 :-) that means together with other services but before X

---

