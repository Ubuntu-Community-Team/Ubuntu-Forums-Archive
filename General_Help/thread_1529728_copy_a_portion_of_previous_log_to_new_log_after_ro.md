---
title: "copy a portion of previous log to new log after rotate"
date: 2010-07-12
forum: General Help
---

### Post by beatdawookie on 2010-07-12
Ok, here is the situation.  
 
I have installed fail2ban and it is working great.  It is monitoring the auth.log and it's own log.  Now here is my question...
 
Every week, my log files rotate, which is just fine for the most part.  But this also rotates the fail2ban log and removes any chance of catching a repeated IP from Sunday to Monday.  Is it possible to copy a portion of the previous log to the new log?
 
Here is my scenario of what I would like to accomplish, but I am a novice here so please be specific..  
 
logrotate does its job as expected...  then a script writes a portion of the previous log to the new log then appends a word/number after that portion (we call this log.1)...
 
next time the log rotates (creating log.2), I want to take the portion of log.1 after the word/number and append it to log.2 along with another word/number
 
process repeats...
 
This will always ensure there is at least 1 week backlog in the logs for fail2ban to track.  I don't want to just change the frequency of the log-roll because it doesn't solve the issue of tracking across the log roll....
 
any help would be great...

---

### Post by bodhi.zazen on 2010-07-12
First I would be surprised if fail2ban does not do this automatically (look through the old logs and/or track ip addresses), but I do not know for sure.

Second, I would ignore any cracking attempt that shows up in the logs as failed log in attempts once a week or less. With anything remotely resembling a strong password it would take thousands of years to crack you PW.

Edit: The official documentation indicated fail2ban is aware of log rotation, although I did not review the specifics, there is a discussion here :

[http://forums.debian.net/viewtopic.php?f=5&t=26281](http://forums.debian.net/viewtopic.php?f=5&t=26281)

---

### Post by CannibalZerg on 2010-07-13
You can parse both current log and rotated logs (*.1.gz *.2.gz and so on) with "zcat -f" command:
```

zcat -f /var/log/logname.log* | grep sometext

```

---

### Post by beatdawookie on 2010-07-13
I have tried to get an explanation of "handles log rotatation" but have yet to find one.  Seems by looking at my logs when the log rotates, fail2ban restarts and erases all bans from the Iptables...  if the data from the previous week was added to the log, then the ban would be recreated...
 
Cannibal, 
 
I don't want to just find "sometext", I would like to find all the text after "sometext"...  the trick is, the search has to begin at the end of the file and move back till it finds the "sometext" then copy the data from the "sometext" thru the EOF to the new log...
 
any help would be appreciated.

---

### Post by bodhi.zazen on 2010-07-13
> **beatdawookie said:**
> any help would be appreciated.

I suggest you post on the fail2ban mailing list asking for an explanation.

---

### Post by beatdawookie on 2010-07-13
I have posted to their list.  Still waiting for an answer...  I will post here if I hear anything.

---

### Post by beatdawookie on 2010-07-13
would adding this to the logrotate config file work
 
```

 
postrotate
     grep -A1000 "Jail 'ssh' started" /var/log/fail2ban.log.1 | grep "WARNING" > /var/log/fail2ban.log
 

```

---

### Post by beatdawookie on 2010-07-14
bump

---

### Post by bodhi.zazen on 2010-07-14
> **beatdawookie said:**
> bump

You should be able to answer the question for yourself. Test the grep in a terminal and examine the output.

Follow what happens when the logs rotate.

What was the answer on the mailing list ?

---

### Post by beatdawookie on 2010-07-14
the grep statement works, I am just not familiar enough with the logrotate config/setup to ensure that this will do what I am hoping...
 
i.e. will putting this in the log rotate config make this the first thing to show up in the log...  that is really what I need to confirm...

---

