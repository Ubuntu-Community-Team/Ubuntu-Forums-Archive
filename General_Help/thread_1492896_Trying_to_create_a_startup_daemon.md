---
title: "Trying to create a startup daemon"
date: 2010-05-25
forum: General Help
---

### Post by scawa on 2010-05-25
I posted this in the Installation and Setup forum but was told to post in another forum.....  So here goes.


I installed ActiveMQ, set up an init.d script and was able to start | stop | restart ActiveMQ from the init.d script.  However, when I tried to use:

>sudo chkconfig --add activemq

upstart seemed not to like it.  Having NO documentation on how to create a daemon that works with Upstart on the Ubuntu forums, I'm wondering if anyone has any idea why my init.d script doesn't convert.

I'm using Ubuntu 10.x.x but this happens on 9.x.x also.

Here is my script..

```

#!/bin/bash
#
### BEGIN INIT INFO
# Provides:          activemq
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Should-Start:      $network $named $time
# Should-Stop:       $network $named $time
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
#chkconfig: 345 88 12
# Short-Description: Start and stop the ActiveMQ server daemon
# Description:       Controls the main ActiveMQ (JMS Messaging Queue Server) daemon
#                    and its wrapper script "mysqld_safe".
# chckconfig:        345 88 12
### END INIT INFO
test -s /etc/rc.status && . /etc/rc.status && rc_reset
# Script Startup variables
JAVA=/usr/bin/java
HOME=/opt/activemq/bin
PLATFORM=linux-x86-64
NAME=ActiveMQ
LONG_NAME=="${NAME} Broker"
# Process ID
PIDDIR="/var/run"
PIDFILE="${PIDDIR}/${NAME}.pid"
LOCKDIR="/var/lock/subsys"
LOCKFILE="$LOCKDIR/$NAME"
WRAPPER_CMD="wrapper"
WRAPPER_CONF="wrapper.conf"

PWD_CMD=`pwd`

# Resolve the location of the 'ps' command
PSEXE="/usr/bin/ps"
if [ ! -x $PSEXE ]; then
   PSEXE="/bin/ps"
   if [ ! -x $PSESE ]; then
      echo "Unable to locate the 'ps' command."
      echo "Please report this message along with the locarion of the command on your system."
      exit 1
   fi
fi

# Resolve the os
DIST_OS=`uname -s | tr [:upper:] [:lower:] | tr -d [:blank:]`
case "$DIST_OS" in
    'sunos')
        DIST_OS="solaris"
        ;;
    'hp-ux' | 'hp-ux64')
        DIST_OS="hpux"
        ;;
    'darwin')
        DIST_OS="macosx"
        ;;
    'unix_sv')
        DIST_OS="unixware"
        ;;
esac
echo "OS $DIST_OS"
# Resolve the architecture
DIST_ARCH=`uname -p 2>/dev/null | tr [:upper:] [:lower:] | tr -d [:blank:]`
if [ "$DIST_ARCH" = "unknown" ] || [ "$DIST_ARCH" = "" ]
then
    DIST_ARCH=`uname -m | tr [:upper:] [:lower:] | tr -d [:blank:]`
fi
echo "DIST_ARCH: $DIST_ARCH"
case "$DIST_ARCH" in
    'amd64' | 'ia32' | 'ia64' | 'i386' | 'i486' | 'i586' | 'i686' | 'x86_64')
        DIST_ARCH="x86"
        ;;
    'ip27')
        DIST_ARCH="mips"
        ;;
    'power' | 'powerpc' | 'power_pc' | 'ppc64')
        DIST_ARCH="ppc"
        ;;
    'pa_risc' | 'pa-risc')
        DIST_ARCH="parisc"
        ;;
    'sun4u' | 'sparcv9')
        DIST_ARCH="sparc"
        ;;
    '9000/800')
        DIST_ARCH="parisc"
        ;;
esac
echo "ARCH $DIST_ARCH"
# Decide on the wrapper binary to use.
# If a 32-bit wrapper binary exists then it will work on 32 or 64 bit
#  platforms, if the 64-bit binary exists then the distribution most
#  likely wants to use long names.  Otherwise, look for the default.
# For macosx, we also want to look for universal binaries.
WRAPPER_TEST_CMD="$HOME/$DIST_OS-$DIST_ARCH-64/$WRAPPER_CMD"
echo "Wraper test cmd $WRAPPER_TEST_CMD"
if [ -x $WRAPPER_TEST_CMD ]
then
    WRAPPER_CMD="$WRAPPER_TEST_CMD"
else
    if [ "$DIST_OS" = "macosx" ]
    then
        WRAPPER_TEST_CMD="$WRAPPER_CMD-$DIST_OS-universal-32"
        if [ -x $WRAPPER_TEST_CMD ]
        then
            WRAPPER_CMD="$WRAPPER_TEST_CMD"
        else
            WRAPPER_TEST_CMD="$WRAPPER_CMD-$DIST_OS-$DIST_ARCH-64"
            if [ -x $WRAPPER_TEST_CMD ]
            then
                WRAPPER_CMD="$WRAPPER_TEST_CMD"
            else
                WRAPPER_TEST_CMD="$WRAPPER_CMD-$DIST_OS-universal-64"
                if [ -x $WRAPPER_TEST_CMD ]
                then
                    WRAPPER_CMD="$WRAPPER_TEST_CMD"
                else
                    if [ ! -x $WRAPPER_CMD ]
                    then
                        echo "Unable to locate any of the following binaries:"
                        echo "  $WRAPPER_CMD-$DIST_OS-$DIST_ARCH-32"
                        echo "  $WRAPPER_CMD-$DIST_OS-universal-32"
                        echo "  $WRAPPER_CMD-$DIST_OS-$DIST_ARCH-64"
                        echo "  $WRAPPER_CMD-$DIST_OS-universal-64"
                        echo "  $WRAPPER_CMD"
                        exit 1
                    fi
                fi
            fi
        fi
    else
        WRAPPER_TEST_CMD="$WRAPPER_CMD-$DIST_OS-$DIST_ARCH-64"
        if [ -x $WRAPPER_TEST_CMD ]
        then
            WRAPPER_CMD="$WRAPPER_TEST_CMD"
        else
            if [ ! -x $WRAPPER_CMD ]
            then
                echo "Unable to locate any of the following binaries:"
                echo "  $WRAPPER_CMD-$DIST_OS-$DIST_ARCH-32"
                echo "  $WRAPPER_CMD-$DIST_OS-$DIST_ARCH-64"
                echo "  $WRAPPER_CMD"
                exit 1
            fi
        fi
    fi
fi
# Build the nice clause
if [ "X$PRIORITY" = "X" ]
then
    CMDNICE=""
else
    CMDNICE="nice -$PRIORITY"
fi

# Build the anchor file clause.
if [ "X$IGNORE_SIGNALS" = "X" ]
then
   ANCHORPROP=
   IGNOREPROP=
else
   ANCHORPROP=wrapper.anchorfile=$ANCHORFILE
   IGNOREPROP=wrapper.ignore_signals=TRUE
fi

# Build the lock file clause.  Only create a lock file if the lock directory exists on this platform.
if [ -d $LOCKDIR ]
then
    LOCKPROP=wrapper.lockfile=$LOCKFILE
else
    LOCKPROP=
fi
getpid() {
    if [ -f $PIDFILE ]
    then
        if [ -r $PIDFILE ]
        then
            pid=`cat $PIDFILE`
            if [ "X$pid" != "X" ]
            then
                # It is possible that 'a' process with the pid exists but that it is not the
                #  correct process.  This can happen in a number of cases, but the most
                #  common is during system startup after an unclean shutdown.
                # The ps statement below looks for the specific wrapper command running as
                #  the pid.  If it is not found then the pid file is considered to be stale.
                pidtest=`$PSEXE -p $pid -o args | grep $WRAPPER_CMD | tail -1`
                if [ "X$pidtest" = "X" ]
                then
                    # This is a stale pid file.
                    rm -f $PIDFILE
                    echo "Removed stale pid file: $PIDFILE"
                    pid=""
                fi
            fi
        else
            echo "Cannot read $PIDFILE."
            exit 1
        fi
    fi
}

testpid() {
    pid=`$PSEXE -p $pid | grep $pid | grep -v grep | awk '{print $1}' | tail -1`
    if [ "X$pid" = "X" ]
    then
        # Process is gone so remove the pid file.
        rm -f $PIDFILE
        pid=""
    fi
}

# Test for the existance of certain apps
test_for_app () 
{
   app_found=0
   if [ "f" = "$2" ] && [ -f $1 ]; then
      app_found=1
   elif [ "x" = "$2" ] && [ -x $1 ]; then
      app_found=1
   fi

   if [ 0 = $app_found ]; then
     echo  "Warning: Could not find required file: $1"
     if [ "$1" = "stop" ]; then
        exit 0
     else
        exit 5
     fi
     update-rc.d -v
     exit

   fi
   return
}

console() {
    echo "Running $APP_LONG_NAME..."
    getpid
    if [ "X$pid" = "X" ]
    then
        COMMAND_LINE="$CMDNICE $WRAPPER_CMD $WRAPPER_CONF wrapper.syslog.ident=$APP_NAME wrapper.pidfile=$PIDFILE $ANCHORPROP $LOCKPROP"
        exec $COMMAND_LINE
    else
        echo "$APP_LONG_NAME is already running."
        exit 1
    fi
}

test_for_app ${JAVA} x
test_for_app ${HOME} x
test_for_app ${HOME}/${PLATFORM} x



usage ()
{
   echo ""
   echo "Usage: $0 <command>"
   echo ""
   echo "where <command> is one of the following:"
   echo "   start   - starts ActiveMQ if it not running."
   echo "   stops   - stops ActiveMQ if it is running."
   echo "   restart - stop and start ActiveMQ"
   echo "   usage   - pring this message"
   echo ""
}

do_start() {
    echo "Starting $APP_LONG_NAME..."
    getpid
    if [ "X$pid" = "X" ]
    then
        COMMAND_LINE="$CMDNICE $WRAPPER_CMD $WRAPPER_CONF wrapper.syslog.ident=$APP_NAME wrapper.pidfile=$PIDFILE wrapper.daemonize=TRUE $ANCHORPROP $IGNOREPROP $LOCKPROP"
        exec $COMMAND_LINE
    else
        echo "$APP_LONG_NAME is already running."
        exit 1
    fi

}
do_stop() {
    echo "Stopping $APP_LONG_NAME..."
    getpid
    if [ "X$pid" = "X" ]
    then
        echo "$APP_LONG_NAME was not running."
    else
        if [ "X$IGNORE_SIGNALS" = "X" ]
        then
            # Running so try to stop it.
            kill $pid
            if [ $? -ne 0 ]
            then
                # An explanation for the failure should have been given
                echo "Unable to stop $APP_LONG_NAME."
                exit 1
            fi
        else
            rm -f $ANCHORFILE
            if [ -f $ANCHORFILE ]
            then
                # An explanation for the failure should have been given
                echo "Unable to stop $APP_LONG_NAME."
                exit 1
            fi
        fi

        # We can not predict how long it will take for the wrapper to
        #  actually stop as it depends on settings in wrapper.conf.
        #  Loop until it does.
        savepid=$pid
        CNT=0
        TOTCNT=0
        while [ "X$pid" != "X" ]
        do
            # Show a waiting message every 5 seconds.
            if [ "$CNT" -lt "5" ]
            then
                CNT=`expr $CNT + 1`
            else
                echo "Waiting for $APP_LONG_NAME to exit..."
                CNT=0
            fi
            TOTCNT=`expr $TOTCNT + 1`

            sleep 1

            testpid
        done

        pid=$savepid
        testpid
        if [ "X$pid" != "X" ]
        then
            echo "Failed to stop $APP_LONG_NAME."
            exit 1
        else
            echo "Stopped $APP_LONG_NAME."
        fi
    fi

}
do_status() {
    getpid
    if [ "X$pid" = "X" ]
    then
        echo "$APP_LONG_NAME is not running."
        exit 1
    else
        echo "$APP_LONG_NAME is running ($pid)."
        exit 0
    fi
}

case "$1" in
    start)
      do_start
      exit
      ;;
    stop)
      do_stop
      exit
      ;;
    restart)
      do_stop
      do_start
      exit
      ;;
    status)
      do_status
      exit
      ;;
    usage|help)
         usage
         exit 0
         ;;
esac

```

