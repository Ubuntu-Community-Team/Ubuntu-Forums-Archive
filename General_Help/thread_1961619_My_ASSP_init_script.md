---
title: "My ASSP init script"
date: 2012-04-19
forum: General Help
---

### Post by dadevnull on 2012-04-19
Okay so here goes.  
Ubuntu 12 (precise)
Perl 5.14.2
ASSP 2.1.1

Backstory:
I have an ASSP server that is going to spam proxy for my Exchange server.  After beating my head against the infamous "dependency wall"  (mainly perl/ubuntu modules) for a few hours I have all the pieces in place, save for one.

Issue:
I have an init script for ASSP that seems to hang when invoked (but ASSP does start) whenever I reboot the system or try the "service assp start" command but when I launch ASSP from the command line with "perl assp.pl &" it works just fine.  All of the obvious things are kosher, paths, etc.

Here's the init script:

#!/bin/sh -e
# Start or stop ASSP (Anti-Spam SMTP Proxy)
#
# Script by Abey Marquez <abeymarquez@gmail.com>
#  v1.0.1 Changed 'force-reload' to force a restart if it can't reload the  config. Also changed 'restart' to start the proc if not running.
# v1.0.0 I'm not an expert but I tried to make this as LSB compliant as possible. Should work really nice with Ubuntu.

### BEGIN INIT INFO
# Provides:          ASSP (Anti-Spam SMTP Proxy)
# Required-Start:    $syslog, $local_fs
# Required-Stop:     $syslog, $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start or stop ASSP
# Description:       Start or stop ASSP (Anti-Spam SMTP Proxy)
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
NAME=assp.pl
HOME=/usr/share/assp
DAEMON=$HOME/$NAME
PIDFILE=$HOME/pid
INITSCRIPT=/etc/init.d/assp

. /lib/lsb/init-functions

case "$1" in
    start)
        log_daemon_msg "Starting ASSP (Anti-Spam SMTP Proxy)" "assp"
        start-stop-daemon --start --quiet --pidfile $PIDFILE --startas $DAEMON 2>&1 > /dev/null --chdir $HOME
        log_end_msg $?
        ;;
    stop)
        log_daemon_msg "Stopping ASSP (Anti-Spam SMTP Proxy)" "assp"
        start-stop-daemon --stop --quiet --pidfile $PIDFILE --chdir $HOME
        log_end_msg $?
        ;;
    restart)
        if [ -f $PIDFILE ]; then
            $0 stop
            sleep 1
            $0 start
        else
            $0 start
        fi
        ;;
    reload)
        log_action_begin_msg "Reloading ASSP (Anti-Spam SMTP Proxy) configuration"
        if [ -f $PIDFILE ]; then
            if kill -1 $(cat $PIDFILE); then
                log_action_end_msg 0
            else
                log_action_end_msg 1
            fi
        else
            log_action_end_msg 1
            exit 1
        fi
        ;;
    force-reload)
        log_action_begin_msg "Reloading ASSP (Anti-Spam SMTP Proxy) configuration"
        if [ -f $PIDFILE ]; then
            if kill -1 $(cat $PIDFILE); then
                log_action_end_msg 0
            else
                log_action_cont_msg "Could not reload configuration. Restarting"
                $0 restart
            fi
        else
            log_action_cont_msg "Could not reload configuration. Restarting"
            $0 restart
        fi
        ;;
    status)
        status_of_proc $DAEMON "ASSP (Anti-Spam SMTP Proxy)"
        ;;
    *)
        log_action_msg "Usage: $INITSCRIPT {start|stop|restart|reload|force-reload|status}"
        exit 1
        ;;
esac
exit 0

Question:
How would I go about troubleshooting this little issue?  Anyone?

Many thanks.

Update:  After boot up, if I SSH in and kill the s550assp process, the terminal states "terminated" and shows the login prompt.  ASSP is running.

---

