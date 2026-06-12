---
title: "motion doesn't start on reboot"
date: 2011-12-24
forum: General Help
---

### Post by Cool Javelin on 2011-12-24
I am using Ubuntu 10.10 server (no GUI, no x) and I installed motion and have a 4 port video board.

when I reboot, motion doesn't start, (no pid in /var/run, no snapshots being created, etc...)

When I type, at a command prompt, 'sudo motion' it starts and works and leaves a pid in /var/run (as expected.)

FYI I changed the location if the pid file in motion.conf as the default was wrong.

In /etc/rc2.d .. /etc/rc5.d there is a link that points to a script called /etc/init.d/motion.

Here is that script.

```
#! /bin/sh -e
#
# /etc/init.d/motion: Start the motion detection
#
### BEGIN INIT INFO
# Provides:       motion
# Required-Start: $local_fs $syslog
# Required-Stop:
# Default-Start:  2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Start Motion detection
# Description: loads motion and assigns privileges
### END INIT INFO

# Ported to new debian way using sh and /lib/lsb/init-functions
# by Angel Carpintero <ack@telefonica.net>
# Modify by : Juan Angulo Moreno <juan@apuntale.com>
#             Eddy Petrisor <eddy.petrisor@gmail.com>

NAME=motion
PATH_BIN=/bin:/usr/bin:/sbin:/usr/sbin
DAEMON=/usr/bin/motion
PIDFILE=/var/run/$NAME.pid
DEFAULTS=/etc/default/$NAME

ENV="env -i LANG=C PATH=$PATH_BIN"

. /lib/lsb/init-functions

test -x $DAEMON || exit 0

RET=0

[ -r "$DEFAULTS" ] && . "$DEFAULTS" || start_motion_daemon=yes


check_daemon_enabled () {
    if [ "$start_motion_daemon" = "yes" ] ; then
        return 0
    else
        log_warning_msg "Not starting $NAME daemon, disabled via /etc/default/$NAME"
        return 1
    fi

}

case "$1" in
  start)
    if check_daemon_enabled ; then
        log_daemon_msg "Starting motion detection daemon : $NAME"
        if start-stop-daemon --start --oknodo --exec $DAEMON -b --chuid motion ; then
            log_end_msg 0
        else
            log_end_msg 1
            RET=1
        fi
    fi
    ;;

  stop)
    log_daemon_msg "Stopping motion detection daemon: $NAME"
    if start-stop-daemon --stop --oknodo --exec $DAEMON --retry 30 ; then
        log_end_msg 0
    else
        log_end_msg 1
        RET=1
    fi
    ;;

  reload|force-reload)
    log_daemon_msg "Reloading $NAME configuration"
    if start-stop-daemon --stop --signal HUP --exec $DAEMON ; then
        log_end_msg 0
    else
        log_end_msg 1
        RET=1
    fi
    ;;

  restart-motion)
    if check_daemon_enabled ; then
        log_action_begin_msg "Restarting $NAME"
        if $0 stop && $0 start ; then
            log_action_end_msg 0
        else
            log_action_cont_msg "(failed)"
            RET=1
        fi
    fi
    ;;

  restart)
    $0 restart-motion
    ;;

  *)
    echo "Usage: /etc/init.d/$NAME {start|stop|restart|reload}"
    RET=1
    ;;
esac

exit $RET

```

Thanks for any help

Mark.

---

### Post by Lampi on 2011-12-24
enable autostart in /etc/default/motion:

```
# set to 'yes' to enable the motion daemon
start_motion_daemon=yes
```

Edit: I remember there was the issue of /var/run/motion not being created with correct ownership/rights - see [this post on launchpad]("https://bugs.launchpad.net/ubuntu/+source/motion/+bug/294852/comments/4") how to fix it.

After that you should be set for autostart

---

### Post by Cool Javelin on 2011-12-25
I may have figured it out, just not sure how to fix it, see below row of ======='s

Thanks, Lampi:

I had forgotten about this when I made this thread, but had already dealt with it previously.

It was setup correctly, so that's not it

```
mark@aserver:/etc/default$ cat motion
# set to 'yes' to enable the motion daemon
start_motion_daemon=yes
```
-----------------------------------------------
an interesting thing to note, I went to cat the motion.conf file so I could paste it here, and couldn't read it.

