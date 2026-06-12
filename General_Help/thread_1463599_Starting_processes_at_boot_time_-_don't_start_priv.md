---
title: "Starting processes at boot time - don't start privoxy"
date: 2010-04-27
forum: General Help
---

### Post by marllowe on 2010-04-27
Hi,

I installed and configured privoxy - everything worked nicely when I run it  manually by 
> /etc/init.d/privoxy startAfter restarting the computer privoxy wasn't start automatically.
I checked the links in /etc/rcX.d - are o.k.
I installed sysv-rc-conf - shows that for runlevel 2 - 5 privoxy is running.
I changed /etc/rc2.d/S20privoxy to /etc/rc2.d/S99privoxy - to start that process at the end.
I installed Boot-Up Manager. Privoxy is marked for start automatically
I added in /etc/rc.local line: /etc/init.d/privoxy start

Privoxy still doesn't turn on at boot time and every time I must start it manually ...
Could you tell me how could I repair this ?

Regards,
Artur

---

### Post by Brandon Williams on 2010-04-27
Open /etc/default/privoxy (create it if it doesn't exist) and add the following code at the end:
```
exec 2> /tmp/privoxy_startup.log
set -x
```

Next, reboot. After the reboot is complete, does the file /tmp/privoxy_startup.log exist? And if it exists, does it contain any useful error messages? If you're not sure, then post the content of the file here.

---

### Post by marllowe on 2010-04-28
I created /etc/default/privoxy. 
After reboot inside /tmp/privoxy_startup.log is this code:
> + [ ! -d /var/log/privoxy ]
+ . /lib/init/vars.sh
+ [ -f /etc/default/rcS ]
+ . /etc/default/rcS
+ TMPTIME=0
+ SULOGIN=no
+ DELAYLOGIN=no
+ UTC=no
+ VERBOSE=no
+ FSCKFIX=no
+ [ -r /proc/cmdline ]
+ grep -qw noswap /proc/cmdline
+ NOSWAP=no
+ [ ! -e /proc/cmdline ]
+ egrep -qw quiet /proc/cmdline
+ VERBOSE=no
+ [  ]
+ true
+ . /lib/lsb/init-functions
+ FANCYTTY=
+ [ -e /etc/lsb-base-logging.sh ]
+ . /etc/lsb-base-logging.sh
+ [  = no ]
+ [ no != no ]
+ do_start
+ start-stop-daemon --start --quiet --pidfile /var/run/privoxy.pid --exec /usr/sbin/privoxy --test
+ start-stop-daemon --start --quiet --pidfile /var/run/privoxy.pid --exec /usr/sbin/privoxy -- --pidfile /var/run/privoxy.pid --user privoxy /etc/privoxy/config
+ [ no != no ]
+ :
~


I still don't know where the problem is.

---

### Post by Brandon Williams on 2010-04-28
At this point you at least know where the problem isn't :-)  Init is attempting to start privoxy and all indications are that, at least as far as the init script is concerned, the attempt is successful.

After this, does that value in /var/run/privoxy.pid represent a running process? It might be useful to add this check to /etc/rc.local:
```
exec 3>&2
exec 2> /tmp/rc.local.log
set -x
if ! ps -fp $(cat /var/run/privoxy.pid)
then
    echo "Privoxy ($(cat /var/run/privoxy.pid)) is not running."
else
    echo "Privoxy ($(cat /var/run/privoxy.pid)) is running."
fi
set +x
exec 2>&3
```

This will at least tell you whether privoxy is still running by the time you get to /etc/rc.local. If it isn't, then the problem is in privoxy somewhere, and should be indicated in a log file somewhere, either the privoxy log or one of the system logs.

---

### Post by marllowe on 2010-04-28
In /tmp/rc.local.log was information that Privoxy isn't running.

> 
This will at least tell you whether privoxy is still running by the time you get to /etc/rc.local. If it isn't, then the problem is in privoxy somewhere, and should be indicated in a log file somewhere, either the privoxy log or one of the system logs.Yes, you were right! :-)
I searched the logs looking for 'privoxy' and I have found in /var/log/privoxy:

```
Apr 28 20:50:22.234 b774c8d0 Info: Privoxy version 3.0.13
Apr 28 20:50:22.267 b774c8d0 Info: Program name: /usr/sbin/privoxy
Apr 28 20:50:22.277 b774c8d0 Info: Listening on port 8118 on IP address localhost
Apr 28 20:50:22.278 b774c8d0 Error: Can not resolve localhost: Name or service not known
Apr 28 20:50:22.278 b774c8d0 Fatal error: can't bind to localhost:8118: The hostname is not resolvable
```So... I changed in /etc/privoxy/config 
```
listen-address  localhost:8118
```to
```
listen-address  127.0.0.1:8118
```and everything works !! :-)

Thank you very much for your help and for your time. Your instructions were very precise - THANK YOU! :-)
Regard,
Artur

---

