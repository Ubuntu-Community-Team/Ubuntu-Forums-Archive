---
title: "Ubuntu hangs on splashscreen during shutdown"
date: 2010-06-11
forum: General Help
---

### Post by sperwer on 2010-06-11
Hi!

Ubuntu hangs on splash screen when shutting down and restarting after creating startup scrip.

I created the upstart script using the following method:

sudo gedit /etc/init.d/local.autostart
"Edit local.autostart"

sudo chmod +x /etc/init.d/local.autostart
And
sudo update-rc.d local.autostart defaults 80.
After this ubuntu hangs on the splash screen during shut down.
If I remove the script by doing:
sudo update-rc.d -f local.autostart remove

Then ubuntu can restart once again.

Any clues are appreciated.

Sperwer

---

### Post by gzarkadas on 2010-06-11
Most probably, you have a bug in your script. Since it hangs it is either a loop that never ends, or an expected input that does not come, or maybe a deadlock if you happen to use pipes or fifos. 

Try to execute the script in isolation, from inside a terminal and see what happens. You may also post it here. You can also check your syslog, from menu: System|Administration|Log Files (or similar) for messages indicative of the type of failure, if any.

Check also that the script's permissions are indeed 755 (rwxr-xr-x); in case you have set in the past a more restrictive umask.

---

### Post by sperwer on 2010-06-13
Thx gzarkadas for ur sugestion.
I have been playing with the problem, but not getting any closer to a solution.

If i run the script manually there is no problem, though.
The local.autostart Script runs three script placed in the home folder.

/etc/init.d/local.autostart:
```
&#65279;#!/bin/sh -e
/home/tv-server/sasc3.sh
sleep 3
/home/tv-server/sasc.sh
sleep 5
/home/tv-server/sasc2.sh
```

/home/tv-server/sasc3.sh:
```
sudo oscam -b
```

/home/tv-server/sasc.sh:
```
cd /usr/local/src/sc/contrib/sasc-ng/
sudo modprobe dvbloopback num_adapters=2
```

/home/tv-server/sasc2.sh:
```
cd /usr/local/src/sc/contrib/sasc-ng/
sudo ./sasc-ng  -j 0:2 -j 1:3
```

I have been looking at the log's but so far havnt been able to locate the problem.

The reason for running the scripts is the need to be started in correct order and before start of mythbackend on my HTPC server.

Regards
Sperwer

---

### Post by gzarkadas on 2010-06-13
Probably some of your actions are out-of-context when the system stops. The start-up scripts follow a specific pattern: a passed in argument specifies the action that is requested and the script must act accordingly.

Try to use the code below as the contents of your script; since the scripts execute succesfully in isolation it will probably work. If you find errors when changing runlevels you may have to supply commands to stop the apps that you activate inside the (now empty) `run_scripts_stop' function.

```

&#65279;#!/bin/sh 

set -e

function log_error()
{
    logger -s -t local-autostart  "${1} returned non-zero exit code"
}

function run_scripts_start()
{
     /home/tv-server/sasc3.sh || log_error "sasc3.sh"
    sleep 3
    /home/tv-server/sasc.sh || log_error "sasc.sh"
    sleep 5
    /home/tv-server/sasc2.sh || log_error "sacc2.sh"
}

function run_scripts_stop()
{
}

case $1 in
start)
    run_scripts_start
    ;;
stop)
    run_scripts_stop
    ;;
status)
    echo "not implemented"
    ;;
restart|reload)
    run_scripts_stop
     run_scripts_start
    ;;
*)
    echo "Usage: $0 {start|stop|restart|reload|status}"
    exit 1
    ;;
esac

```

---

### Post by sperwer on 2010-06-13
THX gzarkadas

I belive the problem i solved.
Just had 10 restarts with minor problem on two of them.
In these two cases there were two problems a: apache2 didnt start and restart did only took me to the login screen from there I had to log in and go to terminal to do "sudo reboot".

Can you point me out where to learn more about the startup context.

Best regards
Sperwer

---

### Post by Naggobot on 2010-06-13
Small comment so that this thread wont confuse anyone. 

> I created the **upstart** script using the  following method:
sudo gedit /etc/**init.d**/local.autostart
...
sudo update-rc.d local.autostart defaults 80.
In Ubuntu (10.04 at least) upstart "scripts" are  

```
/etc/init/[jobname].conf
```and the file [jobname].conf is of form

```
# comment header
description    "description text"
start on ([event])
script
   [script text]    
end script

```and that is it. No need for update-rc.d. 

For several hours I tried to get a script to run properly through update-rc.d on runlevel 2 after the network has connected.  

All in all it took only about 15-30 minutes to get the upstart script working after I finally stumbled to correct web page [http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html). 

Now of course I need to emphasize that the reason I was unable get update-rc.d working is between the chair and the computer, but also this kind of implies that the upstart is easier to use.

---

### Post by gzarkadas on 2010-06-13
Yes, upstart scripts and init scripts are slightly different beasts. This is an init script that we are dealing with.

@sperwer:

A good link about init scripts: [Debian policy manual, section 9.3]("http://www.debian.org/doc/debian-policy/ch-opersys.html"). See also (inside a terminal):`man init' , `man telinit'.

The best to do IMHO is to study the source code of the scripts inside /etc/init.d. Note that the SysV init scheme is order-based: scripts are get run based on their naming order, thus the (S/K)xx prefixes. Upstart jobs are get run based on system events (ie asynchronously). Ubuntu has them both because it gradually migrates from the older scheme (SysV) to the newer (Upstart).

---

### Post by sperwer on 2010-06-19
thx both of you.
I will study both both links.

Sperwer

---

