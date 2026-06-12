---
title: "Startup Script"
date: 2010-10-18
forum: General Help
---

### Post by rmccarri on 2010-10-18
Hi everyone,
I'm trying to get the holdingnuts-server poker server running at startup on my server.  I have the following startup script:

```
#!/bin/bash
# chkconfig: 2345 99 02
# description: Holdingnuts Server

### INIT INFO
# Provides: holdingnuts-server
# Required-Start: $network
# Required-Stop: $network
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-description: Holdingnuts server
# Description: Start and stop the Holdingnuts server.
### END INIT INFO

RETVAL=0

start() {
echo -n "Starting Holdingnuts: "
pgrep -f holdingnuts-server
RETVAL=$?
[ $RETVAL -eq 0 ] && echo "Holdingnuts already running: Exiting" && exit 1

# this call actually starts Holdingnuts.
/usr/games/holdingnuts-server > /dev/null 2>&1 &
RETVAL=$?
[ $RETVAL -eq 0 ] && echo -n "done"
echo
return $RETVAL
}

stop() {
echo -n "Stopping Holdingnuts: "
pkill -f holdingnuts-server
RETVAL=$?
echo
[ $RETVAL -eq 0 ] && echo -n "done"
echo
return $RETVAL
}

# See how we were called.
case "$1" in
start)
start
;;
stop)
stop
;;
restart|reload)
stop
sleep 1
start
RETVAL=$?
;;
*)
echo "Usage: $0 {start|stop|restart}"
exit 1
esac
exit $RETVAL

```

I've borrowed this code from my pyTivo server startup script.  I've tested it and it works perfectly once the server is up and running.  I placed this in my /etc/init.d directory and run update-rc with "defaults and 99 02", so it runs with the last batch of scripts like apache.  Does anyone have any ideas why this does not work at boot, but works perfectly if I invoke:

```

/etc/inid.d/holdingnuts-start start
/etc/inid.d/holdingnuts-start restart
/etc/inid.d/holdingnuts-start stop

```

from the terminal once it's up and running?
Thanks!
Rob

---

### Post by efflandt on 2010-10-18
Have you checked dmesg or /var/log/messages to see if anything shows up about it there?

Does it work if you run it from /etc/rc.local (which runs after everything else starts)?

---

### Post by rmccarri on 2010-10-19
Hmmmm.....thanks for the god suggestions!  I removed the startup script from the rcx.d folders and added the following to my rc.local script:

```
/usr/games/holdingnuts-server &
```

I removed the piping to /dev/null and such so that it would write errors to the logs and I don't see anything.  It's definitely running, but I cannot connect to the server.  Again, if I restart it by running the startup script in /etc/init.d, it runs fine.  

I just thought of something while writing this message.  I tried the startup it under su, as opposed to evoking sudo to see if that makes a difference.  Interestingly, if I restart the server by running the following from my user account, it works fine:

```
sudo /etc/init.d/holdingnuts-start restart
```

However, if I run it as root in su mode, it doesn't.  So this helped me figure it out.  When I run it with sudo from my account, it uses the configuration file from my directory, which I had tweaked the port so that my friends can connect from places where the default port would be blocked.  When it runs it at startup, it runs from an auto-generated configuration file in /root/.holdingnuts that has the default port.  I tweaked this file and now it works!

---

### Post by rmccarri on 2010-10-19
Ugh!  I spoke too soon!  I thought that would fix it, but it didn't.  I still couldn't connect when I restarted.  Does anyone have any ideas?

---

### Post by rmccarri on 2010-10-19
So I added a "sleep 30" to the rc.local file to see if that helped.  When the server was restarted, I sshed in and ran a "ps ax | grep holdingnuts-server" until it was running and indeed, it wasn't running at startup, but started 30 seconds later.  Even then, I wasn't able to connect properly.  So it isn't a problem with other services that it needs not being ready.  It seems to be a problem with the system starting the server as opposed to me running the startup script.  What would be different between the system starting it from the rc.local file and me starting it from the terminal?

---

### Post by rmccarri on 2010-10-19
One more update:

So I decided to try running it as a cron job.  I set cron to run:

```
/etc/init.d/holdingnuts-start start
```

every 2 minutes.  This works in the meantime.  This has the added bonus that if the server crashes, it will restart within 2 minutes.  It still bugs me that I can't get this to work with the startup scripts, though and would appreciate any suggestions.

---

### Post by rmccarri on 2010-10-22
Just in case anyone comes upon this, I started a thread when I came across another startup issue with OpenVPN and got to the root of the issue.  The problem is that I have a bridged interface (br0) and even though the device is brought up early in the boot process, it takes a while to grab the static IP.  Some very helpful individuals guided me to getting an upstart script to work which required my br0 interface to be up to start the poker server.

[http://ubuntuforums.org/showthread.php?t=1603108](http://ubuntuforums.org/showthread.php?t=1603108)

---

