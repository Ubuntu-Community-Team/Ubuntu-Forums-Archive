---
title: "How to write init.d Script?"
date: 2011-03-10
forum: General Help
---

### Post by opensource10 on 2011-03-10
Hello Ubuntu...

I have some questions here. could somebody guide me how to write init.d script or modify the skeleton code.

Actually, I want to add my programe called 'fw1loggrabber' to be added once the computer boot (without considering specific time / without CRON). I have check in internet, what should i do are create an init script then make a symbol link under /etc/rc2.d for start and stop the programe. 

I have modify "Skeleton" script that i find from /etc/init.d/ to be suitable to my programm  

```

popcorn:/# cat /etc/init.d/loggrabber
#! /bin/sh
### BEGIN INIT INFO
#
# Provides : fw1loggrabber
# Required-Start : $remote_fs
# Required-Stop  : $remote_fs
# Default-Start     : 2 3 4 5
# Default-Stop     : 0 1 6
# Short-Description : Example initscript
# Description : This file should be used to construct scripts to be placed in /etc/init.d.
#
### END INIT INFO

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/sbin:/usr/sbin:/bin:/usr/bin
DESC="Description of the Loggrabber"
NAME=fw1loggrabber
DAEMON=/usr/sbin/$NAME
DAEMON_ARGS="--options args"
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$NAME] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present
. /lib/lsb/init-functions

#
# Function that starts the daemon/service
#

do_start ()

{
    # Return 
    # 0 if daemon has been started
    # 1 if daemon was already running
    # 2 if daemon could not be started
    
    start-stop-daemon --start --quite --pidfile $PIDFILE --exec $DAEMON --test > /dev/null \
        || return 1
    start-stop-daemon --start --quite --pidfile $PIDFILE --exec $DAEMON -- \ 
        $DAEMON_ARGS \
        || return 2
        
    # Add code here, if necessary, that waits for the process to be ready
    # to handle requests from services started subsequently which depend
    # on this one.  As a last resort, sleep for some time.
}

#
# Function that stops the daemon/service
#
do_stop()
{
        # Return
        #   0 if daemon has been stopped
        #   1 if daemon was already stopped
        #   2 if daemon could not be stopped
        #   other if a failure occurred
        start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
        RETVAL="$?"
        [ "$RETVAL" = 2 ] && return 2
        # Wait for children to finish too if this is a daemon that forks
        # and if the daemon is only ever run from this initscript.
        # If the above conditions are not satisfied then add some other code
        # that waits for the process to drop all resources that could be
        # needed by services started subsequently.  A last resort is to
        # sleep for some time.
        start-stop-daemon --stop --quiet --oknodo --retry=0/30/KILL/5 --exec $DAEMON
        [ "$?" = 2 ] && return 2
        # Many daemons don't delete their pidfiles when they exit.
        rm -f $PIDFILE
        return "$RETVAL"
}

#
# Function that sends a SIGHUP to the daemon/service
#
do_reload() {
        #
        # If the daemon can reload its configuration without
        # restarting (for example, when it is sent a SIGHUP),
        # then implement that here.
        #
        start-stop-daemon --stop --signal 1 --quiet --pidfile $PIDFILE --name $NAME
        return 0
}

case "$1" in
  start)
        [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
        do_start
        case "$?" in
                0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
                2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
        esac
        ;;
  stop)
        [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
        do_stop
        case "$?" in
                0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
                2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
        esac
        ;;
  #reload|force-reload)
        #
        # If do_reload() is not implemented then leave this commented out
        # and leave 'force-reload' as an alias for 'restart'.
        #
        #log_daemon_msg "Reloading $DESC" "$NAME"
        #do_reload
        #log_end_msg $?
        #;;
  restart|force-reload)
        #
        # If the "reload" option is implemented then remove the
        # 'force-reload' alias
        # 
        log_daemon_msg "Restarting $DESC" "$NAME"
        do_stop
        case "$?" in
          0|1)
                do_start
                case "$?" in
                        0) log_end_msg 0 ;;
                        1) log_end_msg 1 ;; # Old process is still running
                        *) log_end_msg 1 ;; # Failed to start
                esac
                ;;
          *)
                # Failed to stop
                log_end_msg 1
                ;;
        esac
        ;;
  *)
        #echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
        echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
        exit 3
        ;;
esac

:
```Can somebody give an input or suggestion, whether i am on the correct way?

Thank you in advance. :)

---

### Post by howefield on 2011-03-10
Moved to "*General Help*".

---

### Post by cipherboy_loc on 2011-03-10
Duplicate thread, look here:

[http://ubuntuforums.org/showthread.php?t=1704166](http://ubuntuforums.org/showthread.php?t=1704166)

---

### Post by lithopsian on 2011-03-10
Does the script do what you want when you run it with the start and stop parameters?  If so, put it in ./etc/init.d ad create symlinks from all the runlevels where you want it to operate.  Use the symlink number to control the order of the scripts running.

runlevel 0 is shutdown and will run with the stop parameter.  runlevel 6 is reboot and will also run with stop.  All other runlevels run with the start parameter.  runlevel 1 is single user, runlevel 2 is the normal boot, and runlevels 3-5 are the same but not usually used.

---

### Post by howefield on 2011-03-10
Thanks cipherboy_loc, thread closed. 

Duplicate here : [http://ubuntuforums.org/showthread.php?t=1704166](http://ubuntuforums.org/showthread.php?t=1704166)

---

