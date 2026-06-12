---
title: "a weird problem with init.d"
date: 2009-11-12
forum: General Help
---

### Post by pajoohesh on 2009-11-12
[COLOR="Blue"]Hello folks,

I want to start tor at startup and everything seems to be correct but I have no idea why it does not start there.
Clues:
I have /etc/init.d/tor script and I can run it by start command.

I also have /etc/rc2.d/S20tor link and the runlevel is N 2.

I have installed tor from [http://ppa.launchpad.net/f4l3/ppa/ubuntu]("http://ppa.launchpad.net/f4l3/ppa/ubuntu").

1st Suspicion: previously I could run tor by /etc/init.d/tor start command and after starting the control was back to command line but now it just writes 100% circuit established and never comes back to command line.

2nd suspicion: after starting with the above method which starts tor service perfectly I can not stop it and it gives me this error:
> Stopping tor daemon: not running (there is no /var/run/tor/tor.pid).

any suggestions?
Regards,[/COLOR]

---

### Post by hal10000 on 2009-11-12
> 1st Suspicion: previously I could run tor by /etc/init.d/tor start command and after starting the control was back to command line but now it just writes 100% circuit established and never comes back to command line.

If the cursor does'nt come back to the command line, then the startup script may be corrupt.

---

### Post by pajoohesh on 2009-11-12
[COLOR="Blue"]The startup script is this:
Unfortunately I can not find its problem:[/COLOR]
```
#! /bin/bash

### BEGIN INIT INFO
# Provides:          tor
# Required-Start:    $local_fs $remote_fs $network $named $time
# Required-Stop:     $local_fs $remote_fs $network $named $time
# Should-Start:      $syslog
# Should-Stop:       $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Starts The Onion Router daemon processes
# Description:       Start The Onion Router, a TCP overlay
#                    network client that provides anonymous
#                    transport.
### END INIT INFO

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/tor
NAME=tor
DESC="tor daemon"
TORPIDDIR=/var/run/tor
TORPID=$TORPIDDIR/tor.pid
DEFAULTSFILE=/etc/default/$NAME
WAITFORDAEMON=60
ARGS=""
# Let's try to figure our some sane defaults:
if [ -r /proc/sys/fs/file-max ]; then
	system_max=`cat /proc/sys/fs/file-max`
	if [ "$system_max" -gt "80000" ] ; then
		MAX_FILEDESCRIPTORS=32768
	elif [ "$system_max" -gt "40000" ] ; then
		MAX_FILEDESCRIPTORS=16384
	elif [ "$system_max" -gt "10000" ] ; then
		MAX_FILEDESCRIPTORS=8192
	else
		MAX_FILEDESCRIPTORS=1024
		cat << EOF

Warning: Your system has very few filedescriptors available in total.

Maybe you should try raising that by adding 'fs.file-max=100000' to your
/etc/sysctl.conf file.  Feel free to pick any number that you deem appropriate.
Then run 'sysctl -p'.  See /proc/sys/fs/file-max for the current value, and
file-nr in the same directory for how many of those are used at the moment.

EOF
	fi
else
	MAX_FILEDESCRIPTORS=8192
fi

NICE=""

test -x $DAEMON || exit 0

# Include tor defaults if available
if [ -f $DEFAULTSFILE ] ; then
	. $DEFAULTSFILE
fi

wait_for_deaddaemon () {
	pid=$1
	sleep 1
	if test -n "$pid"
	then
		if kill -0 $pid 2>/dev/null
		then
			echo -n "."
			cnt=0
			while kill -0 $pid 2>/dev/null
			do
				cnt=`expr $cnt + 1`
				if [ $cnt -gt $WAITFORDAEMON ]
				then
					echo " FAILED."
					return 1
				fi
				sleep 1
				echo -n "."
			done
		fi
	fi
	return 0
}


check_torpiddir () {
	if test ! -d $TORPIDDIR; then
		#echo "There is no $TORPIDDIR directory.  Creating one for you."
		mkdir -m 02700 "$TORPIDDIR"
		chown debian-tor:debian-tor "$TORPIDDIR"
	fi

	if test ! -x $TORPIDDIR; then
		echo "Cannot access $TORPIDDIR directory, are you root?" >&2
		exit 1
	fi
}

check_config () {
	if ! $DAEMON --verify-config > /dev/null; then
		echo "ABORTED: Tor configuration invalid:" >&2
		$DAEMON --verify-config >&2
		exit 1
	fi
}


case "$1" in
  start)
	if [ "$RUN_DAEMON" != "yes" ]; then
		echo "Not starting $DESC (Disabled in $DEFAULTSFILE)."
		exit 0
	fi

	if [ -n "$MAX_FILEDESCRIPTORS" ]; then
		echo -n "Raising maximum number of filedescriptors (ulimit -n) to $MAX_FILEDESCRIPTORS"
		if ulimit -n "$MAX_FILEDESCRIPTORS" ; then
			echo "."
		else
			echo ": FAILED."
		fi
	fi

	check_torpiddir

	echo "Starting $DESC: $NAME..."
	check_config

	start-stop-daemon --start --quiet --oknodo \
		--pidfile $TORPID \
		$NICE \
		--exec $DAEMON -- $ARGS
	echo "done."
	;;
  stop)
	echo -n "Stopping $DESC: "
	pid=`cat $TORPID 2>/dev/null` || true

	if test ! -f $TORPID -o -z "$pid"; then
		echo "not running (there is no $TORPID)."
		exit 0
	fi

	if start-stop-daemon --stop --signal INT --quiet --pidfile $TORPID --exec $DAEMON; then
		wait_for_deaddaemon $pid
		echo "$NAME."
	elif kill -0 $pid 2>/dev/null
	then
		echo "FAILED (Is $pid not $NAME?  Is $DAEMON a different binary now?)."
	else
		echo "FAILED ($DAEMON died: process $pid not running; or permission denied)."
	fi
	;;
  reload|force-reload)
	echo -n "Reloading $DESC configuration: "
	pid=`cat $TORPID 2>/dev/null` || true

	if test ! -f $TORPID -o -z "$pid"; then
		echo "not running (there is no $TORPID)."
		exit 0
	fi

	check_config

	if start-stop-daemon --stop --signal 1 --quiet --pidfile $TORPID --exec $DAEMON
	then
		echo "$NAME."
	elif kill -0 $pid 2>/dev/null
	then
		echo "FAILED (Is $pid not $NAME?  Is $DAEMON a different binary now?)."
	else
		echo "FAILED ($DAEMON died: process $pid not running; or permission denied)."
	fi
	;;
  restart)
	check_config

	$0 stop
	sleep 1
	$0 start
	;;
  *)
	echo "Usage: $0 {start|stop|restart|reload|force-reload}" >&2
	exit 1
	;;
esac

exit 0
```

---

### Post by hal10000 on 2009-11-12
I also can't find an error in the script, but i see it's going to log events to /var/log/syslog.

So maybe you can find some error if you check /var/log/syslog and/or /var/log/messages.

I suppose you first start to watch syslog on a terminal window:
```
 tail -f -n 30 /var/log/syslog
```
This command logs permanently the last 30 lines of your syslog file.

Then, on another terminal window (re)start tor:
```
sudo /etc/init.d/tor restart 
```

If you go back to the terminal window where you started the syslog watching, then you should see wether issues related to tor are logged.

---

### Post by pajoohesh on 2009-11-12
```
sudo /etc/init.d/tor restart
Stopping tor daemon: not running (there is no /var/run/tor/tor.pid).
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
Nov 12 15:52:29.088 [notice] Tor v0.2.1.19. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Nov 12 15:52:29.088 [notice] Initialized libevent version 1.4.11-stable using method epoll. Good.
Nov 12 15:52:29.088 [notice] Opening Socks listener on 127.0.0.1:9050
Nov 12 15:52:29.088 [warn] Could not bind to 127.0.0.1:9050: Address already in use. Is Tor already running?
Nov 12 15:52:29.088 [warn] Failed to parse/validate config: Failed to bind one of the listener ports.
Nov 12 15:52:29.088 [err] Reading config failed--see warnings above.
```

[COLOR="RoyalBlue"]and there is not any log related to tor in both /var/log/messages and /var/log/syslog.

also there is a valid config file for tor in /etc/tor/torrc. I think because the control does not come back to commandline, tor is not considered as a running program and no PID is associated with it.
[/COLOR]

---

