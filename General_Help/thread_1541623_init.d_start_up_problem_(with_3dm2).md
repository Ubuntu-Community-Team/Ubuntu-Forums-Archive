---
title: "init.d start up problem (with 3dm2)"
date: 2010-07-29
forum: General Help
---

### Post by rchille on 2010-07-29
Hello all!

I recently installed the lasted build of 3dm2 (which is a monitoring app for my 3ware Raid card).

I used the version off 3ware's site and the installation went smoothly, afterwards I fired up the app and everything works. :)

Now the problem: 3dm2 is suppose to start at boot via the init.d scripts. Granted, there are warnings that it was developed for the Red Hat/Fedora/CentOS crowd and I think there are differences between that and the Debian / Ubuntu side...

Anyway, this is what I'm seeing:

3dm2 is not started at after boot:
```

rob@Teletraan:~$ ps -ef | grep 3dm2
rob       1741  1647  0 11:19 pts/0    00:00:00 grep --color=auto 3dm2

```

I can check the status and get this:
```

rob@Teletraan:~$ sudo /etc/init.d/tdm2 status
Check 3ware Daemon Status...  * Check 3ware Daemon Status...                    status: Unknown job: 3dm2
1
                                                                         [fail]

```

Manually starting with script seems to be fine:
```

rob@Teletraan:~$ sudo /etc/init.d/tdm2 start
Starting 3ware Daemon...  * Starting 3ware Daemon...                                   0
                                                                          [ OK ]

```

And I can confirm that it is running after the manual start:
```

rob@Teletraan:~$ ps -ef | grep 3dm2
root      1717     1  0 11:18 pts/0    00:00:00 /usr/sbin/3dm2
root      1720  1717  0 11:18 pts/0    00:00:00 /usr/sbin/3dm2
root      1721  1720  0 11:18 pts/0    00:00:00 /usr/sbin/3dm2
rob       1727  1647  0 11:19 pts/0    00:00:00 grep --color=auto 3dm2

```

I can also stop/restart it without troubles.

The actual script (/etc/init.d/tdm2) Looks like this:
```

#!/bin/sh 
#
# tdm2:     	Starts the 3ware daemon
#
# Author:       Michael Benz <linuxraid@lsi.com>
#
### BEGIN INIT INFO
# Required-Start:    $local_fs $syslog $network
# Required-Stop:     $local_fs $syslog $network
# Default-Start:     3 4 5
# Default-Stop:      S 0 1 6
# Provides:          3dm2
# Short-Description: Start and Stop 3ware Daemon
# Description:       Start the 3dm2 application which logs the current state
#                    of the 3ware RAID controller, then polls for state changes.
### END INIT INFO

# config: /etc/3dm2/3dm2.conf

# Source function library.
. /lib/lsb/init-functions

PROCNAME=3dm2
DAEMON=/usr/sbin/3dm2
LOCKFILE=/var/lock/3dm2
RETVAL=0

export PATH="${PATH:+$PATH:}/bin:/usr/bin:/usr/local/bin:/sbin:/usr/sbin:/usr/local/sbin"

test -x $DAEMON || exit 0

# See how we were called.
case "$1" in
  start)
        if [ ! -f $LOCKFILE ]; then
		echo -n "Starting 3ware Daemon... "
		log_daemon_msg "Starting 3ware Daemon... "
		start-stop-daemon -S -q -x $DAEMON || RETVAL=1
		#start-stop-daemon --start --quiet --exec $DAEMON && touch $LOCKFILE || RETVAL=1
		[ $RETVAL -eq 0 ] && touch $LOCKFILE || RETVAL = 1
		echo $RETVAL
		log_end_msg $RETVAL
        else
                echo "3dm2 must already be running. Found lock file $LOCKFILE"
	fi
	;;
  stop)
	echo -n "Stopping 3ware Daemon... "
	log_daemon_msg "Stopping 3ware Daemon... "
	start-stop-daemon --stop -s TERM -q -n $PROCNAME || RETVAL=1
	#start-stop-daemon --stop --quiet --name $PROCNAME && rm -f $LOCKFILE || RETVAL=1
	[ $RETVAL -eq 0 ] && rm -f $LOCKFILE || RETVAL = 1
	echo $RETVAL
	log_end_msg $RETVAL
	;;
  restart|force-reload)
	$0 stop
        sleep 1
	$0 start
	;;
  status)
	echo -n "Check 3ware Daemon Status... "
	log_begin_msg "Check 3ware Daemon Status... "
	status 3dm2 || RETVAL=1
	echo $RETVAL
	log_end_msg $RETVAL
	;;
  *)
	echo "Usage: $0 {start|stop|restart|force-reload|status}"
	log_success_msg "Usage: $0 {start|stop|restart|force-reload|status}" >&2
	exit 1
	;;
esac

exit $RETVA

```



I dug through /var/log grep'ing for anything that is tdm2, 3dm2 or "3ware" and do not see anything that looks anything more that start/stop messages/.

I did play with the update-rc.d commands a bit to get rid of another error message, so this is the current files:

```

/etc/rc5.d/S95tdm2
/etc/rc1.d/K05tdm2
/etc/rcS.d/K05tdm2
/etc/rc6.d/K05tdm2
/etc/rc0.d/K05tdm2
/etc/init.d/tdm2
/etc/rc2.d/S95tdm2
/etc/rc4.d/S95tdm2

```

