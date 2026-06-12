---
title: "deluge /etc/init.d/ questions...."
date: 2010-03-25
forum: General Help
---

### Post by Darth_tater on 2010-03-25
so i am trying to set up a headless server... I used to sue vuze, but that program has gotten wayyyy to bloated, so i am trying my hand at deluge.

i followed this guide here: [http://ubuntuforums.org/showthread.php?t=1433783](http://ubuntuforums.org/showthread.php?t=1433783)

while there were bits and pieces of that that were not correct (didn't work for me.. i had to adapt them), i finally got deluge up and running perfectly with the web interface and flexget.

But here is the problem....  the /etc/init.d/ scripts that the guide uses do not work for me!  i went thought them (line by line) and made sure that everything was correct (the path's to the executable and  syntax) and as far as i could tell, there was no problem.

however, deluge *will not* start up on boot (as it should with the /etc/init.d/ scripts.

instead, i have to SSH in after it has booted and then start the deluge-web module anually.

from there, i can start the actual deluge daemon.

---- LOG FILES ----

THESE ARE IN CHRONOLOGICAL ORDER, AS IF TE MACHINE HAD *JUST* STARTED!


Checking to see if the deluge binaries are where they are supposed to be.  They are.

```

user@Coretana:/usr/bin$ ls -a | grep deluge
deluged
deluge-web
user@Coretana:/usr/bin$

```

At this point, i can not access the web interface (because it hasnt been loaded....)

so, lets go ahead and start it up:

```

user@Coretana:/usr/bin$ deluged
/usr/lib/pymodules/python2.6/deluge/ui/web/json_api.py:2        14: DeprecationWarning: BaseException.message has been deprecated as of Python 2        .6
  error = {"message": e.message, "code": 3}

/usr/lib/pymodules/python2.6/deluge/core/core.py:501: DeprecationWarning: Use get_session_status().
  warnings.warn("Use get_session_status().", DeprecationWarning)
/usr/lib/pymodules/python2.6/deluge/core/core.py:616: DeprecationWarning: Use get_session_status().
  warnings.warn("Use get_session_status().", DeprecationWarning)



```

That second warning comes from the web interface connecting.  the first error comes just seconds after starting up the daemon.

So this is what i have to go through to get things up and running.

Here is the logs directory:
```

user@Coretana:/var/log$ ls -a
.              cups                fsck          mail.info          syslog
..             daemon.log          gdm           mail.log           syslog.1
apparmor       debug               installer     mail.warn          udev
apt            dist-upgrade        jockey.log    messages           unattended-upgrades
auth.log       dkms_autoinstaller  jockey.log.1  news               user.log
boot           dmesg               kern.log      pm-powersave.log   wtmp
bootstrap.log  dpkg.log            lastlog       pycentral.log      x11vnc.log
btmp           faillog             lpr.log       samba              Xorg.0.log
ConsoleKit     fontconfig.log      mail.err      speech-dispatcher  Xorg.0.log.old


```


There is nothing here....  If anybody thinks that any of these will be useful, i will be more than happy to post them.

-----------

HERE IS MY /etc/init.d/deluge-daemon

[PHP]
#!/bin/sh
### BEGIN INIT INFO
# Provides:          deluge-daemon
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Should-Start:      $network
# Should-Stop:       $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Daemonized version of deluge and webui.
# Description:       Starts the deluge daemon with the user specified in
#                    /etc/default/deluge-daemon.
### END INIT INFO

# Author: Adolfo R. Brandes 
# Modified: Sami Olmari

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="Deluge Daemon"
NAME1="deluged"
NAME2="deluge-web"
DAEMON1=/usr/bin/deluged
DAEMON1_ARGS="-d -c /var/lib/deluge -l /var/log/deluged.log -L warning"
DAEMON2=/usr/bin/deluge-web
DAEMON2_ARGS="-p 9092 -c /var/lib/deluge -l /var/log/deluge-web.log -L warning"
PIDFILE1=/var/run/$NAME1.pid
PIDFILE2=/var/run/$NAME2.pid
PKGNAME=deluge-daemon
SCRIPTNAME=/etc/init.d/$PKGNAME

# Exit if the package is not installed
[ -x "$DAEMON1" -a -x "$DAEMON2" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$PKGNAME ] && . /etc/default/$PKGNAME

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

if [ -z "$RUN_AT_STARTUP" -o "$RUN_AT_STARTUP" != "YES" ]
then
   log_warning_msg "Not starting $PKGNAME, edit /etc/default/$PKGNAME to start it."
   exit 0
fi

if [ -z "$DELUGED_USER" ]
then
    log_warning_msg "Not starting $PKGNAME, DELUGED_USER not set in /etc/default/$PKGNAME."
    exit 0
fi

#
# Function that starts the daemon/service
#
do_start()
{
   # Return
   #   0 if daemon has been started
   #   1 if daemon was already running
   #   2 if daemon could not be started
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE1 --exec $DAEMON1 \
      --chuid $DELUGED_USER --user $DELUGED_USER --test > /dev/null
   RETVAL1="$?"
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE2 --exec $DAEMON2 \
      --chuid $DELUGED_USER --user $DELUGED_USER --test > /dev/null
   RETVAL2="$?"
   [ "$RETVAL1" = "0" -a "$RETVAL2" = "0" ] || return 1

   start-stop-daemon --start --background --quiet --pidfile $PIDFILE1 --make-pidfile --exec $DAEMON1 \
      --chuid $DELUGED_USER --user $DELUGED_USER -- $DAEMON1_ARGS
   RETVAL1="$?"
        sleep 2
   start-stop-daemon --start --background --quiet --pidfile $PIDFILE2 --make-pidfile --exec $DAEMON2 \
      --chuid $DELUGED_USER --user $DELUGED_USER -- $DAEMON2_ARGS
   RETVAL2="$?"
   [ "$RETVAL1" = "0" -a "$RETVAL2" = "0" ] || return 2
}

#
# Function that stops the daemon/service
#
do_stop()
{
   # Return
   #   0 if daemon has been stopped
   #   1 if daemon was already stopped
   #   2 if daemon could not be stopped
   #   other if a failure occurred

   start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --user $DELUGED_USER --pidfile $PIDFILE2
   RETVAL2="$?"
   start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --user $DELUGED_USER --pidfile $PIDFILE1
   RETVAL1="$?"
   [ "$RETVAL1" = "2" -o "$RETVAL2" = "2" ] && return 2

   rm -f $PIDFILE1 $PIDFILE2

   [ "$RETVAL1" = "0" -a "$RETVAL2" = "0" ] && return 0 || return 1
}

case "$1" in
  start)
   [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME1"
   do_start
   case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
   esac
   ;;
  stop)
   [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME1"
   do_stop
   case "$?" in
      0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
      2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
   esac
   ;;
  restart|force-reload)
   log_daemon_msg "Restarting $DESC" "$NAME1"
   do_stop
   case "$?" in
     0|1)
      do_start
      case "$?" in
         0) log_end_msg 0 ;;
         1) log_end_msg 1 ;; # Old process is still running
         *) log_end_msg 1 ;; # Failed to start
      esac
      ;;
     *)
        # Failed to stop
      log_end_msg 1
      ;;
   esac
   ;;
  *)
   echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
   exit 3
   ;;