It struck me the permissions may be off for motion.conf, but when I use sudo to start motion from the command line, it works.
But, I assume when the system is booting it is also starting it as root so there should be no difference.


```
mark@aserver:/etc/motion$ ll
total 72
drwxr-xr-x  2 root root    4096 2011-12-06 12:42 ./
drwxr-xr-x 98 root root    4096 2011-12-24 00:17 ../
-rw-r-----  1 root motion 23786 2011-12-17 00:06 motion.conf
-rw-r-----  1 root root   23979 2011-12-06 12:42 motion.conf.origonal
-rw-r--r--  1 root root    2107 2010-04-05 20:17 thread1.conf
-rw-r--r--  1 root root    2107 2010-04-05 20:17 thread2.conf
-rw-r--r--  1 root root    2110 2010-04-05 20:17 thread3.conf
-rw-r--r--  1 root root    2625 2010-04-05 20:17 thread4.conf

```
----------------------------------------------
As for the location of the pid file...

I had seen the suggested change in the init.d script from another website, but rejected that approach. Rather, I elected to put the pid file one level up and simply remove the subdir. So, that meant a change in motion.conf.

Here is the beginning of my motion.conf file

```
# Start in daemon (background) mode and release terminal (default: off)
daemon on

# File to store the process ID, also called pid file. (default: not defined)
process_id_file /var/run/motion.pid
```
========================================
========================================
I put a trace at the beginning of the /etc/init.d script to trap script output

```
set -x
exec 2>/home/mark/MotionBootTrace
```

Here is it's output

```
+ NAME=motion
+ PATH_BIN=/bin:/usr/bin:/sbin:/usr/sbin
+ DAEMON=/usr/bin/motion
+ PIDFILE=/var/run/motion.pid
+ DEFAULTS=/etc/default/motion
+ ENV=env -i LANG=C PATH=/bin:/usr/bin:/sbin:/usr/sbin
+ . /lib/lsb/init-functions
+ FANCYTTY=
+ [ -e /etc/lsb-base-logging.sh ]
+ . /etc/lsb-base-logging.sh
+ test -x /usr/bin/motion
+ RET=0
+ [ -r /etc/default/motion ]
+ . /etc/default/motion
+ start_motion_daemon=yes
+ check_daemon_enabled
+ [ yes = yes ]
+ return 0
+ log_daemon_msg Starting motion detection daemon : motion
+ [ -z Starting motion detection daemon : motion ]
+ log_use_usplash
+ [ n = y ]
+ type usplash_write
+ log_use_fancy_output
+ TPUT=/usr/bin/tput
+ EXPR=/usr/bin/expr
+ [ -t 1 ]
+ [ xlinux != x ]
+ [ xlinux != xdumb ]
+ [ -x /usr/bin/tput ]
+ [ -x /usr/bin/expr ]
+ /usr/bin/tput hpa 60
+ /usr/bin/tput setaf 1
+ [ -z ]
+ FANCYTTY=1
+ true
+ /usr/bin/tput xenl
+ /usr/bin/tput cols
+ COLS=80
+ [ 80 ]
+ [ 80 -gt 6 ]
+ /usr/bin/expr 80 - 7
+ COL=73
+ printf  * Starting motion detection daemon : motion
+ /usr/bin/expr 80 - 1
+ /usr/bin/tput hpa 79
+ printf
+ start-stop-daemon --start --oknodo --exec /usr/bin/motion -b --chuid motion
+ log_end_msg 0
+ [ -z 0 ]
+ log_use_usplash
+ [ n = y ]
+ type usplash_write
+ [ 73 ]
+ [ -x /usr/bin/tput ]
+ printf \r
+ /usr/bin/tput hpa 73
+ [ 0 -eq 0 ]
+ echo [ OK ]
+ return 0
+ exit 0

```

Nowhere in the script do I see it actually starting motion.

Am I miss reading it?

Mark

---

### Post by Lampi on 2011-12-25
can't help you there, but syslog sure can. just make sure whatever pidfile you are using has root:motion ownership and 775 rights

edit: had a look at my motion.conf and I noticed the following right at the top of the file:
```
# Start in daemon (background) mode and release terminal (default: off)
daemon on

# File to store the process ID, also called pid file. (default: not defined)
process_id_file /var/run/motion/motion.pid
```
make sure you have it the same way...

---

