---
title: "gnome-terminal logging"
date: 2011-09-23
forum: General Help
---

### Post by jungleb on 2011-09-23
Hi guys, I want to save all term output to a monthly log file and then gzip it when new month arrives.

I'm using gnome-terminal and I'm playing with script utility (I found a script from Rafa&#322; B&#322;aszczyk (rblaszczyk) on launchpad), but I'm not being able to make it work ... below you'll find what I got so far ... it would be very helpful if someone could give me a hand on this ...

```

#!/bin/sh
#gnome-terminal log
logdir=/home/user/terminal-logs
month=`date "+%m-%y"`
logfile=$logdir/$mes.something.log
echo $logfile
if [ $logfile = "$logdir/$(date +%m-%y).something.log" ]; then
script -f -q $logfile
tsocks ssh usr@server
fi 
gzip -q $logdir/*.log
script -f -q $logfile
tsocks ssh usr@server

```

Thanks for the help&time!

---

