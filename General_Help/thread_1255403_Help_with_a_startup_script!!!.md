---
title: "Help with a startup script!!!"
date: 2009-09-01
forum: General Help
---

### Post by mihalisla on 2009-09-01
Hello to all of you!
I run ubuntu 9.04
I installed samhain from source and want to tweak it's init script a bit or to create another (preferably) that does this:
make a folder /var/run/samhain (so as samhain can find it at startup and create the samhain.pid file)
Also does anybody know if I should create the .pid file or pids files are created by daemon processes ?

One friend suggested that I should have in the script this:
'test -d /var/run/samhain || mkdir /var/run/samhain'
Thanks in advance!

---

### Post by DaithiF on 2009-09-01
> I installed samhain from source and want to tweak it's init script a bit or to create another (preferably) that does this:
make a folder /var/run/samhain (so as samhain can find it at startup and create the samhain.pid file)
Also does anybody know if I should create the .pid file or pids files are created by daemon processes ?

Normally an init script defines the location of the pidfile and passes that location to the start / stop helpers which take care of the creation / deletion of them.  So no, your daemon process itself doesn't need to manage those.

Why don't you start with the existing samhain init script and, er, tweak it to do what you want?  Have you had a look at what it is doing to see where you would need to make changes? 

ps. I don't know what samhain is other than its the Irish name for November, and a celtic festival :)

---

### Post by mihalisla on 2009-09-01
The init script is way too complicated for me.
So I want to make these files with another new script.
Do u know how to add it to startup scripts,besides from putting it to /etc/init.d/ ?

PS.Samhain is one of the best ids out there with the most advanced stealth capabilities checkout :
[http://la-samhna.de/samhain/](http://la-samhna.de/samhain/)

---

### Post by mihalisla on 2009-09-01
So what i want to do is :
1.Check in the script if /var/run/samhain exists
2.have the  script to create the folder /var/run/samhain
3.Start on boot

Anyone?

---

### Post by DaithiF on 2009-09-01
```
1.Check in the script if /var/run/samhain exists
2.have the  script to create the folder /var/run/samhain
3.Start on boot

```
this is why the init script exists -- to do exactly these kinds of things.  I would still advise starting with that, its only as complicated as it needs to be.  And the end result will be better than creating your own from scratch.  If you need help understanding the script, then feel free to post it here.

---

### Post by mihalisla on 2009-09-01
> #! /bin/sh

### BEGIN INIT INFO
# Provides: samhain
# Required-Start: $syslog $network
# Required-Stop: $syslog $network
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Keep an eye on stuff
# Description: Keep an eye on stuff
### END INIT INFO


# source function library
if test -f /lib/lsb/init-functions; then
. /lib/lsb/init-functions
else
	echo "File /lib/lsb/init-functions not found"
	exit 5
fi

prefix=""
exec_prefix="${prefix}"
DAEMON=/usr/local/sbin/samhain
NAME=samhain

if test ! -f ${DAEMON}; then
	log_failure_msg "Service $NAME is not installed"
  	exit 5
fi

if test "x$2" != "x" && test "x$1" != "xstatus"; then
	log_failure_msg "Excess arguments $@"
	exit 2
fi

log_sh_msg () {
case "$1" in
	0)
	log_success_msg "Service $NAME $2"
	break;
	;;
	1)
	log_failure_msg "Service $NAME: Error"
	break;
	;;
	4)
	log_failure_msg "Service $NAME: Permission denied"
	break;
	;;
	5)
	log_failure_msg "Service $NAME is not installed"
	break;
	;;
	7)
	log_failure_msg "Service $NAME is not running"
	break;
	;;
	*)
	log_failure_msg "Service $NAME: Error"
	break;
	;;
esac
}

log_stat_msg () {
case "$1" in
	0)
	echo "Service $NAME: Running";
	break;
	;;
	1)
	echo "Service $NAME: Stopped and /var/run pid file exists";
	break;
	;;
	3)
	echo "Service $NAME: Stopped";
	break;
	;;
	*)
	echo "Service $NAME: Status unknown";
	break;
	;;
esac
}

case "$1" in
  start)
	${DAEMON} start
	ERRNUM=$?
	SH_ACT="started"
	;;
  stop)
	${DAEMON} stop
	ERRNUM=$?
	if test -f /var/run/samhain/samhain.pid; then
	    /bin/rm -f /var/run/samhain/samhain.pid
	fi
	if test -S /var/run/samhain/${NAME}.sock; then
	    /bin/rm -f /var/run/samhain/${NAME}.sock
        fi
	SH_ACT="stopped"
	;;
  restart)
	${DAEMON} restart
	ERRNUM=$?
	SH_ACT="restarted"
	;;
  reload|force-reload)
	${DAEMON} reload
	ERRNUM=$?
	SH_ACT="reloaded"
	;;
  status)
	${DAEMON} status
	ERRNUM=$?
	log_stat_msg ${ERRNUM}
	exit ${ERRNUM}
	;;
  *)
        log_warning_msg "Usage: samhain {start|stop|restart|(force-)reload|status}"
	exit 2
	;;
esac

log_sh_msg ${ERRNUM} "${SH_ACT}"
exit ${ERRNUM}
 
Now where should I add the check ,if the file exists?
How can I make the script add /var/run/samhain
automatically on boot time?

Thanks a lot!

---

### Post by DaithiF on 2009-09-01
when installing, did you do the 
```
sudo make install-boot

```step?  That would install the init script, setting it up to run on system boot.  The init script will already put a pid file in /var/run/samhain, so I don't think you would have anything to change, you just need to make sure the init script is installed.

---

### Post by mihalisla on 2009-09-01
Well I've installed all these ,but the problem is that /var/run
is mounted under tmpfs in ubuntu so it removes /var/run/samhain
in every restart.
Thats the reason I want to add to the script the making of 
/var/run/samhain

---

### Post by jward3010 on 2009-09-01
These little programs are obviously developed by patriotic Irish developers. Like mentioned above Samhain is the Irish for November and Bealtaine (similar to Beltane) is the Irish for the month of May, trying to find a connection on their site is not easy.

---

### Post by DaithiF on 2009-09-01
ok, add a section towards the top somewhere with:
```
if test ! -d /var/run/samhain; then
   mkdir /var/run/samhain
fi

```

---

### Post by mihalisla on 2009-09-01
And what about the attributes.
samhain folder needs to be set to 755

---

### Post by DaithiF on 2009-09-01
root's umask is 022 so those are the permissions that will get applied by default.

but also, what version of samhain are you running?  i just downloaded & installed (from source) samhain-2.5.8a, the init script is different to the one you posted (it puts the pid file in /var/run/ directly, so you wouldn't have the issue with the missing directory.  It all worked just fine, the init script is set up, it runs on boot, etc.  So maybe try the current version, it may avoid some issues for you.

---

### Post by mihalisla on 2009-09-01
I had it configured it manually (from source)to install it in /var/run/samhain.
I copied the location from the location I got when I installed it through apt-get.
Though it lacked so many features like gpg sighning,altering the name of excecutable and stealth among with hiding the to a postscript image .
It has many difficulties configuring it from source.
Sometime I will publish an installation guide for HIDS only.
I have no server to see specific problems I encountered.

Thanks a lot!!!


ps.If you want sometime to have it configured from source for your desktop PM me(if u need a special feature).I think that I got the info needed to set samhain for desktop use.
Also Khide module (--enable-khide)does not work with ubuntu.

---

