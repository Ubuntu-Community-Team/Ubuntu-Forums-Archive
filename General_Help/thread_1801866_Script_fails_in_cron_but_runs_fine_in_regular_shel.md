---
title: "Script fails in cron but runs fine in regular shell"
date: 2011-07-11
forum: General Help
---

### Post by hyperbart on 2011-07-11
I have an Ubuntu server running Couch Potato, Sick Beard and Sabnzbdplus. Everything "works" pretty well in a sense that CP and SB push the NZB's to Sabnzbdplus, but Sab crashes regularly (haven't found the solution or the cause for this problem, so if you have some advice regarding that, it's welcome).

To counter this problem (Sab crashing) I have a script written which checks if Sab is runnning and if it isn't start it:


```
bart@Pyro:~$ cat CheckSabRunning.sh
#!/bin/sh
SERVICE='sabnzbdplus'

if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE service running, everything is fine"
else
    echo "$SERVICE is not running"
    /etc/init.d/sabnzbdplus start
fi
```When I run this script from the shell, no problem at all, if Sab is not running it starts it, if Sab is running it shows me the "everything is fine" message.

I thought: well let's throw it in my crontab then... Did that, but it doesn't work, so I decided to push the result of the cron-line to a log file:

```
sabnzbdplus service running, everything is fine
sabnzbdplus is not running
 * Starting SABnzbd+ binary newsgrabber
   ...fail!
sabnzbdplus is not running
 * Starting SABnzbd+ binary newsgrabber
   ...fail!
sabnzbdplus is not running
 * Starting SABnzbd+ binary newsgrabber
   ...fail!
sabnzbdplus is not running
 * Starting SABnzbd+ binary newsgrabber
   ...fail!
sabnzbdplus is not running
 * Starting SABnzbd+ binary newsgrabber
   ...fail!
sabnzbdplus is not running
 * Starting SABnzbd+ binary newsgrabber
   ...fail!
```What is happening here, why doesn't it work? The Crontab is my crontab as regular user "bart" (I'm the only user on the server)

---

