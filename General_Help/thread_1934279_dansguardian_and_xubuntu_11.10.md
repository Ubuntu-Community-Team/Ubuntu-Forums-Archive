---
title: "dansguardian and xubuntu 11.10"
date: 2012-03-01
forum: General Help
---

### Post by jaybob321 on 2012-03-01
Hi all-

Im very new to the ubuntu/linux world. 

I currently have a dual boot HP Mini 210 (Win 7 Starter and Xubuntu 11.10 32-bit partitioned harddrive...not thru Wubi)

I am trying to install Dansguardian/Squid on the Xubuntu side mostly by following this how-to

 [http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic](http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic)

Anyway after configuring both dansguardian and squid (with multiple noobie issues i was able to overcome using these forums) but now when Im near the last few steps and  trying to get all traffic thru the now filered port and I run into trouble with the following command.

sudo gedit /etc/init.d/tproxy

I have substited leafpad for gedit yet the command still wont open the right file and I cant find the one Xubuntu uses instead of the one listed for Ubuntu.

Help!!

(also please let me know if any of the remaining commands need to be altered to work for Xubuntu...Thanks)

---

### Post by Toz on 2012-03-02
Hello and welcome to the forums.

I would guess that you need to create that file if it doesn't exist. All its doing is running that one iptables command on startup.

Those instructions are a little dated. There are newer ones (yet similar) available at: [https://help.ubuntu.com/community/DansGuardian]("https://help.ubuntu.com/community/DansGuardian").

---

### Post by jaybob321 on 2012-03-02
Okay so then to create that file I just run that leafpad command in the terminal (sudo leafpad /etc/init.d/tproxy), it opens a blank file, and then ...? What does that file need to contain?

Does it need the scripts listed on that newer page you gave me(thanks for that by the way)? If so then which ones? 

Thanks for the help this forum has given me so far.

---

### Post by Toz on 2012-03-02
No worries.
If you are following the older instructions, then yes, open the blank file, add that one line into that file:
```
iptables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner proxy --dport 80 -j REDIRECT --to-port 8080
```
...save the file and continue with the instructions.

Whats interesting to me (sorry but I don't use this package/setup), is that the newer instructions include more iptables directives. If the older instructions don't work, you may wish to retry with the newer ones.

---

### Post by jaybob321 on 2012-03-04
now Im to the point that I can get it all to work like I want but whenever I reboot it goes back to not working. Obviously I still am messing up those last few steps.

I tried starting over from scratch with the "new" instructions but I got lost when it started talking about changing the owernship of the dansguardian log file. Im just too noobish for that step of instructions. i need a set that is "dumbed down' a bit cuz I still dont fully understand what is going on in the background when using the terminal commands.

I guess my specific questions are 1) when there are multiple "sudo" commands listed i have to do them 1 at a time right? I cant just copy and paste the whole block into a terminal window?

2) what should be the response from the terminal when the commands are executed correctly? Sometimes I see a visual response (ie more lines show up, stuff gets opened and written) and other times nothing happens and I'm not sure if the command did what it was supposed to or not.

---

### Post by Toz on 2012-03-04
> **jaybob321 said:**
> now Im to the point that I can get it all to work like I want but whenever I reboot it goes back to not working. Obviously I still am messing up those last few steps.

I tried starting over from scratch with the "new" instructions but I got lost when it started talking about changing the owernship of the dansguardian log file. Im just too noobish for that step of instructions. i need a set that is "dumbed down' a bit cuz I still dont fully understand what is going on in the background when using the terminal commands.

I guess my specific questions are 1) when there are multiple "sudo" commands listed i have to do them 1 at a time right? I cant just copy and paste the whole block into a terminal window?
Yes. Just copy and paste the commands and you see them. sudo grants you administrative privileges to turn those commands as they require elevated admin rights. 

> 2) what should be the response from the terminal when the commands are executed correctly? Sometimes I see a visual response (ie more lines show up, stuff gets opened and written) and other times nothing happens and I'm not sure if the command did what it was supposed to or not.
Depends on the command. In many cases there will be no visual response - they change will just be made.

