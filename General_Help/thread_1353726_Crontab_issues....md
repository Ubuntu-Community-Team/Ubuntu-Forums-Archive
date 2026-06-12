---
title: "Crontab issues..."
date: 2009-12-13
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2009-12-13
For a few months now I've been using the command ```
gmplayer mms://live.cumulusstreaming.com/KCMO-AM
``` to listen my favorite radio show. Because the powers that be hate me I can no longer stay up long enough to start the command. Not a problem considering we have cron right? That's what I thought anyway. So... I read through mplayer's man page and cam up with ```
mplayer mms://live.cumulusstreaming.com/KCMO-AM -ao pcm:file=/home/sin/coast2coast.asf -vc dummy -vo null
``` which works without a hitch when I run it so I loaded it into crontab just to find nothing there the next day. So I set cron to launch my command 5 min later and mplayer shows up in system monitor but does nothing. Just sits there. I retested the command in the terminal and it started recording as I wanted it to. I think the powers that be really do hate me. I've looked all over Google and the forums but only see explanations for non-working commands. This one works when I run it... I'm confused.

crontab -l: 
```
# m h  dom mon dow   command
50 0 * * *      rm -rf ~/Coast2Coast/*
58 0 * * * 	mplayer mms://live.cumulusstreaming.com/KCMO-AM -ao pcm:file=/home/sin/Coast2Coast/coast2coast.asf -vc dummy -vo null
* 5 * * * 	killall mplayer
```

tail /var/log/syslog from testing tonight:
```
Dec 13 04:04:28 Purgitory crontab[20821]: (sin) REPLACE (sin)
Dec 13 04:04:28 Purgitory crontab[20821]: (sin) END EDIT (sin)
Dec 13 04:04:34 Purgitory lircd-0.8.6[1214]: removed client
Dec 13 04:04:43 Purgitory lircd-0.8.6[1214]: accepted new client on /var/run/lirc/lircd
Dec 13 04:05:01 Purgitory cron[1687]: (sin) RELOAD (crontabs/sin)
Dec 13 04:05:04 Purgitory lircd-0.8.6[1214]: removed client
Dec 13 04:06:01 Purgitory wpa_supplicant[1475]: CTRL-EVENT-SCAN-RESULTS 
Dec 13 04:06:01 Purgitory CRON[20860]: (sin) CMD (mplayer mms://live.cumulusstreaming.com/KCMO-AM -ao pcm:file=/home/sin/coast2coast.asf -vc dummy -vo null)
Dec 13 04:06:01 Purgitory lircd-0.8.6[1214]: accepted new client on /var/run/lirc/lircd
Dec 13 04:06:01 Purgitory postfix/sendmail[20862]: fatal: open /etc/postfix/main.cf: No such file or directory
```

So I'm stumped... Help??

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
I may start crying soon. I've missed 3 episodes...

---

### Post by Wardje on 2009-12-13
A quick google shows [this]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2006-January/057656.html"), though I'm unsure how relevant that is considering the date.
Are any log files and such supposed to be created? (and are they appearing)

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
I specified the output folder and it's not in root. The log is listed in my OP. Thanks for the reply.

---

### Post by john newbuntu on 2009-12-13
Can you type the command in a shell script (or any script for that matter) redirecting stdout and stderr to a file.  Then just run the script in cron.
So your cron would be like:
58 0 * * * /home/<myuserid>/runit.sh

and the template of /home/<myuserid>/runit.sh would be like:

#!/bin/sh
{
/usr/sbin/mplayer mms://live.cumulusstreaming.com/KCMO-AM -ao pcm:file=/home/sin/Coast2Coast/coast2coast.asf -vc dummy -vo null
} >>  /home/<myuserid>/runit.log 2>&1
exit 0

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
I had to manipulate the script but that worked for some reason. Guess scripts for crontab commands with flags then? A little confused still but ah well... it works. Thanks.

---

