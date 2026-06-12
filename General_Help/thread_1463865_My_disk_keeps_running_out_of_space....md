---
title: "My disk keeps running out of space..."
date: 2010-04-27
forum: General Help
---

### Post by PerfectReign on 2010-04-27
A few days ago, I got a message that stated I had zero bytes of disk space left.

Odd, I thought, but I had been doing video transcribing and thought that may be the issue.

I moved a video (4 GB) off the hard drive to an external drive and then went about my business.


This morning, I got the message again.  I enclosed a screen shot.  I moved a few more items off my hard drive - but then was soon out of space again. (Less than an hour later.)

I logged in as root and poked around.  I noticed that /var/archives had almost 60 GB of data in .tar.gz files.

I moved them off to an external drive and am okay for now.

What are those??

[IMG]http://www.perfectreign.com/stuff/2010/ScreenShot498.png[/IMG]



[IMG]http://www.perfectreign.com/stuff/2010/ScreenShot499.png[/IMG]

---

### Post by limey_rick on 2010-04-27
Do you have any automated backup running? It looks like these are being created daily. 

Go into a terminal and type crontab -l and see if it has anything in - post if it does. Also, post sudo crontab -l as well. I don't know if there is a different crontab for root. This would show if there is any background job schedule to back up your files.

---

### Post by psusi on 2010-04-27
It looks like you are trying to download all packages that exist and run your own personal archive.

---

### Post by PerfectReign on 2010-04-27
As for crontab, here's what I have - nada
[FONT=System][COLOR=Blue]
[SIZE=3][COLOR=Navy]kai@kai-laptop:~$ crontab -l
no crontab for kai
kai@kai-laptop:~$ sudo crontab -l
[sudo] password for kai: 
no crontab for roo[/COLOR][/SIZE][/COLOR][/FONT][SIZE=3][COLOR=Navy]t[/COLOR][/SIZE]


Downloading packages? How would I do that?

---

### Post by dannyboy79 on 2010-04-27
> **limey_rick said:**
> Do you have any automated backup running? It looks like these are being created daily. 

Go into a terminal and type crontab -l and see if it has anything in - post if it does. Also, post sudo crontab -l as well. I don't know if there is a different crontab for root. This would show if there is any background job schedule to back up your files.

+1 
this looks spot on as to what is occurring. i would say that you have a backup of /home/ and /etc/ being created by some program. luckbackup, sbackup, or any of the other automated backup solutions. 

look in your /etc/cron* folders (example: cron.daily, cron.hourly etc etc) to see what is all in there. i am guessing it's in cron.daily because it appears to be creating it once a day

---

