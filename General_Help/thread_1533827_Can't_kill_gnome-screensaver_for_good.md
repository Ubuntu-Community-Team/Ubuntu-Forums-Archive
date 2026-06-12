---
title: "Can't kill gnome-screensaver for good"
date: 2010-07-18
forum: General Help
---

### Post by narnie on 2010-07-18
Hello,

I have a very simple little script that kills the gnome-screensaver. This script has worked on ubuntu < 10.04 for some time, but breaks on UNE 10.04.

It will kill the screensaver process, but it mysteriously gets restarted. I have /apps/gnome-power-manager/lock/use_screensaver_settings set in gconf-edit to False (unchecked), btw.

Here is my code:

```
#! /bin/bash
#
#TODO develop this
#delete screensaver
#ps uxf|grep -v grep|grep -A 1 "/bin/bash /home/woodnt/bin/ssd"|sed -n '2p'|awk '{print $2}'|xargs kill
STIME="60m"
#STAMP="`date +"%d%y%H%M%S"`"
USAGE () {
echoWhere "
=========================================\n
USAGE:\n\n
ssoff [-k|t|h|p]\n\n
-p	prompt for time
-k	keep screensaver off without a timeout
-t	time to keep off [default is 60m] no suffix is time in seconds
-h	help
"
exit
}
TIME=${1:-4h}
(
pkill screens
sleep $TIME
gnome-screensaver &
zenity --info --title "Screensaver restarted" --text "The screensaver has been restarted" --timeout 600 &
zenity --question --title "Screensaver lock" --text "The screensaver will lock in 5 seconds unless you press cancel" --timeout 5
if [ $? = 5 ] ; then
	gnome-screensaver-command --lock
fi
) &

zenity --info --title "Screensaver killed" --text "Screensaver process killed and will be restarted in $TIME" --timeout 5
exit
```

It is off for a while, but is restarted by /sbin/init as can be seen

```
$ ps -ef|grep /bin/gnome-scr
woodnt    3673     1  0 11:26 ?        00:00:00 /usr/bin/gnome-screensaver

$ ps -ef|grep /sbin/init
root         1     0  0 Jul16 ?        00:00:00 /sbin/init
```

Any idea why /sbin/init is continuing to restart gnome-screensaver and how to stop this behaviour?

With thanks,
Narnie

---

### Post by lkjoel on 2010-07-18
> **narnie said:**
> Hello,

I have a very simple little script that kills the gnome-screensaver. This script has worked on ubuntu < 10.04 for some time, but breaks on UNE 10.04.

It will kill the screensaver process, but it mysteriously gets restarted. I have /apps/gnome-power-manager/lock/use_screensaver_settings set in gconf-edit to False (unchecked), btw.

Here is my code:

```
#! /bin/bash
#
#TODO develop this
#delete screensaver
#ps uxf|grep -v grep|grep -A 1 "/bin/bash /home/woodnt/bin/ssd"|sed -n '2p'|awk '{print $2}'|xargs kill
STIME="60m"
#STAMP="`date +"%d%y%H%M%S"`"
USAGE () {
echoWhere "
=========================================\n
USAGE:\n\n
ssoff [-k|t|h|p]\n\n
-p    prompt for time
-k    keep screensaver off without a timeout
-t    time to keep off [default is 60m] no suffix is time in seconds
-h    help
"
exit
}
TIME=${1:-4h}
(
pkill screens
sleep $TIME
gnome-screensaver &
zenity --info --title "Screensaver restarted" --text "The screensaver has been restarted" --timeout 600 &
zenity --question --title "Screensaver lock" --text "The screensaver will lock in 5 seconds unless you press cancel" --timeout 5
if [ $? = 5 ] ; then
    gnome-screensaver-command --lock
fi
) &

zenity --info --title "Screensaver killed" --text "Screensaver process killed and will be restarted in $TIME" --timeout 5
exit
```It is off for a while, but is restarted by /sbin/init as can be seen

```
$ ps -ef|grep /bin/gnome-scr
woodnt    3673     1  0 11:26 ?        00:00:00 /usr/bin/gnome-screensaver

$ ps -ef|grep /sbin/init
root         1     0  0 Jul16 ?        00:00:00 /sbin/init
```Any idea why /sbin/init is continuing to restart gnome-screensaver and how to stop this behaviour?

With thanks,
Narnie
Can't you just do:
```
killall gnome-screensaver
sudo killall gnome-screensaver
```

---

### Post by narnie on 2010-07-18
> **lkjoel said:**
> Can't you just do:
```
killall gnome-screensaver
sudo killall gnome-screensaver
```

Yes, but this is just quick and dirty code and want to restart it later (my code for just disabling rather than killing is much more complex to keep track of pid's of the sleep so that it can be re-enabled earlier if desired and I'll refactor this later time permitting).

The problem I didn't make clear, is that /sbin/init will restart it on it's own even after it has been killed. How long it takes this I'm not sure, but it is within 30 mins of killing it.

It is as if /sbin/init thinks a user's gnome-screensaver is a "must run" and will restart it if it is closed without my wanting it to. Haven't seen this behavior in previous Ubuntu's (not sure if it is UNE specific).

With thanks,
Narnie:D

---

### Post by lkjoel on 2010-07-18
You could try:
```
(
while true
do
killgnome.sh
done
) &
```
That will keep it always running, but I am not sure that you would want to run this!

---

### Post by narnie on 2010-07-18
> **lkjoel said:**
> You could try:
```
(
while true
do
killgnome.sh
done
) &
```
That will keep it always running, but I am not sure that you would want to run this!

Right. I'd rather not have a process running like that, but I had considered it.

I'd rather see why it is running in the first place.

Plus, if it ever did get to run and lock, then I've defeated one of my original purposes, to prevent locking. Perhaps, I'll just modify /apps/gnome-screensaver/lock_enabled to False from the command line which should do what I want in this situation.

Truth be told, it is somewhat irritating that it is forcing it to run like that. It should not take that control away from us. We should be in charge of the screensaver, not /sbin/init.

Cheerio,
Narnie

---

### Post by lkjoel on 2010-07-18
> **narnie said:**
> Truth be told, it is somewhat irritating that it is forcing it to run like that. It should not take that control away from us. We should be in charge of the screensaver, not /sbin/init.
Yes, I would agree with you on that.

---

