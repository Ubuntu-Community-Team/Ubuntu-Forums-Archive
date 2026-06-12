---
title: "How do I make my computer lock out the user on a schedule?"
date: 2009-07-21
forum: General Help
---

### Post by Endolith on 2009-07-21
I have no self-control, and I often find myself on the Internet until several hours after I told myself I would go to sleep.  :)

How would I schedule my computer to lock me out at a certain time?

I guess what I'm imagining is that it would forcefully set the screensaver with password lock out at a certain time on weeknights.  Since I'll occasionally still want to use it past the time I set for myself, I'm thinking that it would forcefully lock me out, I could enter my password and continue using it, after 10 minutes it would lock me out again, etc. like a Snooze button on an alarm.  Of course it should stop with the repeated lockouts in the morning.

---

### Post by michy99 on 2009-07-21
I don't know if this will help or not. It is really for parents to control the time their kids spend on the computer, but it might give you some ideas.

[http://ubuntuforums.org/showthread.php?t=887769](http://ubuntuforums.org/showthread.php?t=887769)

---

### Post by michy99 on 2009-07-21
Also, have you looked at the forced typing break function under keyboard preferences?

---

### Post by Sidewinder1 on 2009-07-21
Most scheduling (by time. login, etc.) is done from the command line (Terminal) with the "cron" command. Open a terminal and enter:
```
man cron
```
and you should get something like this:

NAME
       cron - daemon to execute scheduled commands (Vixie Cron)

SYNOPSIS
       cron [-f] [-l] [-L loglevel]

DESCRIPTION
       cron is started automatically from /etc/init.d on entering multi-user runlevels.

OPTIONS
       -f      Stay in foreground mode, don’t daemonize.

       -l      Enable LSB compliant names for /etc/cron.d files

       -L loglevel
               Sets  the  loglevel  for  cron. The standard logging level (1) will log the start of all the cron jobs. A higher loglevel (2) will cause cron to log also the end of all
               cronjobs, which can be useful to audit the behaviour of tasks run by cron. Logging will be disabled if the loglevel is set to zero (0).

NOTES
       cron searches its spool area (/var/spool/cron/crontabs) for crontab files (which are named after accounts in /etc/passwd); crontabs found are loaded  into  memory.   Note  that
       crontabs in this directory should not be accessed directly - the crontab command should be used to access and update them.

       cron  also  reads /etc/crontab, which is in a slightly different format (see crontab(5)).  Additionally, cron reads the files in /etc/cron.d: it treats the files in /etc/cron.d
       as in the same way as the /etc/crontab file (they follow the special format of that file, i.e. they include the user field). However, they are independent of /etc/crontab: they
       do  not,  for  example,  inherit environment variable settings from it. The intended purpose of this feature is to allow packages that require finer control of their scheduling
       than the /etc/cron.{daily,weekly,monthly} directories to add a crontab file to /etc/cron.d. Such files should be named after the package that supplies them. Files must  conform
       to  the  same naming convention as used by run-parts(8): they must consist solely of upper- and lower-case letters, digits, underscores, and hyphens. If the -l option is speci&#8208;
       fied, then they must conform to the LSB namespace specification, exactly as in the --lsbsysinit option in run-parts.

       Like /etc/crontab, the files in the /etc/cron.d directory are monitored for changes. In general, the admin should not use /etc/cron.d/, but  use  the  standard  system  crontab
       /etc/crontab.

       cron  then wakes up every minute, examining all stored crontabs, checking each command to see if it should be run in the current minute.  When executing commands, any output is
       mailed to the owner of the crontab (or to the user named in the MAILTO environment variable in the crontab, if such exists).  The children copies of  cron  running  these  pro&#8208;
       cesses have their name coerced to uppercase, as will be seen in the syslog and ps output.

       Additionally, cron checks each minute to see if its spool directory’s modtime (or the modtime on /etc/crontab) has changed, and if it has, cron will then examine the modtime on
       all crontabs and reload those which have changed.  Thus cron need not be restarted whenever a crontab file is modified.  Note that the crontab(1) command updates the modtime of
       the spool directory whenever it changes a crontab.

       Special  considerations  exist  when  the  clock is changed by less than 3 hours, for example at the beginning and end of daylight savings time. If the time has moved forwards,
       those jobs which would have run in the time that was skipped will be run soon after the change.  Conversely, if the time has moved backwards by less than 3  hours,  those  jobs
       that fall into the repeated time will not be re-run.

       Only  jobs  that run at a particular time (not specified as @hourly, nor with ’*’ in the hour or minute specifier) are affected. Jobs which are specified with wildcards are run
       based on the new time immediately.

       Clock changes of more than 3 hours are considered to be corrections to the clock, and the new time is used immediately.

       cron logs its action to the syslog facility ’cron’, and logging may be controlled using the standard syslogd(8) facility.

SEE ALSO
       crontab(1), crontab(5)

AUTHOR
       Paul Vixie <paul@vix.com>


HTH, 
Side

---

### Post by Endolith on 2009-07-21
> **Sidewinder1 said:**
> Most scheduling (by time. login, etc.) is done from the command line (Terminal) with the "cron" command.

I think you mean Gnome Schedule.  ;)

