---
title: "cron job/gdesklets help"
date: 2006-01-26
forum: General Help
---

### Post by spin2cool on 2006-01-26
Since gdesklets seems to have a pretty bad memory leak, I'd like to have cron kill it and restart it once in a while.  I've having trouble with getting cron to launch gdesklets, though.

Say I wanted to do it at 11 after every hour.  I stick this in my crontab file to kill gdesklets:

```
11 * * * * myusername kill $(pgrep -f gdesklets)
```

and it works great!

The next line is supposed to restart gdesklets, though, and doesn't seem to work:
```
11 * * * * myusername gdesklets
```

I've also tried substituting "gdesklets restart" and "gdesklets shell" and neither works.  If I go to a terminal and type any of these commands in, gdesklets comes up just fine, though.

Any ideas why this isn't working, or how to fix it??

---

### Post by amohanty on 2006-01-26
Crontab's format is like:
1 minute of the hour, 00 to 59
2 hour of the day, 00 to 32 (military time)
3 day of the month, 1 to 31
4 month of the year, 1 to 12
5 day of the week, sun, mon, tue,....
6 actual command to execute

which means you are starting killing and starting your jobs at the 11th minute of every hour. I would suggest that you start gdesklets one minute after the kill op.

so try using this to start your job after killing it:
12 * * * * <cmd>

HTH
AM

---

### Post by three_sixteen on 2006-01-26
[QUOTE=spin2cool]Since gdesklets seems to have a pretty bad memory leak, I'd like to have cron kill it and restart it once in a while.  I've having trouble with getting cron to launch gdesklets, though.

Say I wanted to do it at 11 after every hour.  I stick this in my crontab file to kill gdesklets:

```
11 * * * * myusername kill $(pgrep -f gdesklets)
```

and it works great!

The next line is supposed to restart gdesklets, though, and doesn't seem to work:
```
11 * * * * myusername gdesklets
```

I've also tried substituting "gdesklets restart" and "gdesklets shell" and neither works.  If I go to a terminal and type any of these commands in, gdesklets comes up just fine, though.

Any ideas why this isn't working, or how to fix it??[/QUOTE]

This is a great idea, I never thought to use cron to get around the annoying leakage.

---

### Post by spin2cool on 2006-01-26
[QUOTE=amohanty]so try using this to start your job after killing it:
12 * * * * <cmd>[/QUOTE]

Yeah, I already tried that.  even if I remove the kill statement, close gdesklets, and then set the crontab to just start the process, it doesn't launch.

