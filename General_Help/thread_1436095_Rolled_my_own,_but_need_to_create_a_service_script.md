---
title: "Rolled my own, but need to create a service script"
date: 2010-03-22
forum: General Help
---

### Post by ant2ne on 2010-03-22
Using ubuntu 9.10 server, I've installed squid3 from the source code [using this tutorial]("http://www.ant2ne.com/?p=38") (work in progress) and squid is running. 

When installing from the source, squid does not set the service scripts. The documentation says something about distribution specific and too many possibilities etc. So what I did was a sudo apt-get install squid3 and then copied the /etc/init.d/squid script and made modifications to it.

```

#! /bin/sh
#
# squid3                Startup script for the SQUID HTTP proxy-cache.
#
# Version:      @(#)squid3.rc  1.0  07-Jul-2006  luigi@debian.org
#
### BEGIN INIT INFO
# Provides:          squid
# Required-Start:    $local_fs $network
# Required-Stop:     $local_fs $network
# Should-Start:      $named
# Should-Stop:       $named
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Squid HTTP Proxy version 3.0
### END INIT INFO

#NAME=squid3
NAME=squid
DESC="Squid HTTP Proxy 3.0"
#DAEMON=/usr/sbin/squid3
DAEMON=/usr/local/squid/sbin/squid
PIDFILE=/var/run/squid.pid
#CONFIG=/etc/squid3/squid.conf
CONFIG=/usr/local/squid/etc/squid.conf
SQUID_ARGS="-D -YC -f $CONFIG"

[ ! -f /etc/default/squid3 ] || . /etc/default/squid3

. /lib/lsb/init-functions

PATH=/bin:/usr/bin:/sbin:/usr/sbin:/usr/local/squid/sbin

[ -x $DAEMON ] || exit 0

ulimit -n 65535

find_cache_dir () {
        w="     " # space tab
        res=`sed -ne '
                s/^'$1'['"$w"']\+[^'"$w"']\+['"$w"']\+\([^'"$w"']\+\).*$/\1/p;
                t end;
                d;
                :end q' < $CONFIG`
        [ -n "$res" ] || res=$2
        echo "$res"
}

find_cache_type () {
        w="     " # space tab
        res=`sed -ne '
                s/^'$1'['"$w"']\+\([^'"$w"']\+\).*$/\1/p;
                t end;
                d;
                :end q' < $CONFIG`
        [ -n "$res" ] || res=$2
        echo "$res"
}

start () {
        cache_dir=`find_cache_dir cache_dir /var/spool/squid3`
        cache_type=`find_cache_type cache_dir ufs`

        #
    # Create spool dirs if they don't exist.
    #
        if [ "$cache_type" = "coss" -a -d "$cache_dir" -a ! -f "$cache_dir/stripe" ] || [ "$cache_type" != "coss" -a -d "$cache_dir" -a ! -d "$cache_dir/00" ]
        then
                log_warning_msg "Creating $DESC cache structure"
                $DAEMON -z
        fi

        umask 027
        ulimit -n 65535
        cd $cache_dir
        start-stop-daemon --quiet --start \
                --pidfile $PIDFILE \
                --exec $DAEMON -- $SQUID_ARGS < /dev/null
        return $?
}

stop () {
        PID=`cat $PIDFILE 2>/dev/null`
        start-stop-daemon --stop --quiet --pidfile $PIDFILE --exec $DAEMON
#        #
#        #       Now we have to wait until squid has _really_ stopped.
#        #
        sleep 2
        if test -n "$PID" && kill -0 $PID 2>/dev/null
        then
                log_action_begin_msg " Waiting"
                cnt=0
                while kill -0 $PID 2>/dev/null
                do
                        cnt=`expr $cnt + 1`
                        if [ $cnt -gt 24 ]
                        then
                                log_action_end_msg 1
                                return 1
                        fi
                        sleep 5
                        log_action_cont_msg ""
                done
                log_action_end_msg 0
                return 0
        else
                return 0
        fi

#       if ps -A | grep squid | grep -v PID 2> /dev/nul
#echo $PID
#       then
#               log_action_begin_msg " kill squid"
#               killall squid
#               return 0
#       else
#               log_action_begin_msg " nothing to kill"
#               return 0
#       fi
}

case "$1" in
    start)
        log_daemon_msg "Starting $DESC" "$NAME"
        if start ; then
                log_end_msg $?
        else
                log_end_msg $?
        fi
        ;;
    stop)
        log_daemon_msg "Stopping $DESC" "$NAME"
        if stop ; then
                log_end_msg $?
        else
                log_end_msg $?
        fi
        ;;
    reload|force-reload)
        log_action_msg "Reloading $DESC configuration files"
        start-stop-daemon --stop --signal 1 \
                --pidfile $PIDFILE --quiet --exec $DAEMON
        log_action_end_msg 0
        ;;
    restart)
        log_daemon_msg "Restarting $DESC" "$NAME"
        stop
        if start ; then
                log_end_msg $?
        else
                log_end_msg $?
        fi
        ;;
    *)
        echo "Usage: /etc/init.d/$NAME {start|stop|reload|force-reload|restart}"
        exit 3
        ;;
esac

exit 0

```
{You can see my feeble attempt at hacking this script as commented out}

I then did a 'sudo update-rc.d squid defaults'

It does start up on computer reboot. I can start the service with sudo /etc/init.d/squid start. But I can not stop or restart in this way (because it can't stop) using this script. I can stop squid with a sudo killall squid, but I'd like to get this working correctly.

---

### Post by gmargo on 2010-03-22
You could install the squid3 package from the repository, and see how they did it.

---

### Post by ant2ne on 2010-03-22
> **gmargo said:**
> You could install the squid3 package from the repository, and see how they did it.I tried that. Notice above where I say, > So what I did was a sudo apt-get install squid3 and then copied the /etc/init.d/squid script and made modifications to it.

---

### Post by gmargo on 2010-03-22
Sorry for my confusion... I don't see anything wrong with your script.  I believe you're saying that "/etc/init.d/squid3 stop" does not stop the squid3 daemon.  Any chance that new squid3 is configured to ignore SIGTERM? (seems unlikely)  My gut tells me it's something to do with the squid vs squid3 naming, but I can't see it.  You do have only this single version of squid installed, right?

Hmm. Any chance the new squid3 is forking so that the saved PID is wrong?  You can check the pid file against ps output.

---