---

### Post by jaybob321 on 2012-03-07
Sorry Ive been busy for a few days.  Anyway Im trying to run those newer instruction and when I get to this line:

sudo /etc/init.d/dansguardian start

This is the message I get:

Error opening/creating log file. (check ownership and access rights).
I am running as dansguardian and I am trying to open /var/log/dansguardian//access.log
                                                                                             [fail]

Suggestions??

---

### Post by Toz on 2012-03-08
I don't have dansguardian installed. Can you post back the contents of **/etc/init.d/dansguardian**?

Also, the instructions call on changing the ownership of the /var/log/dansguardian directory and files below. What does the following command return?
```
ls -l /var/log/dansguardian/*
```
...looks like a rights issue.

---

### Post by jaybob321 on 2012-03-14
contents of **/etc/init.d/dansguardian**?

#! /bin/sh
# Startup script for dansguardian
#
# description: A web content filtering plugin for web \
#              proxies, developed to filter using lists of \
#              banned phrases, MIME types, filename \
#              extensions and PICS labling.
# processname: dansguardian
# pidfile: /var/run/dansguardian.pid
# config: /etc/dansguardian/dansguardian.conf
### BEGIN INIT INFO
# Provides:          dansguardian
# Required-Start:    $remote_fs $network $syslog
# Required-Stop:     $remote_fs $network $syslog
# Default-Start:     2 3 4 5 
# Default-Stop:      0 1 6 
# Description: Starts dansguardian content proxy 
# short-description: dansguardian configuration
### END INIT INFO

#include lsb functions
. /lib/lsb/init-functions

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/dansguardian
NAME=dansguardian
DESC="DansGuardian"