esac

:

[/PHP]


Any and ALL help you can provide is immensely appreciated!!!:popcorn:

---

### Post by Woody1987 on 2010-03-26
You could try adding deluged and deluge-web to /etc/rc.local before the exit 0.

---

### Post by krunge on 2010-03-26
You don't appear to mention there being any run-level scripts symlinking back to the /etc/init.d script.  That is how services are started at boot time. E.g.:
```

$ ls -l /etc/rc3.d/S20openbsd-inetd 
lrwxrwxrwx 1 root root 23 2008-01-18 10:54 /etc/rc3.d/S20openbsd-inetd -> ../init.d/openbsd-inetd

```
The 'S' stands for start I believe; if it starts with 'K' that means kill that service when the system enters that runlevel. The presence of a script in /etc/init.d doesn't mean it is run at boot time. See the update-rc.d(8) and related manpages for more info.

---

### Post by Darth_tater on 2010-03-26
> **krunge said:**
> You don't appear to mention there being any run-level scripts symlinking back to the /etc/init.d script.  That is how services are started at boot time. E.g.:
```

$ ls -l /etc/rc3.d/S20openbsd-inetd 
lrwxrwxrwx 1 root root 23 2008-01-18 10:54 /etc/rc3.d/S20openbsd-inetd -> ../init.d/openbsd-inetd

```
The 'S' stands for start I believe; if it starts with 'K' that means kill that service when the system enters that runlevel. The presence of a script in /etc/init.d doesn't mean it is run at boot time. See the update-rc.d(8) and related manpages for more info.

Sorry about that...  i set them up as per the guide:

