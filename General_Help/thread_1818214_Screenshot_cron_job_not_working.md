---
title: "Screenshot cron job not working"
date: 2011-08-04
forum: General Help
---

### Post by villsen on 2011-08-04
Hi all. I've been searching all over the internet for an aswer to this but can't seem to find anything that works for me.

I want to run a cron job that automaticly takes a screenshot every minute. The script look like this:

```
#!/bin/bash
cd /home/ville/Skrivbord/screenshot
import -display :0 -win root screenshot.jpg
```The code works fine when manually executed but does not work when i run it as a cron job.

The cron file look like this:

```
* * * * * /root/bin/screen.bash &> /dev/null
* * * * * /root/bin/syncdata.bash
```The other task, syncdata works fine as well.

Here are some of the things i've tried without success:


[LIST]
[*]Change permissions on /root/binscreen.bash and /home/ville/Skrivbord/screenshot to 777 and change owner to root.
[*]Change filename to screen.sh (maybe there's no difference between .bash and .sh?)
[*]Change the import line to "import -win root screenshot.jpg" and "import -display :0.0 -win root screenshot.jpg".
[*]Added the code:
```
# Set display to :0 if it's not already set. 
: ${DISPLAY:=:0} 
export DISPLAY
```One time above the existing code in screen.bash and one time below.
[*]Changed the line in cron to "* * * * * export DISPLAY=:0 && /root/bin/screen.bash".
[/LIST]
Nothing works!

Please help me

---

### Post by Beacon11 on 2011-08-04
You're close.

Try this:

```
#!/bin/sh

: ${DISPLAY:=:0}
export DISPLAY

PATH="/home/ville/Skrivbord"

/usr/bin/import -window root "${PATH}/screenshot.jpg"
```

Leave your crontab as * * * * * /root/bin/screen.sh or whatever.

---

### Post by villsen on 2011-08-04
Thanks for the answer! I did exactly as you said but still no luck...  Any more ideas?

---

### Post by Beacon11 on 2011-08-04
Yeah... after I posted that I tried what you had and it still worked for me. Very interesting, I'm sorry. Take a look at /var/log/syslog with ```
tail -f /var/log/syslog
``` and see what cron is doing. Does it give any useful clues?

---

### Post by villsen on 2011-08-04
I was looking for a log but couldn't find one. I'm still very new to linux systems. Here it is:

Aug  4 22:06:01 villesDator CRON[5471]: (CRON) info (No MTA installed, discarding output)
Aug  4 22:07:01 villesDator CRON[5557]: (root) CMD (/root/bin/screen.sh)
Aug  4 22:07:01 villesDator CRON[5558]: (root) CMD (/root/bin/syncdata.bash)
Aug  4 22:07:01 villesDator CRON[5555]: (CRON) error (grandchild #5557 failed with exit status 1)
Aug  4 22:07:01 villesDator CRON[5555]: (CRON) info (No MTA installed, discarding output)
Aug  4 22:08:00 villesDator crontab[5459]: (root) END EDIT (root)
Aug  4 22:08:01 villesDator CRON[5642]: (root) CMD (/root/bin/syncdata.bash)
Aug  4 22:08:01 villesDator CRON[5643]: (root) CMD (/root/bin/screen.sh)
Aug  4 22:08:01 villesDator CRON[5641]: (CRON) error (grandchild #5643 failed with exit status 1)
Aug  4 22:08:01 villesDator CRON[5641]: (CRON) info (No MTA installed, discarding output)
Aug  4 22:09:00 villesDator AptDaemon: INFO: Initializing daemon
Aug  4 22:09:01 villesDator CRON[5757]: (root) CMD (/root/bin/syncdata.bash)
Aug  4 22:09:01 villesDator CRON[5756]: (root) CMD (/root/bin/screen.sh)
Aug  4 22:09:01 villesDator CRON[5755]: (CRON) error (grandchild #5756 failed with exit status 1)
Aug  4 22:09:01 villesDator CRON[5755]: (CRON) info (No MTA installed, discarding output)

---

### Post by Beacon11 on 2011-08-04
Alright then, do me a favor. Since you have no MTA, redirect screen.sh's stderr to a file, i.e. make your crontab line like so:

```
* * * * * /root/bin/screen.sh 2> /home/ville/Skrivbord/output.txt
```

What's in that file after it runs?

---

### Post by villsen on 2011-08-04
Here is the output:

```
import: unable to open X server `:0' @ error/import.c/ImportImageCommand/362.
```

Maybe it has something to do with that display thing after all?

---

### Post by villsen on 2011-08-04
Ok, after looking around a bit i found a tip to create a .xprofile file in /root and put the following line in it:

 
```
[ "$XAUTHORITY" ] && cp -f "$XAUTHORITY" ~/.Xauthority
```

but, no difference...

---

### Post by villsen on 2011-08-05
It has been solved! The problem seemed to be that I ran my crontab under root. When I ran it under user and added the screen.sh it worked fine! wether some of the other things helped as well i don't know...

Thank you so much Beacon11!

---

### Post by Beacon11 on 2011-08-05
> **villsen said:**
> It has been solved! The problem seemed to be that I ran my crontab under root. When I ran it under user and added the screen.sh it worked fine! wether some of the other things helped as well i don't know...

Thank you so much Beacon11!

Ah yes... I should have asked about that, since my testing was being done in my user crontab. Sorry about that!

---