ls -l /var/log/dansguardian/*
gives this reply
ls: cannot access /var/log/dansguardian/*: No such file or directory

Thanks for all this help. Obviously this is not something that I can work on everyday.

Thanks again

---

### Post by jaybob321 on 2012-03-14
I missed some of the contents of the file..the full file is this

#! /bin/sh
# Startup script for dansguardian
#
# description: A web content filtering plugin for web \
#              proxies, developed to filter using lists of \
#              banned phrases, MIME types, filename \
#              extensions and PICS labling.
# processname: dansguardian
# pidfile: /var/run/dansguardian.pid
# config: /etc/dansguardian/dansguardian.conf
### BEGIN INIT INFO
# Provides:          dansguardian
# Required-Start:    $remote_fs $network $syslog
# Required-Stop:     $remote_fs $network $syslog
# Default-Start:     2 3 4 5 
# Default-Stop:      0 1 6 
# Description: Starts dansguardian content proxy 
# short-description: dansguardian configuration
### END INIT INFO

#include lsb functions
. /lib/lsb/init-functions

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/dansguardian
NAME=dansguardian
DESC="DansGuardian"

CONFFILELOCATION=/etc/dansguardian/
#BINARYLOCATION=/usr/sbin/
#PIDDIR=/var/run/

grep -q ^UNCONFIGURED ${CONFFILELOCATION}dansguardian.conf && {
cat <<EOF
        DansGuardian has not been configured!
        Please edit ${CONFFILELOCATION}dansguardian.conf manually then rerun
        this script.
EOF
exit; }

test -x $DAEMON || exit 0
test -f ${CONFFILELOCATION}dansguardian.conf || exit 0

set -e

case "$1" in
  start)
    log_daemon_msg "Starting $DESC" "$NAME"
    test -d /var/lock/subsys || mkdir -p /var/lock/subsys
    start-stop-daemon --start --quiet --pidfile /var/run/$NAME.pid \
        --exec $DAEMON || log_end_msg 1
    log_end_msg 0
    ;;
  stop)
    log_daemon_msg "Stopping $DESC" "$NAME"
    start-stop-daemon --stop --quiet --retry 15 --oknodo --pidfile /var/run/$NAME.pid \
        --exec $DAEMON || log_end_msg 1
    log_end_msg 0
    ;;
  reload)
    log_action_begin_msg "Reloading $DESC configuration..."
    echo "Reloading $DESC configuration files."
    start-stop-daemon --stop --signal 1 --quiet --pidfile \
        /var/run/$NAME.pid --exec $DAEMON || log_action_end_msg 1
    log_action_end_msg 0
      ;;
  restart|force-reload)
    #
    #    If the "reload" option is implemented, move the "force-reload"
    #    option to the "reload" entry above. If not, "force-reload" is
    #    just the same as "restart".
    #
    log_daemon_msg "Restarting $DESC" "$NAME"
    start-stop-daemon --stop --quiet --retry 15 --oknodo --pidfile \
        /var/run/$NAME.pid --exec $DAEMON || log_end_msg 1
    start-stop-daemon --start --quiet --pidfile \
        /var/run/$NAME.pid --exec $DAEMON || log_end_msg 1
    log_end_msg 0
    ;;
  *)
    N=/etc/init.d/$NAME
    # echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
    log_action_msg "Usage: $N {start|stop|restart|force-reload}" >&2
    exit 1
    ;;
esac

exit 0

---

### Post by Toz on 2012-03-14
> **jaybob321 said:**
> ls -l /var/log/dansguardian/*
gives this reply
ls: cannot access /var/log/dansguardian/*: No such file or directory

Thanks for all this help. Obviously this is not something that I can work on everyday.

Thanks again

What does the following return:
```
sudo ls -l /var/log/dansguardian/*
```

If the directory doesn't exist, then do:
```
sudo mkdir -p /var/log/dansguardian
sudo touch /var/log/dansguardian/access.log

```

---

### Post by jaybob321 on 2012-03-21
The first time that script returned a message about no such file found. I ran the two scripts and now the response is
-rw-r--r-- 1 root root 0 2012-03-21 10:56 /var/log/dansguardian/access.log

the start dansguardian script still returns this however

* Starting DansGuardian dansguardian                                                               Error opening/creating log file. (check ownership and access rights).
I am running as dansguardian and I am trying to open /var/log/dansguardian//access.log

---

### Post by Toz on 2012-03-21
> /var/log/dansguardian//access.log

Can you post back the contents of your config file (/etc/dansguardian/dansguardian.conf)?

---

### Post by jaybob321 on 2012-04-20
Thanks for the help so far. I was messing around with other features of my xubuntuinstall and managed to screw it up so bad I had to delete the xubuntu partition and totally reinstall. Anyway I decided to follow the older instructions

[http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic](http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic)


Anyway I get everything to work perfectly but when I reboot, the protection is gone. Seems to me Im messing up the last command somehow.

the last command  sudo update-rc.d tproxy

shows this as a response

usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
       update-rc.d [-n] <basename> disable|enable [S|2|3|4|5]
        -n: not really
        -f: force

The disable|enable API is not stable and might change in the future.


Like I said, I cant get dansguardian to filter everything just great but all the protection goes away when I restart.

Do i need to update something? Does xubuntu have a slightly different script than ubuntu/ (along the lines of the gedit/leafpad difference?)

Thanks

---

### Post by jaybob321 on 2012-04-20
as an addition after Ive experiemented a litle more

going into firefox and resetting the proxy back to 127.0.0.1 makes my whole connection not work. i dont get the standard blocked message on eveything but nothing ever connects. google.com just loads and loads and loads etc

running the sudo /etc/init.d/squid restart  script makes eveything work again.

My question is can I add that script to the tproxy file or would I have to make a file for squid that runs on start up like the tproxy file?

---

### Post by Toz on 2012-04-20
> **jaybob321 said:**
> Thanks for the help so far. I was messing around with other features of my xubuntuinstall and managed to screw it up so bad I had to delete the xubuntu partition and totally reinstall. Anyway I decided to follow the older instructions

[http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic](http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic)


Anyway I get everything to work perfectly but when I reboot, the protection is gone. Seems to me Im messing up the last command somehow.

the last command  sudo update-rc.d tproxy

shows this as a response

usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
       update-rc.d [-n] <basename> disable|enable [S|2|3|4|5]
        -n: not really
        -f: force

The disable|enable API is not stable and might change in the future.


Like I said, I cant get dansguardian to filter everything just great but all the protection goes away when I restart.

Do i need to update something? Does xubuntu have a slightly different script than ubuntu/ (along the lines of the gedit/leafpad difference?)

Thanks

I think the command should be:
```
sudo update-rc.d tproxy defaults
```
...so it can setup the default permissions.

---

### Post by Toz on 2012-04-20
> **jaybob321 said:**
> as an addition after Ive experiemented a litle more

going into firefox and resetting the proxy back to 127.0.0.1 makes my whole connection not work. i dont get the standard blocked message on eveything but nothing ever connects. google.com just loads and loads and loads etc

running the sudo /etc/init.d/squid restart  script makes eveything work again.

My question is can I add that script to the tproxy file or would I have to make a file for squid that runs on start up like the tproxy file?

First, try fixing the tproxy startup (as per my previous post) to see if that fixes both problems. If not, a cludgy way would be to edit the tproxy file to read:
```

#!/bin/bash
iptables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner proxy --dport 80 -j REDIRECT --to-port 8080
/etc/init.d/squid restart
```

---

### Post by jaybob321 on 2012-04-21
Well I tried all that (didnt work) but now Ive discovered that if after I reboot the internet doesnt work at all and then I use the synaptic package manager to re-install squid...it filters perfectly like it is supposed to.

So my question now is how to a make a script to run in startup that will re install squid just like the synaptic package manager does?

I know reinstalling squid every time I reboot will get very old very fast.

Thanks

---

### Post by Toz on 2012-04-21
So, does running:
```
sudo iptables -t nat -A OUTPUT -p tcp -m owner ! --uid-owner proxy --dport 80 -j REDIRECT --to-port 8080
```
...and
```
sudo /etc/init.d/squid restart
```
...manually after reboot no longer work?

---

### Post by jaybob321 on 2012-04-26
Yes those two codes do work after reboot. I guess I messed them up when I tried them earlier.

I tried to make those two scripts using the settings manager>session and startup>application autostart

I used the new button to add a new startup application and I pasted the above codes into the "command" line.  I did one per script.  

Its not working I think its because they are not being executed in the proper order. The squid restart script is running before the iptables command instead of after and I cant figure out how to change the order that they are listed in.

is there a way to change the order or is there a better way to make these scripts run at startup?

Thanks

---

### Post by Toz on 2012-04-26
What does your rc2.d directory look like?
```
ls /etc/rc2.d
```

Maybe we can change the order of the startup of those 2 services there. If not, we can add the commands to /etc/rc.local.

---

### Post by jaybob321 on 2012-04-28
README                S20tproxy               S50saned         S99grub-common
S20clamav-freshclam   S20unattended-upgrades  S70dns-clean     S99ondemand
S20dansguardian       S25bluetooth            S70pppd-dns      S99rc.local
S20kerneloops         S50pulseaudio           S75sudo
S20speech-dispatcher  S50rsync                S99acpi-support

Ive already deleted the scripts I put in  settings manager>session and startup>application autostart

Right no I making due with just running the iptables script and the squid restart script you gave me. Its the first thing I do after evertyhing boots up and it works fine, its just getting a bit old.

Thanks

---

### Post by Toz on 2012-04-28
What happens if you add:
```
/etc/init.d/squid restart
```
...to the end of /etc/rc.local above the *exit 0* line? 

Post back the contents of your /etc/rc.local file to confirm along with:
```
ls -l /etc/rc.local
```

---

### Post by jaybob321 on 2012-05-08
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/etc/init.d/squid restart

exit 0

So far this seems to work great. Im not home to fully test it but it works fine for the wired hotel connection Ive been using. ill have to wait to try it on wifi for another few days but it should work as well.

Thank you thank you thank you!

---