And here is just SOME of the errors I get trying to do this:

```

The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'ufw' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'dmesg' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `networking' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `wpa-ifupdown' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-stop' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'console-setup' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'apport' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'mysql' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'failsafe-x' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0) of script `halt' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `umountnfs.sh' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'irqbalance' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'cron' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevtrigger' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udev-finish' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-splash' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hwclock-save' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'plymouth-log' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `sendsigs' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface-security' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'udevmonitor' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'module-init-tools' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'network-interface' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'rsyslog' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'hostname' missing LSB tags and overrides
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'atd' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (6) of script `reboot' overwrites defaults (empty).
insserv: warning: current start runlevel(s) (0 6) of script `umountfs' overwrites defaults (empty).
The script you are attempting to invoke has been converted to an Upstart
job, but lsb-header is not supported for Upstart jobs.
insserv: warning: script 'procps' missing LSB tags and overrides
insserv: warning: current start runlevel(s) (0 6) of script `umountroot' overwrites defaults (empty).
insserv: There is a loop between service rsyslog and hwclock if stopped
insserv:  loop involving service hwclock at depth 4
insserv:  loop involving service postgresql at depth 3
insserv: There is a loop between service postgresql and rsyslog if stopped
insserv:  loop involving service rsyslog at depth 4
insserv: exiting now without changing boot order!
/sbin/insserv failed, exit code 1
activemq                  0:off  1:off  2:off  3:off  4:off  5:off  6:off

```

What's going on here?

Thanks

Stephen McConnell

---

### Post by Brandon Williams on 2010-05-25
I haven't used chkconfig in a while, not since before ubuntu began the move to upstart. Clearly, there's some weird interaction with this. Is it important to you that this work with chkconfig? If not, then I suggest that you either generate the symlinks by hand or use update-rc.d to generate the symlinks. I know that these two methods work, and it would allow you to get your service working without having to figure out what's going wrong with chkconfig.

If getting chkconfig to work is important to you, hopefully someone else more familiar with it will respond, too.

---

### Post by dino99 on 2010-05-25
[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

---

