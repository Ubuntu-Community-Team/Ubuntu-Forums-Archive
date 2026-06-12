---
title: "Tripp-lite PowerAlert RPM - can't convert with Alien"
date: 2011-04-14
forum: General Help
---

### Post by jlbrewer on 2011-04-14
We got a big Tripp-Lite SmartOnline UPS in a while ago.  Turns out the official Linux support for it is only in Fedora and OpenSUSE.  I tried converting the .rpm packages of their management software and ran into the following problems:
```

error: cannot open Packages database in /home/jamie/.rpmdb
```

Tried creating the folder and got:

```
error: cannot open Packages database in /home/jamie/.rpmdb
error: cannot open Packages index using db3 - No such file or directory (2)
```

So no go.  It's 64-bit Ubuntu 10.10 and the RPMs are 32-bit.  (And I have no idea if the PowerAlert tools will run sans GUI on the servers it will be powering anyway.)

Anyone know what's wrong with Alien?  I downloaded it from apt and as far as I can tell all the dependencies are in place.

Anyone have experience getting PowerAlert to run on Ubuntu?  I called their tech support and got the company line, no help there.

I will try nut next, but I'm pesimistic - it had driver issues with the smaller Cyberpower UPSes that the workstations are running on (but Cyberpower at least has working .deb binaries!).

---

### Post by jlbrewer on 2011-04-23
one-week bump.

---

### Post by JPorter on 2011-05-17
I'd love to know this as well...

---

### Post by DavidAGG on 2012-06-27
Here's how I got this working:

Download the Fedora RPM.
Convert it to a gzipped tarball with [FONT=Courier New]alien --to-tgz pal-app-12.04.0053-1.i386-fedora.rpm[/FONT]
Unzip it: [FONT=Courier New]tar -zxvf pal-12.04.0053.tgz[/FONT]
Copy files across: [FONT=Courier New]cp -rpf var/* /va[/FONT]r
[FONT=Courier New]cp etc/init.d/pald /etc/init.d[/FONT]

The pald init file does not work since it is looking for Redhat/Fedora init functions. I modified it thus:

```
#!/bin/bash
prog=pald

start() {
    echo -n $"Starting $prog: "
    start-stop-daemon --start --exec /var/tripplite/poweralert/engine/$prog --pidfile /var/run/${prog}.pid --make-pidfile
    RETVAL=$?
    echo
    [ "$RETVAL" = 0 ]
}

stop() {
    echo -n $"Stopping $prog: "
    start-stop-daemon --stop --name $prog 
    RETVAL=$?
    echo
    [ "$RETVAL" = 0 ] && rm -f /var/run/${prog}.pid
}

restart() {
    stop
    start
}

# See how we are called.
case "$1" in
    start)
        start ;;

    stop)
        stop ;;

    restart)
        restart ;;

    *)
        echo $"Usage: $0 {start|stop|restart}"
        exit 1
esac

exit $RETVAL
```I created a symlink to the init file: [FONT=Courier New]ln -s /etc/init.d/pald /etc/rc5.d/S80pald[/FONT]

The GUI monitoring software is in [FONT=Courier New]/var/tripplite/poweralert/console/pal_console.sh[/FONT]. You will need a relatively recent Java JRE. It seems to be working as expected so far. The only oddity is that the PID stored in [FONT=Courier New]/var/run/pald.pid[/FONT] does not match that returned by [FONT=Courier New]ps[/FONT]. I assume this is because the daemon forks itself into the background twice so it can release its controlling TTY and/or make itself a session group leader (an old daemon trick).

---

### Post by HDave on 2013-03-24
> **DavidAGG said:**
> Here's how I got this working:

Download the Fedora RPM.
Convert it to a gzipped tarball with [FONT=Courier New]alien --to-tgz pal-app-12.04.0053-1.i386-fedora.rpm[/FONT]
Unzip it: [FONT=Courier New]tar -zxvf pal-12.04.0053.tgz[/FONT]
Copy files across: [FONT=Courier New]cp -rpf var/* /va[/FONT]r
[FONT=Courier New]cp etc/init.d/pald /etc/init.d[/FONT]

The pald init file does not work since it is looking for Redhat/Fedora init functions. I modified it thus:

```
#!/bin/bash
prog=pald

start() {
    echo -n $"Starting $prog: "
    start-stop-daemon --start --exec /var/tripplite/poweralert/engine/$prog --pidfile /var/run/${prog}.pid --make-pidfile
    RETVAL=$?
    echo
    [ "$RETVAL" = 0 ]
}

stop() {
    echo -n $"Stopping $prog: "
    start-stop-daemon --stop --name $prog 
    RETVAL=$?
    echo
    [ "$RETVAL" = 0 ] && rm -f /var/run/${prog}.pid
}

restart() {
    stop
    start
}

# See how we are called.
case "$1" in
    start)
        start ;;

    stop)
        stop ;;

    restart)
        restart ;;

    *)
        echo $"Usage: $0 {start|stop|restart}"
        exit 1
esac

exit $RETVAL
```I created a symlink to the init file: [FONT=Courier New]ln -s /etc/init.d/pald /etc/rc5.d/S80pald[/FONT]

The GUI monitoring software is in [FONT=Courier New]/var/tripplite/poweralert/console/pal_console.sh[/FONT]. You will need a relatively recent Java JRE. It seems to be working as expected so far. The only oddity is that the PID stored in [FONT=Courier New]/var/run/pald.pid[/FONT] does not match that returned by [FONT=Courier New]ps[/FONT]. I assume this is because the daemon forks itself into the background twice so it can release its controlling TTY and/or make itself a session group leader (an old daemon trick).

This isn't working for me.  My x64 Ubuntu server 12.04 will not run the pald executable.... presumably because it is a 32bit exec on a 64bit system.  Installing ia32libs seemed way overkill.  Any suggestions?

Edit:  I punted on there stuff and went with nut along with the tripplite_usb driver which is working great.

---

### Post by wildmanne39 on 2013-03-25
Thanks for sharing,please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

