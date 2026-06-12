---
title: "apcupsd multiple UPS monitoring startup script"
date: 2009-07-17
forum: General Help
---

### Post by Xi0N on 2009-07-17
Im trying to monitor 3 UPS from the same Debian machine, all them connected by USB...
The point is that i am following [this howto]("http://www.apcupsd.com/manual/manual.html#controlling-multiple-upses-on-one-machine"), and im in the part where you have to modify your /etc/init.d/apcupsd file to make it handle multiple configuration files. The problem is that the example in the page is for a red-hat distro, and i dont have enough knowledgements to "translate" it for making it work with my ubuntu...... did anyone implement this on a debian-based machine? Anyone so kind to share the startup script with me? maybe a brave one to convert it to debian? :P

Thanks!

---

### Post by t4thfavor on 2009-07-17
It looks like it would be about the same, in both cases you have to modify your init.d/apupsd script.

Take a look at it with gedit nd see if you can figure out how to make it iterate through multiple conf files.

If you need some more help, I will consider looking at my installation and seeing if I can figuree it out.

---

### Post by Xi0N on 2009-07-18
I think i did it:

```
#!/bin/sh

### BEGIN INIT INFO
# Provides:		apcupsd
# Required-Start:	$syslog
# Required-Stop:	$syslog
# Should-Start:		$local_fs
# Should-Stop:		$local_fs
# Default-Start:	2 3 4 5
# Default-Stop:		0 1 6
# Short-Description:	Starts apcupsd daemon
# Description:		apcupsd provides UPS power management for APC products.
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/sbin/apcupsd
CONFIG=/etc/default/apcupsd
NAME=apcupsd
DESC="UPS power management"

test -x $DAEMON || exit 0
test -e $CONFIG || exit 0

set -e

. $CONFIG

if [ $ISCONFIGURED = no ]
then
	echo "Please check your configuration ISCONFIGURED in /etc/default/apcupsd"
	exit 0
fi


case "$1" in
    start)
       rm -f /etc/apcupsd/powerfail
       rm -f /etc/nologin
       for conf in /etc/apcupsd/apcupsd.*.conf ; do
          inst=`basename $conf`
          echo -n "Starting UPS monitoring ($inst):"
          /sbin/apcupsd -f $conf -P /var/run/apcupsd-$inst.pid
          RETVAL=$?
          echo
          [ $RETVAL -eq 0 ] && touch /var/lock/subsys/apcupsd-$inst
       done
       ;;
    stop)
       for conf in /etc/apcupsd/apcupsd.*.conf ; do
          inst=`basename $conf`
          echo -n "Shutting down UPS monitoring ($inst):"
          killall apcupsd
          echo
          rm -f /var/run/apcupsd-$inst.pid
          rm -f /var/lock/subsys/apcupsd-$inst
       done
       ;;
	restart|force-reload)
		$0 stop
		sleep 10
		$0 start
		;;

	status)
		#/sbin/apcaccess status
		$APCACCESS status
		;;

	*)
		N=/etc/init.d/$NAME
		echo "Usage: $N {start|stop|restart|force-reload}" >&2
		exit 1
		;;
esac

exit 0

```

At least, it looks like it works....

---

### Post by enortje on 2009-08-04
Hi XiON

I am new to Ubuntu scripting and have only done a little bit of scripting on other distros so forgive me if I sound silly.

My init.d script (which follows after this reply) looks nowhere near as tidy as yours but I tried to do the same sort of stuff they had in the template in the manual. I checked for running processes on startup etc.

It seems to work pretty well starting up multiple instances but I have issues in two areas:

1. When I simulate a power-failure my "master" box also wants to restart because somehow the 99 exit code that I pass to it gets lost. 
How did you handle this? One (ugly) option would be to change the apccontrol scripts for the non-master instances of apcupsd but I'd prefer doing it the "right" way.

2. When I try to use things like APCACCESS to retrieve the status it does not work.

Any advice would be greatly appreciated!

Cheers,
Eugene

```
######  init.d script start   #########

#!/bin/sh

### BEGIN INIT INFO
# Provides:        apcupsd
# Required-Start:    $syslog
# Required-Stop:    $syslog
# Should-Start:        $local_fs
# Should-Stop:        $local_fs
# Default-Start:    2 3 4 5
# Default-Stop:        0 1 6
# Short-Description:    Starts apcupsd daemon
# Description:        apcupsd provides UPS power management for APC products.
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/sbin/apcupsd
CONFIG=/etc/default/apcupsd
NAME=apcupsd
DESC="UPS power management"

test -x $DAEMON || exit 0
test -e $CONFIG || exit 0

set -e

. $CONFIG

if [ $ISCONFIGURED = no ]
then
    echo "Please check your configuration ISCONFIGURED in /etc/default/apcupsd"
    exit 0
fi


case "$1" in
    start)
        rm -f /etc/apcupsd/powerfail

          for conf in /etc/apcupsd/apcupsd.*.conf ; do
              inst=`basename $conf`
              echo -n "Starting UPS monitoring ($inst):"

          if [ "`pidof apcupsd-$inst`" = "" ]
          then
            start-stop-daemon --start --quiet --exec /sbin/apcupsd --pidfile /var/run/apcupsd-$inst.pid -- -f $conf

# note the above is on ONE line in the script #

            echo "$NAME."
          else
            echo ""
            echo "A copy of the daemon is still running.  If you just stopped it,"
            echo "please wait about 5 seconds for it to shut down."
            exit 0
          fi

          done
        ;;

    stop)
             for conf in /etc/apcupsd/apcupsd.*.conf ; do
            inst=`basename $conf`
          echo -n "Shutting down UPS monitoring ($inst):" 
                start-stop-daemon --stop oknodo --pidfile /var/run/apcupsd-$inst.pid || echo "Not Running."
          rm -f /var/run/apcupsd-$inst.pid
        done
        ;;

    restart|force-reload)
        $0 stop
        sleep 15
        $0 start
        ;;

    reload)
          echo "$0: reload not implemented"
          exit 3
        ;;


    status)
        for conf in /etc/apcupsd/apcupsd.*.conf ; do
              inst=`basename $conf`
              status -p /var/run/apcupsd-$inst.pid apcupsd-$inst
              RETVAL=$?
              if [ $RETVAL -eq 0 ]
              then
                  NISPORT=`grep ^NISPORT < $conf | sed -e "s/NISPORT *\([0-9]\)/\1/"`
                  /sbin/apcaccess status localhost:$NISPORT | egrep "(STATUS)|(UPSNAME)" 
              fi
            done
          ;;

    *)
        N=/etc/init.d/$NAME
        echo "Usage: $N {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

######  init.d script end  #########
```

---

### Post by Xi0N on 2009-08-04
I did not realize the thing with the power failure you describe... i didnt have anyone still, and since the machine apcupsd is in is not critical for production, i think is not really a big deal in my situation-
I realized that when you launch the apcaccess command, you only get retrieved the information regarding the first ups that your init script initializes the monitor on....... its a bit crappy, since even the developers seems not to know how to handle this: I have sent them a mail through their mailing list system regarding this particular issue and i did not get any reply.... it makes the mail sending functionaity a bit confusing, since everytime anythong happens on an ups, an output of this command gets attached in the body of the mail... so, maybe ups #3 is failing, but you will get a notification giving you the status of ups #1..... i will try to insist on this with them.....

Good luck!

---

