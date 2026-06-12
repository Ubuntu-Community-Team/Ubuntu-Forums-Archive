---
title: "SLiM troubles"
date: 2011-04-11
forum: General Help
---

### Post by El_Belgicano on 2011-04-11
A few days ago, I installed SLiM from the repos, all went well.
I started customizing the theme and configuration file /etc/slim.conf, no problems (yet) to be noticed.
I went a bit deeper into using the multi-session capabilities of slim to load different 'profiles' depending on the network I wanted to connect to, since I'm only using openbox, that is not a problem.
The thing is, all the modifications worked, once or twice, then at some point I must have screwed it up because slim does not start openbox right anymore.

*_The symptoms:_*
**(1)** when using the "text" argument in the grub commandline, slim does not load, I drop to the console login interface, login is good, everything working like it should. (expected behaviour)
**(2)** when using "quiet splash" in the grub commandline, slim does get loaded, the theme appears right, but after login and when openbox has been loaded, I can get the rightclick menu, but no application gets loaded when clicked on.
**(3)** when using no arguments in the grub commandline, I got a black screen where slim should be.
**(4)** a few times, slim would ask me for a password, then a username, then a password again, before loading the .xinitrc.

At the moment I'm using number 1 as a workaround, I switch the arguments in grub before loading anything, but I'd like slim to work right.

*_The files:_*
**(a) /etc/slim.conf**
```
default_path        /bin:/usr/bin:/usr/local/bin:/usr/bin/X11
default_xserver     /usr/bin/X11/X
xserver_arguments   -nolisten tcp
halt_cmd            /sbin/shutdown -h now
reboot_cmd          /sbin/shutdown -r now
console_cmd         /usr/bin/xterm -C -fg white -bg black +sb -T "Console login" -e /bin/sh -c "/bin/cat /etc/issue.net; exec /bin/login"
xauth_path          /usr/bin/X11/xauth
authfile            /var/run/slim.auth
numlock             on
hidecursor          false
login_cmd           exec /bin/sh - ~/.xinitrc %session
daemon              yes
sessions            UGentLan,HomeWLan,UGentWLan,NoNetwork
screenshot_cmd      scrot /home/user/slim.png
welcome_msg         Welcome to %host
session_msg         Network: 
shutdown_msg        The system is halting...
reboot_msg          The system is rebooting...
default_user        user
focus_password      yes
auto_login          no
current_theme       dark
lockfile            /var/run/slim.lock
logfile             /var/log/slim.log
```

**(b) /etc/init.d/slim** (the part in bold comes from [HERE]("http://ubuntuforums.org/showthread.php?t=1723874") and this enables me to trigger the "symptom 1"-behaviour.
```
#!/bin/sh

# Largely adapted from xdm's init script:
# Copyright 1998-2002, 2004, 2005 Branden Robinson <branden@debian.org>.
# Copyright 2006 Eugene Konev <ejka@imfi.kspu.ru>

### BEGIN INIT INFO
# Provides:          slim
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Should-Start:      xfs $named slapd
# Should-Stop:       xfs $named slapd
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start/stop the SLiM daemon.
### END INIT INFO

test -z "$HEED_DEFAULT_DISPLAY_MANAGER" && HEED_DEFAULT_DISPLAY_MANAGER=true
DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager

DAEMON=/usr/bin/slim
PIDFILE=/var/run/slim.lock

SSD_START_ARGS="--pidfile $PIDFILE --name $(basename $DAEMON) --startas $DAEMON -- -d"
SSD_STOP_ARGS="--pidfile $PIDFILE --name $(basename $DAEMON) --retry TERM/5/TERM/5"

case $1 in
  start)
[B]    for ARG in $(cat /proc/cmdline)
    do
      case "${ARG}" in
        text|-s|s|S|single)
          plymouth quit || :
          exit 0
          ;;
      esac
    done[/B]
    if [ "$HEED_DEFAULT_DISPLAY_MANAGER" = "true" ] &&
       [ -e $DEFAULT_DISPLAY_MANAGER_FILE ] &&
       [ "$(cat $DEFAULT_DISPLAY_MANAGER_FILE)" != "$DAEMON" ]; then
      echo "Not starting X display manager (slim); it is not the default display manager."
    else
      echo -n "Starting X display manager: slim"
      start-stop-daemon --start --quiet $SSD_START_ARGS || echo -n " already running"
      echo "."
    fi
  ;;

  stop)
    echo -n "Stopping X display manager: slim"
    if ! [ -f $PIDFILE ]; then
      echo -n " not running ($PIDFILE not found)"
    else
      start-stop-daemon --stop --quiet $SSD_STOP_ARGS
      SSD_RES=$?
      if [ $SSD_RES -eq 1 ]; then
        echo -n " not running"
      fi
      if [ $SSD_RES -eq 2 ]; then
        echo -n " not responding to TERM signals"
      else
    if [ -f $PIDFILE ]; then
      echo -n " (removing stale $PIDFILE)"
      rm $PIDFILE
    fi
      fi
    fi
    echo "."
  ;;

  restart)
    $0 stop
    sleep 2
    $0 start
  ;;

  force-reload)
    /etc/init.d/slim restart
  ;;

  *)
    echo "Usage: /etc/init.d/slim {start|stop|restart|force-reload}"
    exit 1
  ;;
esac

# End of file

```

**(c) ~/.xinitrc**
```
#!/bin/sh
case $1 in
UGentLan)
	~/.scripts/networkconnect ul &
	;;
HomeWLan)
	~/.scripts/networkconnect hw &
	;;
UGentWLan)
	~/.scripts/networkconnect uw &
	;;
esac
xcompmgr -fF -I 0.1 -O 0.1 -D 20 &
gnome-power-manager &
#numlockx on &
nitrogen --restore &
gnome-keyring-daemon &
conky -p 20 -c ~/.conkyrctest &
conky -p 20 -c ~/.conkyrcmpd &
conky -p 10 -c ~/.conkyrcmini &
conky -p 10 -c ~/.conkyrcmini2 &
conky -p 20 -c ~/.conkyrcweather &
conky -p 20 -c ~/.conkyrc &
(sleep 2 && tint2) &
(sleep 2 && ~/.config/adeskmenu/adeskmenu) &
(sleep 2 && adeskbar) &
exec openbox-session
```

Should you need something more, just ask, I'll be happy to provide it to you.

Thank you for your time.

---

