---
title: "How to pass\change flags to init.d started deamon?"
date: 2011-12-26
forum: General Help
---

### Post by kamaradski on 2011-12-26
Hi all,

I installed and recompiled pure-ftpd on my xubuntu. The deamon is tarted with the standard /etc/init.d script that came with the original package.

When started a bunch of start-up flags are passed to the commandline, however i would like to change these flags.

- As i cannot see these flags in the init script, where do they come from ?
- And how can i change these flags to my liking ?

Cheers for any help,
kamaradski

---

### Post by 2F4U on 2011-12-26
I don't know pure-ftp, but usually applications have configuration options stored in a file, which is usually located in the /etc directory.

---

### Post by kamaradski on 2011-12-26
Thanks 2F4U for the reply :0

I checked in "/etc" and "/etc/pure-ftpd" for any config file that could be passing these start-up flags to the daemon, yet failed to discover anything that would help me.

I did however found a file in: "/etc/default/pure-ftpd-common". But unfortunately  this file seems not responsible for passing the flags to the start-up script.

Also i cannot see in the script where any external file is called except for this "pure-ftpd-common". Maybe in the part where it say:
```
if [ -h $0 ]; then
	ME=`/bin/readlink $0`
else 
	ME=$0
fi
```

As this is all symlink, and nothing tangible, i'm not educated enough to figure out where exactly is the information stored that i need.

**Anyway for completeness please find here the full start script:**
```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          pure-ftpd
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Should-Start:      slapd mysql postgresql-8.3 postgresql-8.4
# Should-Stop:       slapd mysql postgresql-8.3 postgresql-8.4
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
### END INIT INFO
#
# pure-ftpd	starts and stops the pure-ftpd ftp daemon
#
# Copyright 2002-2011 by Stefan Hornburg (Racke) <racke@linuxia.de>

PATH=/sbin:/bin:/usr/sbin:/usr/bin
NAME=pure-ftpd
DESC="ftp server"
: ${SSDAEMONLOGOPTS:="--quiet"}
UPLOADDAEMON=/usr/sbin/pure-uploadscript
UDNAME=pure-uploadscript
UDDESC="ftp upload handler"
WRAPPER=/usr/sbin/pure-ftpd-wrapper

# load LSB init-functions to get status_of_proc helper
. /lib/lsb/init-functions

PIDFILE=/var/run/pure-ftpd/pure-ftpd.pid

# try to figure with suffix this script is called,
# $0 might be a symlink pointing to this script
if [ -h $0 ]; then
	ME=`/bin/readlink $0`
else 
	ME=$0
fi

SUFFIX=`basename $ME | sed -ne 's/^pure-ftpd-\(.*\)/\1/p'`
if [ "$SUFFIX" ] ; then
	DAEMON=/usr/sbin/pure-ftpd-$SUFFIX
else
	DAEMON=/usr/sbin/pure-ftpd
fi

export STANDALONE_OR_INETD=standalone
export VIRTUALCHROOT=
test -r /etc/default/pure-ftpd-common && . /etc/default/pure-ftpd-common

if [ "$VIRTUALCHROOT" = "true" ]; then
	if [ "$SUFFIX" ]; then
		SUFFIX="$SUFFIX-virtualchroot"
	else
		SUFFIX="virtualchroot"
	fi
fi

test -x $DAEMON || exit 0
test -x $WRAPPER || exit 0

set -e

if [ ! -e `dirname $PIDFILE` ];then
       mkdir `dirname $PIDFILE`
fi

start_uploadscript() {
	if [ "$UPLOADSCRIPT" -a "$STANDALONE_OR_INETD" != inetd ] && \
		egrep -i '^[ 	]*(yes|1|on)[ 	]*' /etc/pure-ftpd/conf/CallUploadScript > /dev/null 2>&1
	then
		UOPTS=""
		test "$UPLOADUID" && UOPTS="$UOPTS -u $UPLOADUID"
		test "$UPLOADGID" && UOPTS="$UOPTS -g $UPLOADGID"
		echo -n "$1 $UDDESC: "
		start-stop-daemon --start $SSDAEMONLOGOPTS --oknodo \
			--exec $UPLOADDAEMON -- -r "$UPLOADSCRIPT" -B $UOPTS
		echo "$UDNAME."
		
	fi
}

case "$1" in
  start)
	test "$STANDALONE_OR_INETD" = standalone || exit 0
	echo -n "Starting $DESC: "
	start-stop-daemon --start $SSDAEMONLOGOPTS --pidfile "$PIDFILE" \
		--exec $WRAPPER -- $SUFFIX
	start_uploadscript Starting
	;;
  stop)
	echo -n "Stopping $DESC: "
	start-stop-daemon --stop $SSDAEMONLOGOPTS --oknodo \
		--pidfile "$PIDFILE"
	start-stop-daemon --stop $SSDAEMONLOGOPTS --oknodo --exec $UPLOADDAEMON
	echo "$NAME."
	;;
  restart|force-reload)
	test "$STANDALONE_OR_INETD" = standalone || exit 0
	echo -n "Restarting $DESC: "
	start-stop-daemon --stop $SSDAEMONLOGOPTS --oknodo \
		--pidfile "$PIDFILE"
	start-stop-daemon --stop $SSDAEMONLOGOPTS --oknodo --exec $UPLOADDAEMON
	sleep 1
	start-stop-daemon --start $SSDAEMONLOGOPTS --pidfile "$PIDFILE" \
		--exec $WRAPPER -- $SUFFIX
	start_uploadscript Restarting
	;;
  status)
	status_of_proc -p /var/run/pure-ftpd/pure-ftpd.pid $DAEMON $NAME && exit 0 || exit $?
	;;
  *)
	N=/etc/init.d/$NAME
	echo "Usage: $N {start|stop|restart|force-reload|status}" >&2
	exit 1
	;;
esac

exit 0

```

---

### Post by kamaradski on 2011-12-26
I figured it out :)

the script is calling a wrapper, and the wrapper is parsing the installed config, and the present config files in /etc/pure-ftpd/conf, then passes it on to the start-script.

To overwrite or influence this you can do one of a combination of the following:

- create the appropriate config files.
- add flags to the start-up script
- change the wrapper script

issue solved, Thanks.

---

