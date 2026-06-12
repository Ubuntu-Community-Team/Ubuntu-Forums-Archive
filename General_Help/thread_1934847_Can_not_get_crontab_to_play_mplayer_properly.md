---
title: "Can not get crontab to play mplayer properly"
date: 2012-03-03
forum: General Help
---

### Post by andyklaj1985 on 2012-03-03
Hey Guys

I am trying to get mplayer to work in crontab but am having trouble

I am using the following line in crontab (playing every mintue just to test).
* * * * * /usr/bin/mplayer -playlist /home/andy/Desktop/MyMusic/Morning.m3u  

What happens is at the beginning of every minute only the first second of the song plays.

I have tested the line in the terminal and there does not seem to be a problem 

Any ideas?

Kind regards

Andrew

---

### Post by andyklaj1985 on 2012-03-03
Figured it out 

had to redirect output > /dev/null 2>&1

(cant completely remember what this means)

Kind regards

Andrew

---

### Post by efflandt on 2012-03-03
That redirects standard error to standard out, and standard out to nowhere (/dev/nul).  Without that it would likely tell you something like "broken pipe", since cron has minimal environment and would have no clue where to display anything.  If you want to see what it actually says, redirect it to a file, instead of to /dev/null (like **>> /home/andy/cron-log.txt 2>&1** if you want to append to some log file instead of overwrite it).

---