> 
sudo update-rc.d deluge-daemon defaults


and this is the result:

```

user@Coretana:~$ ls -l /etc/rc3.d/S20deluge-daemon
lrwxrwxrwx 1 root root 23 2010-03-25 22:29 /etc/rc3.d/S20deluge-daemon -> ../init.d/deluge-daemon


```

---

### Post by Darth_tater on 2010-03-26
SOLVED.

the /etc/init.d script provided with the example is not entirely correct.  the path's to the config files were incorrect and there were a few other problems with the log files.

i fixed those and it still isint working, so i went with the suggestion to put everything in /etc/rc.local

and boom!  it works perfectly!

so, thats all folks.

---

### Post by McButt on 2010-03-27
I'm glad you solved it this way, but I did notice you must've skipped some parts of that guide you linked. If you follow it exactly I don't think you'll run into these problems.;)

---

### Post by Redsandro on 2010-05-02
> **Darth_tater said:**
> SOLVED.

the /etc/init.d script provided with the example is not entirely correct.  the path's to the config files were incorrect and there were a few other problems with the log files.

i fixed those and it still isint working, so i went with the suggestion to put everything in /etc/rc.local

and boom!  it works perfectly!

so, thats all folks.

Could you elaborate on what you did?
I consider myself savvy enough but I cannot get the thing to work either.
If I have the init.d scripts in place, nothing runs, but I cannot start the daemon from deluge (gui) either, but when I remove the scripts again, I can start the daemon from deluge (gui) fine.

I want the daemon to run on startup. I guess it needs to be root because my home is encrypted, right?

---

### Post by Darth_tater on 2010-05-02
To be honest, i dont remember exactly what i did.

i havent been in touch with or had access to the machine i did this work on in quite a while (since a few days after i started this thread).

i am at university for another 2 weeks, and then i will have a change to go home and look @ this machine.

If you are still interested / havent figured out the problem by then, i will be more then happy to take a look @ the machine to try and figure out what it is that i did.

---

### Post by Redsandro on 2010-05-02
Thanks, meanwhile I'll try some different routes.

---

### Post by Darth_tater on 2010-05-03
ok,  I'll add it to my todo list to come back here and update you once im done with finals.

---

### Post by Darth_tater on 2010-05-23
the encryption on your home directory might be effecting this.

but i dont think any of the config files were actually stored in the /home/USER directory.

either way i took down this setup because the daemon that was *supposed* to can rss feeds for new items wasn't working.

I reformatted and installed 10.04 and went back to my old Vuze + Scane RSS setup which *is* working flawlessly


I am sorry i couldn't be of much help.

---

### Post by Redsandro on 2010-05-23
Thanks for getting back at this.
I have everything in an unencrypted user now but I still cannot get it to work as daemon. I cannot start a new daemon when the automatic daemon is scripted to start although **not even running**. I cannot connect through webUI either.

My solution is to let a restricted account, which I use for mediacenter purposes anyway, autologin. From there, automatically start deluge in non-classic mode (daemon+client). Now it runs sort of as a daemon, that account is logged in always anyway. WebUI works now, too. When I login, I have to connect, ironically, to a daemon.

It's not perfect but in essence it's the same now as it would have when it worked.

Flexget works perfect for rss feeds, rediculously customizable. Takes some efford to understand but it's pretty sweet.

---

### Post by Darth_tater on 2010-05-23
glad to hear you got it working!

I had flexget set up perfectly... it worked flawlessly for a few days.

then it just stopped.

and never worked properly.

Oh well.  to each his own.

---

### Post by Redsandro on 2010-05-23
That's annoying. When things just stop working and you know there's probably a good explanation but it will take forever to figure out. It's one of those downsides of linux. :)

---

### Post by yochaigal on 2010-06-22
In case this helps anyone...

I originally tried the init script provided by the deluge dev site, but in the end simply added this to my /etc/rc.local file:


su - yochai -c "deluged -c /home/yochai/.config/deluge -p 58846 -l /home/yochai/deluged.log -L warning"
su - yochai -c "deluge-web -p 8112 -l /home/yochai/deluge-web.log -L warning"
exit 0

this essentially runs deluge as my user on a specific port, then does the same for the web interface.


yes, I know it lacks the start/stop functionality of the init script, but this was much simpler and didn't give me any of the issues I had before (mostly permission stuff).  Perhaps the updated init script from their website would be a better solution now, but I still thought this was a useful option.

now if only I could figure out how to get the web interface to auto-connect to the deluge daemon...

---