### Post by tredegar on 2011-07-11
> The Crontab is my crontab as regular user "bart" (I'm the only user on the server)
Here lies the problem, I think.
Your crontab scripts run as yourself, but
**/etc/init.d/sabnzbdplus start**
probably needs to be run as root.

Do you not need to run **sudo ./CheckSabRunning.sh** from your terminal?

---

### Post by dethorpe on 2011-07-11
This may not be the reasin but one thing that can cause this is that cron dosn't automatically source the user environment settings in .bashrc, .profile, .cshrc etc like the terminal does. So if your script requries any of those settings such as paths, or particuler environment variables it will fail.
 
I've seen that cause cron jobs to fail that work on command line many times. You can get round that in a anumber of ways, such as explicitly sourcing your profile in the crontab command, making sure your script isn't dependent on it or setting any environment variables you need in the crontab file itself (PATH etc).
 
As its the "/etc/init.d/sabnzbdplus start" command that is failing would be worth checking that to see what it does and if it relies on the users environment.
 
you can make the cronjob source your profile by adding it to the command in the file:
 
   . /home/username/.bashrc;script

Or just sourcing it in your script itself
 
Hope that helps

---

### Post by hyperbart on 2011-07-11
> **tredegar said:**
> Here lies the problem, I think.
Your crontab scripts run as yourself, but
**/etc/init.d/sabnzbdplus start**
probably needs to be run as root.

Do you not need to run **sudo ./CheckSabRunning.sh** from your terminal?

Nope, that's not the issue because Sabnzbd can be started without sudo-rights:

```
bart@Pyro:~$ /etc/init.d/sabnzbdplus start
 * Starting SABnzbd+ binary newsgrabber
   ...done.

```So adding this line in my script:

```
    . /home/username/.bashrc;script
```Should do the trick?

I need a little bit of walkthrough here...

---

### Post by dethorpe on 2011-07-11
If the problem is the environment not being set then in your crontab rather than just the script name as the command enter it like this:
 
 
```

. /home/bart/.bashrc;CheckSabRunning.sh

```
 
(assuming your home is /home/bart, if not change that bit to whatever your home dir is)
 
That should source your profile then run your script. Of course that may not be the problem, if still not working post cron output and the /etc/init.d/sabnzbdplus script and I can have a look to see if theres anything else i can see

---

### Post by tredegar on 2011-07-11
What dethorpe is suggesting is that you source your bashrc in your script like this:```
#!/bin/sh
[COLOR="Red"].  /home/bart/.bashrc[/COLOR]
SERVICE='sabnzbdplus'

if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE service running, everything is fine"
else
    echo "$SERVICE is not running"
    /etc/init.d/sabnzbdplus start
fi
```
But I think it is .profile you may need to run.
```
#!/bin/sh
[COLOR="Red"].  /home/bart/.profile[/COLOR]
SERVICE='sabnzbdplus'

if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE service running, everything is fine"
else
    echo "$SERVICE is not running"
    /etc/init.d/sabnzbdplus start
fi
```
Try them both?

---

### Post by hyperbart on 2011-07-11
With this:
```
#!/bin/sh
SERVICE='sabnzbdplus'
.  /home/bart/.bashrc

if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE service running, everything is fine"
else
    echo "$SERVICE is not running"
    /etc/init.d/sabnzbdplus start
fi
```

I get this as output when i run the script myself in the shell:

```
bart@Pyro:~$ sh CheckSabRunning.sh
/home/bart/.bashrc: 13: shopt: not found
/home/bart/.bashrc: 21: shopt: not found
/home/bart/.bashrc: 103: shopt: not found
/etc/bash_completion: 32: [[: not found
/etc/bash_completion: 38: [[: not found
/etc/bash_completion: 51: Bad substitution
bart@Pyro:~$
```

With this one:


```
#!/bin/sh
.  /home/bart/.profile
SERVICE='sabnzbdplus'

if ps ax | grep -v grep | grep $SERVICE > /dev/null
then
    echo "$SERVICE service running, everything is fine"
else
    echo "$SERVICE is not running"
    /etc/init.d/sabnzbdplus start
fi
```

I get a failed, just like before in cron, but it runs when i do it in the shell myself...

My sabnzbdplus script in /etc/init.d :

```
#!/bin/sh
#
# Copyright (C) 2008-2010 by JCF Ploemen <linux@jp.pp.ru>
# released under GPL, version 2 or later

################################################
#                                              #
#  TO CONFIGURE EDIT /etc/default/sabnzbdplus  #
#                                              #
################################################

### BEGIN INIT INFO
# Provides:          sabnzbdplus
# Required-Start:    $local_fs $network $remote_fs
# Required-Stop:     $local_fs $network $remote_fs
# Should-Start:      NetworkManager
# Should-Stop:       NetworkManager
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: SABnzbd+ binary newsgrabber
### END INIT INFO

DAEMON=/usr/bin/sabnzbdplus
SETTINGS=/etc/default/sabnzbdplus

([ -x $DAEMON ] && [ -r $SETTINGS ]) || exit 0

DESC="SABnzbd+ binary newsgrabber"
DEFOPTS="--daemon"
PYTHONEXEC="^$(sed -n '1s/^#\!\([a-z0-9\.\/]\+\)\(.*\)/\1(\2)?/p' $DAEMON)"
PIDFILE=/var/run/sabnzbdplus.pid
SETTINGS_LOADED=FALSE

# these are only accepted from the settings file
unset USER CONFIG HOST PORT EXTRAOPTS

. /lib/lsb/init-functions

check_retval() {
    if [ $? -eq 0 ]; then
        log_end_msg 0
        return 0
    else
        log_end_msg 1
        exit 1
    fi
}

is_running() {
    # returns 0 when running, 1 otherwise
    PID="$(pgrep -f -x -u $USER "$PYTHONEXEC $DAEMON $DEFOPTS.*")"
    RET=$?
    [ $RET -gt 1 ] && exit 1 || return $RET
}

load_settings() {
    if [ $SETTINGS_LOADED != "TRUE" ]; then
        . $SETTINGS

        [ -z "$USER" ] && {
            log_warning_msg "$DESC: not configured, aborting. See $SETTINGS";
            return 1; }

        OPTIONS="$DEFOPTS"
        [ -n "$CONFIG" ] && OPTIONS="$OPTIONS --config-file $CONFIG"
        [ -n "$HOST" ] && SERVER="$HOST" || SERVER=
        [ -n "$PORT" ] && SERVER="$SERVER:$PORT"
        [ -n "$SERVER" ] && OPTIONS="$OPTIONS --server $SERVER"
        [ -n "$EXTRAOPTS" ] && OPTIONS="$OPTIONS $EXTRAOPTS"
        SETTINGS_LOADED=TRUE
    fi
    return 0
}

start_sab() {
    load_settings || exit 0
    if ! is_running; then
        log_daemon_msg "Starting $DESC"
        start-stop-daemon --quiet --chuid $USER --start --exec $DAEMON -- $OPTIONS
        check_retval
        # create a pidfile; we don't use it but some monitoring app likes to have one
        [ -w $(dirname $PIDFILE) ] && \
            pgrep -f -x -n -u $USER "$PYTHONEXEC $DAEMON $OPTIONS" > $PIDFILE
    else
        log_success_msg "$DESC: already running (pid $PID)"
    fi
}

stop_sab() {
    load_settings || exit 0
    if is_running; then
        TMPFILE=$(mktemp /tmp/sabnzbdplus.XXXXXXXXXX || exit 1)
        trap '[ -f $TMPFILE ] && rm -f $TMPFILE' EXIT
        echo "$PID" > $TMPFILE
        log_daemon_msg "Stopping $DESC"
        start-stop-daemon --stop --user $USER --pidfile $TMPFILE --retry 30
        check_retval
    else
        log_success_msg "$DESC: not running"
    fi
    [ -f $PIDFILE ] && rm -f $PIDFILE
}

case "$1" in
    start)
        start_sab
    ;;
    stop)
        stop_sab
    ;;
    force-reload|restart)
        stop_sab
        start_sab
    ;;
    status)
        load_settings || exit 4
        if is_running; then
            log_success_msg "$DESC: running (pid $PID)"
        else
            log_success_msg "$DESC: not running"
            [ -f $PIDFILE ] && exit 1 || exit 3
        fi
    ;;
    *)
        log_failure_msg "Usage: $0 {start|stop|restart|force-reload|status}"
        exit 3
    ;;
esac

exit 0

```

---

### Post by tredegar on 2011-07-11
Hah! Just noticed the first line of your script is **#!/bin/sh**
Do you *really* want to use **sh** ?
You are using **bash** in your terminal
Try **#!/bin/bash** as the first line of your cronscript.

---

### Post by mister_p_1998 on 2011-07-11
Where are you telling the script to echo to?

If I run a GUI app in cron I have to tell it which display to run it on eg:

20 08 * * 1-5 DISPLAY=:0 &&  /usr/bin/cvlc [http://www.radioparadise.com/musiclinks/rp_128.m3u](http://www.radioparadise.com/musiclinks/rp_128.m3u)

Note the DISPLAY=:0  that means display output on the first video display, you aren't telling it where to display, so I reckon your problem lies in that area. If you run from a terminal it displays to the same terminal, that explains why it works manually.

BTW I do the same job using Hellanzb and Leechr, its been running fine for over a year and never crashes. Might be worth giving it a try.

---

### Post by hyperbart on 2011-07-11
Changed that, didn't work, don't get an error though about sourcing my profile now with .profile or bashrc...

Mister P, that would be strange, because my "move everything to my nas" script runs without those parameters you mentioned, just like my subtitle search script and everything...

---

### Post by dethorpe on 2011-07-11
Looks like .profile or .bashrc  are not the problem then, can't see anything in the init'd start script that relies on them, its all hardcoded or configered from the settings file /etc/default/sabnzbdplus, which is what i'd expect for an init.d script anyway.
 
The DISPLAY variable setting shouldn't be needed unless its a GUI app, but i don't think this is, its just a command line script.
 
Could try removing the --quiet option from start-stop-daemon command in the start_sab() function of the /etc/init.d script  to see if it kicks out any more info on whats failing?

---

### Post by mister_p_1998 on 2011-07-12
> **hyperbart said:**
> Changed that, didn't work, don't get an error though about sourcing my profile now with .profile or bashrc...

Mister P, that would be strange, because my "move everything to my nas" script runs without those parameters you mentioned, just like my subtitle search script and everything...

Yes it will work because you're not trying to:

echo "$SERVICE service running, everything is fine"
else
    echo "$SERVICE is not running"

If you echo to an output screen, it needs to know which one!
If you're just running a task in the background, it doesn't need an output screen.

---

### Post by hyperbart on 2011-07-12
Meanwhile, we found the problem: the startupscript from sabnzbd is very strict about a daemon parameter or something (a colleague helped). I changed it, en now everything is running fine...

---

### Post by tredegar on 2011-07-12
> Meanwhile, we found the problem: the startupscript from sabnzbd is very strict about a daemon parameter or something (a colleague helped). I changed it, en now everything is running fine...
Good.

But this is how the linux forums work on the internet:

- You post a problem.
- We try to help.
- Eventually you (hopefully) solve your problem, with the advice offered freely. So, it's working for you now. Good.

But the next step is very important:

- You should post _exactly_ what solved your problem, so this information can then help others (if they can use a search engine), even if you cannot be bothered to help them individually,  as we have at least tried to help you.

If you cannot answer this, perhaps show your colleague this post, and they'll be able to reply. It would be appreciated.

In summary, what were the changes your colleague made to the startup script from sabnzbd (that you previously posted) that solved your, and perhaps other people's future problems?

---

