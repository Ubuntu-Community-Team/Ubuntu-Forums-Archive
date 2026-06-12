---
title: "asterisk init.d"
date: 2006-03-19
forum: General Help
---

### Post by ChrisStu on 2006-03-19
Hi,
I'm running asterisk on Breezy AMD64 and I am trying to add it to init.d. I have put this script in /etc/init.d:
```
#! /bin/sh
# $Id: asterisk,v 1.2 2004/07/18 20:24:07 Gregory Boehnlein <damin@nacs.net>
#
# asterisk	start the asterisk PBX
#
# Sun Jul 18 2004 Gregory Boehnlein <damin@nacs.net>
# - Updated Version to 1.2
# - Added test for safe_asterisk
# - Changed "stop gracefully" to "stop now"
# - Added support for -U and -G command line options
# - Modified "reload" to call asterisk -rx 'reload' 

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME=asterisk
DESC="Asterisk PBX"
# Full path to asterisk binary
DAEMON=/usr/sbin/asterisk

# Full path to safe_asterisk script
SAFE_ASTERISK=/usr/sbin/safe_asterisk

# Leave this set unless you know what you are doing.
export LD_ASSUME_KERNEL=2.4.1

# Uncomment the following and set them to the user/groups that you
# want to run Asterisk as. NOTE: this requires substantial work to
# be sure that Asterisk's environment has permission to write the
# files required  for  its  operation, including logs, its comm
# socket, the asterisk database, etc.
#AST_USER="asterisk"
#AST_GROUP="asterisk"

test -x $DAEMON || exit 0

set -e

case "$1" in
  start)
	echo -n "Starting $DESC: "
	if [ -f $SAFE_ASTERISK ] ; then
		DAEMON=$SAFE_ASTERISK
	fi
        if [ $AST_USER ] ; then
                ASTARGS="-U $AST_USER"
        fi
        if [ $AST_GROUP ] ; then
                ASTARGS="`echo $ASTARGS` -G $AST_GROUP"
        fi
	start-stop-daemon --start --exec $DAEMON -- $ASTARGS
	echo "$NAME."
	;;
  stop)
	echo -n "Stopping $DESC: "
	$DAEMON -rx 'stop now' > /dev/null 2> /dev/null && echo -n "$NAME"
	echo "."
	exit 0
	;;
  reload)
	echo "Reloading $DESC configuration files."
	$DAEMON -rx 'reload' > /dev/null 2> /dev/null
	;;
  restart|force-reload)
	$DAEMON -rx 'restart gracefully' > /dev/null 2> /dev/null && echo -n "$NAME"
	;;
  *)
	N=/etc/init.d/$NAME
	echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
	exit 1
	;;
esac

exit 0

```
But when I test it, I get this
root@richmond:/etc/init.d# /etc/init.d/asterisk start
Starting Asterisk PBX: start-stop-daemon: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
root@richmond:/etc/init.d#

I've tried adding /lib to PATH and LD_LIBRARY_PATH in the script above, but it makes no difference. Asterisk runs fine from the command line.

Any ideas what the problem is.

Regards,
Chris.

---

