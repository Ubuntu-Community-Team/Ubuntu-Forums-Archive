---
title: "fancontrol and shutdown"
date: 2011-01-07
forum: General Help
---

### Post by kripton on 2011-01-07
hey guys :D i have a problem with fancontrol as described here: [https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/563545]("https://bugs.launchpad.net/ubuntu/+source/lm-sensors-3/+bug/563545")... in this link there is a patch:```
diff -Nurp old/debian/fancontrol.init new/debian/fancontrol.init
--- old/debian/fancontrol.init	2010-04-24 19:38:52.000000000 +0400
+++ new/debian/fancontrol.init	2010-04-24 20:19:24.000000000 +0400
@@ -4,7 +4,7 @@
 # Provides:          fancontrol
 # Required-Start:    $remote_fs
 # Required-Stop:     $remote_fs
-# Default-Start:     2 3 4 5
+# Default-Start:     0 2 3 4 5 6
 # Default-Stop:
 # Short-Description: fancontrol
 # Description:       fan speed regulator
@@ -18,6 +18,7 @@ DAEMON=/usr/sbin/fancontrol
 DESC="fan speed regulator"
 NAME="fancontrol"
 PIDFILE=/var/run/fancontrol.pid
+OMITPIDFILE=/lib/init/rw/sendsigs.omit.d/fancontrol
 CONF=/etc/fancontrol
 
 test -x $DAEMON || exit 0
@@ -29,6 +30,8 @@ case "$1" in
 			log_daemon_msg "Starting $DESC" "$NAME"
 			start-stop-daemon --start --quiet --background --pidfile $PIDFILE --startas $DAEMON
 			log_end_msg $?
+			mkdir -p `dirname $OMITPIDFILE`
+			ln -s $PIDFILE $OMITPIDFILE
 		else
 			log_failure_msg "Not starting fancontrol, outdated configuration file; please re-run pwmconfig."
 		fi
@@ -42,6 +45,7 @@ case "$1" in
 	log_daemon_msg "Stopping $DESC" "$NAME"
 	start-stop-daemon --stop --quiet --pidfile $PIDFILE --oknodo --startas $DAEMON
 	rm -f $PIDFILE
+	rm -f $OMITPIDFILE
 	log_end_msg $?
 	;;
   restart) 
```
where i have to put this code? Thank's for the help

---

