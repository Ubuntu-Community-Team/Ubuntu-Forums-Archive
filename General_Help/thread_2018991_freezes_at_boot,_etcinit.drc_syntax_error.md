---
title: "freezes at boot, etc/init.d/rc syntax error"
date: 2012-07-06
forum: General Help
---

### Post by jaredanderson on 2012-07-06
during the boot process I receive this error message ```
/etc/init.d/rc: 338: /etc/init.d/rc: syntax error: end of file unexpected (expecting "fi")
error: '/etc/init.d/rc' exited outside the expected code flow 
``` any help?

---

### Post by Toz on 2012-07-06
Can you post the contents of /etc/init.d/rc? From a command prompt, try:
```
pastebinit /etc/init.d/rc
```
...and post back the link it returns.

---

### Post by jaredanderson on 2012-07-06
it says paste binit is currently not installed I assume I should install it.

---

### Post by jaredanderson on 2012-07-06
well I tried to install it and it returned this message ```
W: not using locking for read only lock file /var/lib/dpkg/lock
E: unable to write to /var/cache/apt/
E: the package lists or status file could not be parsed or opened
```

---

### Post by Toz on 2012-07-06
Looks like you've got more than one problem. 

1. /etc/init.d/rc -> open it in gedit:
```
gedit /etc/init.d/rc
```
...copy the contents and paste them back here. Please use paste the contents between code tags (See: [http://ubuntuforums.org/misc.php?do=bbcode]("http://ubuntuforums.org/misc.php?do=bbcode")).

2. For the installation issue, try:
```
sudo apt-get install pastebinit
```
If it still doesn't work, try:
```
sudo apt-get update
```
...and post back any error messages you may get.

---

### Post by jaredanderson on 2012-07-06
```
#! /bin/sh
#
# rc
#
# Starts/stops services on runlevel changes.
#
# Optimization: A start script is not run when the service was already
# configured to run in the previous runlevel.  A stop script is not run
# when the the service was already configured not to run in the previous
# runlevel.
#
# Authors:
#     Miquel van Smoorenburg <miquels@cistron.nl>
#     Bruce Perens <Bruce@Pixar.com>

PATH=/sbin:/usr/sbin:/bin:/usr/bin
export PATH

# Un-comment the following for interactive debugging. Do not un-comment
# this for debugging a real boot process as no scripts will be executed.
# debug=echo

# Specify method used to enable concurrent init.d scripts.
# Valid options are 'none' and 'makefile'.  Obsolete options
# used earlier are 'shell' and 'startpar'.  The obsolete options
# are aliases for 'makefile' since 2010-05-14.  The default since
# the same date is 'makefile', as the init.d scripts in Debian now
# include dependency information and are ordered using this
# information.  See insserv for information on dependency based
# boot sequencing.
CONCURRENCY=makefile

# Make sure the name survive changing the argument list
scriptname="$0"

umask 022

on_exit() {
    echo "error: '$scriptname' exited outside the expected code flow."
}
trap on_exit EXIT # Enable emergency handler

# Ignore CTRL-C only in this shell, so we can interrupt subprocesses.
trap ":" INT QUIT TSTP

# Set onlcr to avoid staircase effect.
stty onlcr 0>&1

# Functions for splash progress bars
if [ -e /lib/init/splash-functions-base ] ; then
    . /lib/init/splash-functions-base
else
    # Quiet down script if old initscripts version without /lib/init/splash-functions-base is used.
    splash_progress() { return 1; }
    splash_stop() { return 1; }
fi

# Now find out what the current and what the previous runlevel are.

runlevel=$RUNLEVEL
# Get first argument. Set new runlevel to this argument.
[ "$1" != "" ] && runlevel=$1
if [ "$runlevel" = "" ]
then
    echo "Usage: $scriptname <runlevel>" >&2
    exit 1
fi
previous=$PREVLEVEL
[ "$previous" = "" ] && previous=N

export runlevel previous

if [ -f /etc/default/rcS ] ; then
    . /etc/default/rcS
fi
export VERBOSE

if [ -f /lib/lsb/init-functions ] ; then
    . /lib/lsb/init-functions
else
    log_action_msg() { echo $@; }
    log_failure_msg() { echo $@; }
    log_warning_msg() { echo $@; }
fi

#
# Stub to do progress bar ticks (for splash programs) on startup
#
startup_progress() {
    # Avoid divide by zero if anyone moved xdm/kdm/gdm first in a runlevel.
    if [ 0 -eq "$num_steps" ] ; then return; fi

    step=$(($step + $step_change))
    progress=$(($step * $progress_size / $num_steps + $first_step))
    $debug splash_progress "$progress" || true
}

#
# Check if we are able to use make like booting.  It require the
# insserv package to be enabled. Boot concurrency also requires
# startpar to be installed.
#
if [ "none" != "$CONCURRENCY" ] ; then
    test -s /etc/init.d/.depend.boot  || CONCURRENCY="none"
    test -s /etc/init.d/.depend.start || CONCURRENCY="none"
    test -s /etc/init.d/.depend.stop  || CONCURRENCY="none"
    if test -e /etc/init.d/.legacy-bootordering ; then
        CONCURRENCY="none"
    fi
    startpar -v      > /dev/null 2>&1 || CONCURRENCY="none"

#
# Start script or program.
#
case "$CONCURRENCY" in
    makefile|startpar|shell) # startpar and shell are obsolete
        CONCURRENCY=makefile
        log_action_msg "Using makefile-style concurrent boot in runlevel $runlevel"
        # The splash API is not handled with this CONCURRENCY mode.
        # It need to be implented in startpar.  Until that is done
        # stop the splash screen before starting services, to avoid
        # usplash and X to confuse each other during boot.
        startup() {
            if [ start = "$1" ] || [ boot = "$1" ]
            then
                $debug splash_stop || true
            fi
            eval "$(startpar -p 4 -t 20 -T 3 -M $1 -P $previous -R $runlevel)"

            if [ -n "$failed_service" ]
            then
                log_failure_msg "startpar: service(s) returned failure: $failed_service"
            fi

            if [ -n "$skipped_service" ]
            then
                log_warning_msg "startpar: service(s) skipped: $skipped_service"
            fi

            unset failed_service skipped_service
        }
        ;;
    none|*)
        startup() {
            action=$1
            shift
            scripts="$@"
            for script in $scripts ; do
                $debug "$script" $action
                startup_progress
            done
        }
        ;;
esac

# Check if the splash screen should be stopped before the given
# script.
is_splash_stop_scripts() {
    scriptname=$1
    case "$scriptname" in
        # killprocs is used in runlevel 1
        gdm|xdm|kdm|ltsp-client|ltsp-client-core|reboot|halt|killprocs)
            return 0
            ;;
    esac
    return 1
}

# Is there an rc directory for this new runlevel?
if [ -d /etc/rc$runlevel.d ]
then
    # Find out where in the progress bar the initramfs got to.
    PROGRESS_STATE=0
    if [ -f /dev/.initramfs/progress_state ]; then
        . /dev/.initramfs/progress_state
    fi

    # Split the remaining portion of the progress bar into thirds
    progress_size=$(((100 - $PROGRESS_STATE) / 3))

    case "$runlevel" in
        0|6)
            ACTION=stop
            # Count down from 0 to -100 and use the entire bar
            first_step=0
            progress_size=100
            step_change=-1
            ;;
        S)
            ACTION=start
            # Begin where the initramfs left off and use 2/3
            # of the remaining space
            first_step=$PROGRESS_STATE
            progress_size=$(($progress_size * 2))
            step_change=1
            ;;
        *)
            ACTION=start
            # Begin where rcS left off and use the final 1/3 of
            # the space (by leaving progress_size unchanged)
            first_step=$(($progress_size * 2 + $PROGRESS_STATE))
            step_change=1
            ;;
    esac

    # Count the number of scripts we need to run
    # (for progress bars)
    num_steps=0
    for s in /etc/rc$runlevel.d/[SK]*; do
        if is_splash_stop_scripts "${s##/etc/rc$runlevel.d/S??}" ; then
            break
        fi
        num_steps=$(($num_steps + 1))
    done
    step=0

    # First, run the KILL scripts.
    if [ makefile = "$CONCURRENCY" ]
    then
        if [ "$ACTION" = "start" ] && [ "$previous" != N ]
        then
            startup stop
        fi
    elif [ "$previous" != N ]
    then
        # Run all scripts with the same level in parallel
        CURLEVEL=""
        for s in /etc/rc$runlevel.d/K*
        do
            # Extract order value from symlink
            level=${s#/etc/rc$runlevel.d/K}
            level=${level%%[a-zA-Z]*}
            if [ "$level" = "$CURLEVEL" ]
            then
                continue
            fi
            CURLEVEL=$level
            SCRIPTS=""
            for i in /etc/rc$runlevel.d/K$level*
            do
                # Check if the script is there.
                [ ! -f $i ] && continue

                #
                # Find stop script in previous runlevel but
                # no start script there.
                #
                suffix=${i#/etc/rc$runlevel.d/K[0-9][0-9]}
                previous_stop=/etc/rc$previous.d/K[0-9][0-9]$suffix
                previous_start=/etc/rc$previous.d/S[0-9][0-9]$suffix
                #
                # If there is a stop script in the previous level
                # and _no_ start script there, we don't
                # have to re-stop the service.
                #
                [ -f $previous_stop ] && [ ! -f $previous_start ] && continue

                # Stop the service.
                SCRIPTS="$SCRIPTS $i"
                if is_splash_stop_scripts "$suffix" ; then
                    $debug splash_stop || true
                fi
            done
            startup stop $SCRIPTS
        done
    fi

    if [ makefile = "$CONCURRENCY" ]
    then
        if [ S = "$runlevel" ]
        then
            startup boot
        else
            startup $ACTION
        fi
    else
        # Now run the START scripts for this runlevel.
        # Run all scripts with the same level in parallel
        CURLEVEL=""
        for s in /etc/rc$runlevel.d/S*
        do
            # Extract order value from symlink
            level=${s#/etc/rc$runlevel.d/S}
            level=${level%%[a-zA-Z]*}
            if [ "$level" = "$CURLEVEL" ]
            then
                continue
            fi
            CURLEVEL=$level
            SCRIPTS=""
            for i in /etc/rc$runlevel.d/S$level*
            do
                [ ! -f $i ] && continue

                suffix=${i#/etc/rc$runlevel.d/S[0-9][0-9]}
                if [ "$previous" != N ]
                then
                    #
                    # Find start script in previous runlevel and
                    # stop script in this runlevel.
                    #
                    stop=/etc/rc$runlevel.d/K[0-9][0-9]$suffix
                    previous_start=/etc/rc$previous.d/S[0-9][0-9]$suffix
                    #
                    # If there is a start script in the previous level
                    # and _no_ stop script in this level, we don't
                    # have to re-start the service.
                    #
                    if [ start = "$ACTION" ] ; then
                        [ -f $previous_start ] && [ ! -f $stop ] && continue
                    else
                        # Workaround for the special
                        # handling of runlevels 0 and 6.
                        previous_stop=/etc/rc$previous.d/K[0-9][0-9]$suffix
                        #
                        # If there is a stop script in the previous level
                        # and _no_ start script there, we don't
                        # have to re-stop the service.
                        #
                        [ -f $previous_stop ] && [ ! -f $previous_start ] && continue
                    fi

                fi
                SCRIPTS="$SCRIPTS $i"
                if is_splash_stop_scripts "$suffix" ; then
                    $debug splash_stop || true
                fi
            done
            startup $ACTION $SCRIPTS
        done
    fi
fi

trap - EXIT # Disable emergency handler

exit 0


```

---

### Post by jaredanderson on 2012-07-06
I can't gedit the file because I can not boot I am running command promtps through recovery mode. I was able to view the file through windows, ?I am dual booting, but it didn't show the formatting of the file such as color if that is what you were hoping for. the error I posted with W: was what I got from apt-get install as for apt-get update I had many  errors I will post in a second

---

### Post by jaredanderson on 2012-07-06
```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/precise/Release.gpg could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://mirror.lstn.net/ubuntu/dists/precise/Release.gpg could not resolve 'mirror.lstn.net'

W: Failed to fetch http://mirror.lstn.net/ubuntu/dists/precise-updates/Release.gpg could not resolve 'mirror.lstn.net'

W: Failed to fetch http://mirror.lstn.net/ubuntu/dists/precise-backports/Release.gpg could not resolve 'mirror.lstn.net'

W: Failed to fetch http://mirror.lstn.net/ubuntu/dists/precise-security/Release.gpg could not resolve 'mirror.lstn.net'

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg could not resolve 'extras.ubuntu.com'

W: Some index files failed to download. they have been ignored, or old ones used instead

W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened
```

---

### Post by afoin on 2012-07-07
The "fi" that is missing should be at the beginning of the line after
startpar -v      > /dev/null 2>&1 || CONCURRENCY="none"
If you edit /etc/init.d/rc and put it back there, it should boot

---

### Post by jaredanderson on 2012-07-07
I decided to run a live desktop from a jump drive I copied the rc file from the live desktop onto my installation and that fixed both problems I was having. Thanks a ton for your help though very much appreciated.

---