Inside each of the startup /etc/rc[245].d looks like:
```

lrwxrwxrwx 1 root root  14 2010-07-27 19:16 S19lirc -> ../init.d/lirc
lrwxrwxrwx 1 root root  27 2010-07-27 19:24 S20nfs-kernel-server -> ../init.d/nfs-kernel-server
lrwxrwxrwx 1 root root  17 2010-07-28 22:21 S20postfix -> ../init.d/postfix
lrwxrwxrwx 1 root root  15 2010-07-27 19:16 S21aumix -> ../init.d/aumix
lrwxrwxrwx 1 root root  13 2010-07-27 19:16 S23ntp -> ../init.d/ntp
lrwxrwxrwx 1 root root  19 2010-07-27 19:16 S25bluetooth -> ../init.d/bluetooth
lrwxrwxrwx 1 root root  15 2010-07-27 19:16 S50rsync -> ../init.d/rsync
lrwxrwxrwx 1 root root  19 2010-07-27 19:16 S70dns-clean -> ../init.d/dns-clean
lrwxrwxrwx 1 root root  18 2010-07-27 19:16 S70pppd-dns -> ../init.d/pppd-dns
lrwxrwxrwx 1 root root  17 2010-07-27 19:16 S91apache2 -> ../init.d/apache2
lrwxrwxrwx 1 root root  22 2010-07-27 19:16 S99acpi-support -> ../init.d/acpi-support
lrwxrwxrwx 1 root root  21 2010-07-27 19:16 S99grub-common -> ../init.d/grub-common
lrwxrwxrwx 1 root root  18 2010-07-27 19:16 S99ondemand -> ../init.d/ondemand
lrwxrwxrwx 1 root root  18 2010-07-27 19:16 S99rc.local -> ../init.d/rc.local

```

I'm a little lost as what to do next. The app seems to work, it just doesn't start-up at boot. I feel it might be something getting lost with the init.d scripts but my morning romp through Google hasn't yielded anything that works. 

Any suggestion?

Thanks!

---

### Post by ajgreeny on 2010-07-29
Add your manual command to start it, minus the sudo, to the /etc/rc.local file just above the **exit 0** line, and it may do the job.
```
/etc/init.d/tdm2 start
exit 0
```
However it seems weird that the init'd script you tried does not work when the manual command does.

Don't forget that some things that used to be started by init.d are now using upstart, and I don't know the best way to deal with those.  However, you could also try ```
sudo service tdm2 start
``` to see if that works and if so use that command minus the sudo again in rc/local, thus avoiding the init.d script completely.

---

### Post by sisco311 on 2010-07-29
@ajgreeny

The problem with rc.local is that Upstart often runs it too soon.

@OP, I would try to edit the original System-V style init script.

Back it up:
```
sudo cp /etc/init.d/tdm2{,-backup}
```
And edit it to something like:
```

case "$1" in
  start)
        if [ ! -f $LOCKFILE ]; then
		echo -n "Starting 3ware Daemon... "
		log_daemon_msg "Starting 3ware Daemon... "
                [B]
                #the number of times we try to start the daemon 
                TRY=3
                #wait $WAIT second(s) between each try
                WAIT=2
                i=0
                while [ $i -lt $WAIT ]; do
                    start-stop-daemon -S -q -t -x $DAEMON && break
                    sleep $WAIT
                    i=`expr $i + 1`
                done[/B]  
		start-stop-daemon -S -q -x $DAEMON || RETVAL=1
		#start-stop-daemon --start --quiet --exec $DAEMON && touch $LOCKFILE || RETVAL=1
		[ $RETVAL -eq 0 ] && touch $LOCKFILE || RETVAL = 1
		echo $RETVAL
		log_end_msg $RETVAL
        else
                echo "3dm2 must already be running. Found lock file $LOCKFILE"
	fi
	;;

```

If it doesn't work restore the original:
```
sudo cp /etc/init.d/tdm2{-backup,}
```

---

### Post by rchille on 2010-07-29
Thank you both for the replies!

Unfortunately, adding either line to the /etc/rc.local seemed to have no effect. 

Adding the while loop into the init.d script seems to help some of the time. About 3 in 20 time the service has come up on boot. I expanded the params to try 6 times, one every 10 secs and still nothing. 

The fact that it seemed to work a few times gives me hope that it will work!

Is there anyway to log the results of these tries?

Thanks!

---

### Post by SaintDanBert on 2010-07-29
> **ajgreeny said:**
> 
...
Don't forget that some things that used to be started by init.d are now using upstart, ...


The "upstart" approach to system start-up includes its own edition of the **init** utility.  The folders **/etc/init.d** and **/etc/rc[2345].d** exist for compatibility with the System-V approach to system start-up. The old way use scripts that ran in a sequence defined by the script authors.  The upstart-way also uses scripts, but is determined by the chain-of-events that happen, not only during startup but at all other times during a running system.

EDIT:  Both System-V and Upstart use files in **/etc/init.d** -- they are just used differently with different file contents.

~~~ 0;-Dan

---

### Post by sisco311 on 2010-07-29
Hmmm, lets try to convert the System-V style init script to an Upstart job.

Save the following as /etc/init/3dm2.conf:
```

# 3dm2
#
# Start the 3dm2 application which logs the current state
# of the 3ware RAID controller, then polls for state changes.

description "Start and Stop 3ware Daemon"

start on (started rsyslog
          and started networking) 

stop on runlevel [06]

expect fork
respawn

exec /usr/sbin/3dm2

```

And disable the System-V style init scrip:
```
sudo chmod -x /etc/init.d/tdm2
```
Reboot ans see if it works.


To re-enable the old init script, run:
```
sudo chmod +x /etc/init.d/tdm2
```

---

### Post by rchille on 2010-07-29
sisco311,

Thanks for the tip! That [switching to the Upstart method] seemed to work, I've gone through 5 reboots now and 3dm2 has come up properly each and every time!

Marking this one solved!
Thanks everyone for the help!

---