[This]("http://ubuntuforums.org/showpost.php?p=5578771&postcount=3") looks promising.

---

### Post by Sidewinder1 on 2009-07-21
Seems that's exactly what you're lookin' for...
{Sidewinder walks away with head held low, embarrassed...}

---

### Post by VCoolio on 2009-07-21
You could also use "sudo shutdown -hP blah" and replace "blah" with the time you allow yourself to roam the internet, e.g. "+m 30" for 30 minutes, or "23:59" to shutdown at that time (24 hour format).

---

### Post by zacktu on 2009-07-21
Check out the man page for shutdown.  If you see that you want to be kicked off an hour from now, just type

sudo shutdown +60

and your computer will shut down 60 minutes from now.  Of course, you can cancel it with ^C, but then you can kill any other process as well.

---

### Post by Endolith on 2009-07-21
I don't want to shut it down, just lock out the screen.  (If my computer suspended correctly, I'd want it to suspend, but the [second biggest problem users have]("http://brainstorm.ubuntu.com/most_popular_ever/") is not very high on Canonical's priorities, I guess...)

Anyway, I found that Gnome Screensaver can be activated from the command line, and it works from within Gnome Schedule.

```
gnome-screensaver-command --lock
```I'm not sure whether to use --lock or --activate.  They both seem to do the same thing.

  ```

 -q, --query                Query the state of the screensaver
 -l, --lock                 Tells the running screensaver process to lock the screen immediately
 -a, --activate             Turn the screensaver on (blank the screen)

```So I'm thinking I could either:


[LIST]
[*]Create a script that checks the current time, queries the screensaver if it's on the 10s, starts the screensaver if it's down, and kills itself if it's morning. Then schedule the script to execute every weeknight at bedtime
[*]Mess with cron and set it to execute a short shell command to query and activate the screensaver, and have it execute every 10 minutes from a certain time to a certain time on certain days.
[/LIST]

---

### Post by Endolith on 2009-07-21
Here's what I made:

[php]#!/usr/bin/env python
# -*- coding: utf-8 -*-

# Use the Gnome screensaver to enforce bedtime or otherwise lock out the computer

# Note that the actual time it warns the user is whenever you call the script,
# so you can use more granularity than an hour, can set it for different times 
# on different days, etc.

import time
import pynotify
from subprocess import Popen, PIPE

appname      = 'Bedtime' # In case you want to use it for something else
bedtime      = 12 + 9    # (hours) Time before which the script should refuse to run
morning      = 5         # (hours) Time after which the script should quit and stop locking out the user
grace_period = 20        # (minutes) Time between warning and locking out
snooze_time  = 10        # (minutes) Time between logging back in and being locked back out

def current_hour():
    """Returns the current hour"""
    return time.localtime().tm_hour

def notify(message):
    """Pops up a libnotify notification and prints"""
    print message
    pynotify.Notification(appname, message).show()

if morning < current_hour() < bedtime:
    print 'Script started too early - quitting'
else:
    pynotify.init(appname)
    notify('You will be locked out in %(grace_period)s minutes' % locals())
    time.sleep((grace_period - snooze_time) * 60)    
   
    while current_hour() >= bedtime or current_hour() < morning:
        status = Popen(['gnome-screensaver-command', '--query'], stdout=PIPE).communicate()[0]
        print status.split('\n')[0]
        if 'inactive' in status:
            notify('You will be locked out in %(snooze_time)s minutes' % locals())
            time.sleep(snooze_time * 60)
            
            notify('Locking screen...')
            time.sleep(4) # short pause so you see the notification that tells you why it's shutting down
            Popen(['gnome-screensaver-command', '--lock'])
        time.sleep(snooze_time * 60)
[/php]It seems to work, but I'll have to use it for a while to find out.  Figuring out how to get cron to run it took almost as long as writing the script itself:

```
40 22 * * 1-5 env DISPLAY=:0.0 /home/endolith/Applications/bedtime.py #JOB_ID_2

```

---

### Post by jnewm on 2010-02-12
Hi Endolith.  I have the exact same problem!  It's ridiculous. So, if you don't mind sharing, how is your solution working?  And, if you don't mind helping, how would I go about borrowing your solution?  I see the PHP Code, but I'm not sure what to do with it.  Do I just save it as a .py file and then stick that single line code (with appropriate user name changes of course) into cron somehow?  Thanks for any help!

---

### Post by Endolith on 2010-02-12
Yes.  See [http://gist.github.com/157847](http://gist.github.com/157847)

---

### Post by jnewm on 2010-02-16
Thank you Endolith.  After some messing around with cron, I got it all working.  Your script is great!

---

