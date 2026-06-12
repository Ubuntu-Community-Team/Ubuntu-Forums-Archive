---
title: "removing mail from command line?"
date: 2006-03-05
forum: General Help
---

### Post by hcker2000 on 2006-03-05
Alright I need to know how to clear all mail out of my local mail inbox. I don't need to read it just to clear it.

---

### Post by schilcha on 2006-03-05
Here's the brute-force approach:

Have a look at the directory /var/mail/. There should be a file that's named just like your username. All your emails are in there, one after the other. It's a plain-text file, so you can open it in your favourite editor and remove the mails you don't like. You can even remove all lines, so no mail's left.

Good Luck!

---

### Post by dcstar on 2006-03-05
Or if you do ever want to manage it (in a convenient way, including root e-mails):

[http://ubuntuforums.org/showthread.php?t=136509](http://ubuntuforums.org/showthread.php?t=136509)

---

### Post by hcker2000 on 2006-03-05
Thanks if any one can tell me how to stop cron from sending me mail that would also help.

---

### Post by schilcha on 2006-03-06
```
man 5 crontab
```
> 
       If MAILTO is defined but empty (MAILTO=""), no
       mail will be sent.  Otherwise mail is sent to the owner of the crontab.

       [...]

       EXAMPLE CRON FILE
       # use /bin/sh to run commands, no matter what /etc/passwd says
       SHELL=/bin/sh
       # mail any output to ‘paul’, no matter whose crontab this is
       MAILTO=paul
       #
       # run five minutes after midnight, every day
       5 0 * * *       $HOME/bin/daily.job >> $HOME/tmp/out 2>&1
       # run at 2:15pm on the first of every month -- output mailed to paul
       15 14 1 * *     $HOME/bin/monthly
       # run at 10 pm on weekdays, annoy Joe
       0 22 * * 1-5    mail -s "It’s 10pm" joe%Joe,%%Where are your kids?%
       23 0-23/2 * * * echo "run 23 minutes after midn, 2am, 4am ..., everyday"
       5 4 * * sun     echo "run at 5 after 4 every sunday"


So, make MAILTO empty in your crontab.

---

### Post by hcker2000 on 2006-04-03
Thanks just made the addition to the file and will see if it works.

---

