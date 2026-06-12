---
title: "Shell scripting and Cron - Newb Problems"
date: 2010-09-25
forum: General Help
---

### Post by jrowland on 2010-09-25
I'm new to this game, so I thought I'd play around a bit with trying to kick off a shell script with crontab.  I've spent the last couple of days teaching myself shell scripts and cron, mostly through UbuntuForums searches and Google.

My script itself works if I execute it from a command line.  And I can see in my syslog that the cron job is kicking off.  But, I don't see the desired results, which should be a popup window with "Hello World".

I'm in my user profile at /home/jimmy

I wrote a quick script using [COLOR=Blue]$ nano helloworld.sh[/COLOR]```
zenity --info --text "Hello World"
```gave it a [COLOR=Blue]chmod 777 /home/jimmy/helloworld.sh[/COLOR]

Threw it into my crontab with[COLOR=Blue] $ crontab -e[/COLOR]```
*/1 * * * *   /home/jimmy/helloworld.sh
```When that didn't work, I added the same text to the [COLOR=Blue]sudo crontab -e[/COLOR], with the same results (or, rather, lack of results).

If I go into the GUI Gnome Schedule 2.1.1, I see the job listed.  If I highlight the job, and click on the "Run Selected Task" icon, the "Hello World" popup... well, pops up.  All is good.

Any ideas on why this doesn't work "normally"?

---

### Post by john newbuntu on 2010-09-25
Normally an X server serves multiple screens.  You need to indicate where to display your new window when run from other areas like cron.  So, throw in a line like:
export DISPLAY=:0.0
just before your zenity statement in your shell script and you are good to go.

---

### Post by jrowland on 2010-09-25
Hunh... yep, that worked. thanks. Seems I've still got some more learning to do.  So, does the 0.0 mean "apply to all screens"?

---

### Post by john newbuntu on 2010-09-25
If I am right, the .0 is a display number referring to a specific screen on your TCP connection.

---

### Post by jrowland on 2010-09-25
So, in the spirit of forum non-etiquette,  I'll ask a second question now that my first one has been answered. (I did mark the thread as solved, though) :^)

So I wanted to play with some commands that only root could do, so I did a [COLOR=Blue]sudo crontab -e[/COLOR] and added a quick 1 liner: ```
* * * * *   ifconfig eth0 down
```Again, I can see in the syslog that the command was executed, but the eth0 is always up.  (I'm on wireless, so I don't care about eth0)

Any ideas why this wouldn't work?

---

### Post by john newbuntu on 2010-09-25
Try with full path "/sbin/ifconfig" and see if it works.

---

### Post by jrowland on 2010-09-25
Sure enough.  I can tell I've got some teeth cutting left to do.  Thanks for your time.  This is fun. :^)

---

