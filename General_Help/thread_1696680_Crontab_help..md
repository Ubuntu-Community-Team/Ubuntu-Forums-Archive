---
title: "Crontab help."
date: 2011-02-27
forum: General Help
---

### Post by greg2725d on 2011-02-27
First off i'm fairly new to linux, learning as I go so if I say something that really doesnt make sense please call me out on it. :)

So I want to schedule a few scripts to run every once in a while... I run a small game server, and I post the current map on a website. I would like it to automatically do this every 30 minutes. I have the .sh files already done and i've been using them to manually do this. 

When I edit crontab i've added this line:

*/30 * * * * sh /home/shfiles/start_pixelmap_normal.sh

The file looks like this:

#!/bin/sh
/home/pixelmap/pixelmap -w /home/minecraft/world -f /var/www/maps/pixelmap/normal.png

also made that file executable with chmod. 

This runs perfectly outside of crontab... but I cant seem to get it to run as scheduled or even if I force it to run immediately in crontab. There are many other files like this I want to schedule like this but they all give me the same result. I've searched too many forums with no results... i'm lost. :confused:

---

### Post by cjhabs on 2011-02-27
*/30 should be 0,30

---

### Post by greg2725d on 2011-02-27
I tried the 0,30 and that did not help. I dont think the problem is how its scheduled... for some reason crontab wont run the .sh

---

### Post by rolandrock on 2011-02-27
I don't think you need the 'sh' between the asterisks and the /home in the crontab line.

Make sure you put a new line at the end of the crontab line or it won't be executed.

Have you looked in /var/log/syslog and dmesg for errors?

Post output for:
> crontab -l

---

### Post by gmargo on 2011-02-27
What error did you get from cron?  Check /var/log/syslog.  Check the email that the cron daemon sent you.

---

### Post by greg2725d on 2011-02-27
Ok... so i didnt realize the email thing.  Got into that and this is what it printed to me:


Message 25:
From [email]root@server.digcraft.com[/email]  Mon Feb 28 07:30:01 2011
Date: Mon, 28 Feb 2011 07:30:01 +0300
From: [email]root@server.digcraft.com[/email] (Cron Daemon)
To: [email]root@server.digcraft.com[/email]
Subject: Cron <root@server> sh /home/shfiles/start_pixelmap_normal.sh
Content-Type: text/plain; charset=ANSI_X3.4-1968
X-Cron-Env: <SHELL=/bin/sh>
X-Cron-Env: <HOME=/root>
X-Cron-Env: <PATH=/usr/bin:/bin>
X-Cron-Env: <LOGNAME=root>


Process chunks
Segmentation fault


Now...k the segmentation fault is from the program... its a memory error. I usually only get that if i run out of memory. This machine has 4 gigs and only 1 is reserver for the game. I checked the available memory and there's over 2gigs free. why would i get this error?

I also tried removing the sh and it did not change anything... the program is running...

---

### Post by greg2725d on 2011-02-27
Also this is my crontab -l output

> 

0,30 * * * * /home/shfiles/start_pixelmap_normal.sh # JOB_ID_13



---

### Post by rolandrock on 2011-02-28
That seems to show cron is scheduling the job ok.

If the program runs interactively but segfaults in cron then there is probably a difference in the shell environments.

Try ssh'ing into the machine from elsewhere and run your script from the command line remotely.  If it segfaults then your pixelmap/world programs probably need extra setup like dbus, Xauthority and/or DISPLAY values.

You could try using strace in your script to see where it is going wrong.

---

### Post by greg2725d on 2011-03-01
Thanks for you guys's help... your comments actually made me remember there's a "--no-gui" argument that I can add to the program. I forgot all about that. It works great now :D

---

