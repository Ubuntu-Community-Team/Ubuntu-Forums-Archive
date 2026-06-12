---
title: "app startup at boot"
date: 2009-12-07
forum: General Help
---

### Post by linuxcss on 2009-12-07
using Ubuntu 9.10 - karmic

I have an app that monitors a battery backup UPS, originally written for RedHat.

I was able to get it to installed on karmic and working but when I reboot
a few utils including a daemon need to be manually restarted.

The Redhat script was adding to the /etc/inittab   3 programs to be
called at system startup time. Apparently ubuntu does NOT use /etc/inittab.

What do I need to do to have those programs invoked at ubuntu 9.10 startup time??

the three lines are:

dp::wait:/etc/pndown/powersrv
du::wait:/etc/pndown/upsagentd
di::wait:/etc/pndown/upsis  ....


thanks

---

### Post by linuxcss on 2009-12-18
anyone have an answer to the above?

---

### Post by amsterdamharu on 2009-12-18
According to this page:
[http://www.netadmintools.com/html/5inittab.man.html](http://www.netadmintools.com/html/5inittab.man.html)
 *id*:*runlevels*:*action*:*process* 
all your lines are missing runlevel field
dp::wait:/etc/pndown/powersrv
I found a script on my 8.04 that looks for inittab called (locate inittab): 
 /usr/lib/upstart/migrate-inittab.pl
That script looks for inittab and then tries to convert it but the script will fail due to the missing runlevel field
I don't know why it's missing a runlevel because this page doesn't specify what a missing runlevel means (unless you forgot to paste the lines that are above the lines you provided):
[http://www.netadmintools.com/html/5inittab.man.html](http://www.netadmintools.com/html/5inittab.man.html)
You can check out this page and decide when your app needs to run:
[http://en.wikipedia.org/wiki/Runlevel#Typical_Linux_runlevels](http://en.wikipedia.org/wiki/Runlevel#Typical_Linux_runlevels)
I guess runlevel 0 and 6 should not be added since they are halt (shut down) and reboot so then the process should be stoped (or killed if it doesn't want to stop)

Now you can create the inittab yourself and see if the script runs and processes your inittab.

---