In fact, it looks like this guy had the same problem:
[http://ubuntuforums.org/showthread.php?t=57238](http://ubuntuforums.org/showthread.php?t=57238)

Any other suggestions?

---

### Post by amohanty on 2006-01-26
Can you replicate the behavior with some other app, like apache?
Also I am assuming you are setting this up in your crontab, am I correct?

AM

---

### Post by Robor on 2006-01-26
I just starting using gdesklets about a week ago.  I didn't know about the memory leak so this is news to me.  

I normally reboot my laptop on work days to take it to/from work but on Monday morning it was frozen.  If there's a memory leak with gdesklets I guess that could explain why that happened as my system usually sits without reboots on the weekends.

---

### Post by spin2cool on 2006-01-26
it doesn't seem to work with any program that requires a display window (gdesklets, gedit, firefox, etc).

Someone on another forum suggested that it might be a problem with proper access (xauth) or setting a display, but I'm having trouble finding information on either of those in the context of this problem.

Here are the contents of my /etc/crontab file, if it helps:

```

SHELL=/bin/bash
PATH=/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games

# m h dom mon dow user	command
17 * * * * root    run-parts --report /etc/cron.hourly
25 6 * * * root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6 * * 7 root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6 1 * * root	test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly
50 * * * * myusername gdesklets
#

```

---

### Post by mettallicat on 2006-01-26
Yes you need to say the paths ... cron works in a diferent tty

---

### Post by spin2cool on 2006-01-26
It doesn't work even if I replace the last line with:

```
50 * * * * myusername /usr/local/bin/gdesklets
```

This leads me to believe that it isn't a path problem.

---

### Post by mettallicat on 2006-01-26
i use this to start and kill azureus 

```

00 03 * * * /home/mettallicat/Scripts/azureus_start
00 09 * * * killall java

```

```

#!/bin/bash
export DISPLAY=:0
export PATH=/usr/local/bin:/usr/local/bin:/usr/bin:/bin:/usr/X11R6/bin:/usr/games:/usr/lib/java/bin:/usr/lib/java/jre/bin:/usr/share/texmf/bin:.
export JAVA_HOME=/usr/lib/java
/home/mettallicat/azureus/azureus >/tmp/error.log 2>&1


#/home/mettallicat/azureus/azureus


```

try that way :D

---

### Post by Game_Ender on 2006-01-26
It is usually much better to call a script than to put the command directly into crontab.  If the script is in your home directory you can also modify it without have to use any sudo/root access which is a good thing.

If gdesklets starts automatically at boot it is a good possbility that it is a service and so it will have an init scrip in init.d.  So you should probably take a look in the /etc/init.d/ directory.  If there is a script called "gdesklets" you should be able to restart by just using the command "/etc/init.d/gdesklets restart".  You can of course try that manually in a terminal first to see if it works.

---

### Post by MasJ on 2006-01-26
Hey, spin2cool.
Thanks for asking this question since I realised through it that I too could use this to kill gdesklets and start it. Gdesklets would REALLY bog down my CPU after a while..

Anyway, my search for a solution was a little fruitful so I'd like to share the spoils with you. In cron, what you NEED to do (to run GUI apps) is to tell it which display to use.

To make things simple, here's my crontab entry:

```

11 * * * * kill $(pgrep -f gdesklets)
12 * * * * export DISPLAY=:0 && /usr/bin/gdesklets

```

Credit for the above information goes to this post:
[http://www.ubuntuforums.org/showpost.php?p=579987&postcount=15](http://www.ubuntuforums.org/showpost.php?p=579987&postcount=15)

---

### Post by amohanty on 2006-01-27
I think cron only provide 4 shell variables:

HOME
LOGNAME
PATH
SHELL

so you might need to provide the display variable, you could:
1. prepend the command with **export DISPLAY=:0 &&**
or
2. try something like: **gdesklet -display :0**

HTH
AM

Edit: gotta learn to read the last comment first. MasJ's solution should work fine.

---

### Post by spin2cool on 2006-01-27
Thanks!  That last suggestion worked perfectly.  I'm not sure of the reasons behind it, but <shrug>   It works!!

---

### Post by amohanty on 2006-01-27
>  I'm not sure of the reasons behind it, but <shrug> It works!!

All graphical applications on X require a server (Xserver daemon) and a client (your nice coloured desktop - well its a bit more complicated but for now that will suffice). X originally was designed so that the server could be anywhere/any machine and you could connect as a client and be provided a display to work with. So if two people login onto the same machine you get two displays one called <hostname>:0 and the other <hostname>:20. The numbering sort of varies but it is in the same vein. 

So then if you have a graphical app, it needs to render its screen onto a display (aka the client - dont ask, the devs of the original X turned the client -server nomenclature on the head - ref: Unix Haters Guide - the X disaster). Typically apps will pick up the display number (:0, :20 etc) form the DISPLAY env variable. 

In this case since cron does not provide that environment variable to its tasks the app convulses and dies. That can be fixed by either exporting the variable  in the command in crontab itself (MasJ's suggestion) or using a scrip file and putting it in there (Game_Ender's suggestion) or using the -display option. However this assumes that you have XSever running, so you will not be able to use any of this on a headless server - is no graphical environment/window manager running.

HTH
AM

---

