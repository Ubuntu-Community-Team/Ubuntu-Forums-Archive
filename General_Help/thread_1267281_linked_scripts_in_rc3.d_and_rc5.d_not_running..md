---
title: "linked scripts in rc3.d and rc5.d not running."
date: 2009-09-15
forum: General Help
---

### Post by awclemen on 2009-09-15
I've set up JBoss on Ubuntu 9.0.4 with a starting script in /etc/init.d/jboss.  When I run /etc/init.d/jboss start or stop, everything works and is fine.  I made two links to /etc/rc3.d and /etc/rc5.d for start up however, when I reboot, jboss does not come up.  What am I doing wrong?  Is something in the wrong place?

link in /etc/rc3.d:
```
lrwxrwxrwx   1 root root    15 2009-09-11 15:00 S21jboss -> ../init.d/jboss

```

link in /etc/rc5.d:
```
lrwxrwxrwx   1 root root    15 2009-09-11 15:00 S21jboss -> ../init.d/jboss

```

jboss script in /etc/init.d:
```
-rwxr-xr-x   1 root root  3393 2009-09-15 08:32 jboss

```

Thanks in advance,
Andy

---

### Post by KeyserSoze93 on 2009-09-15
I was informed recently, and confirmed for myself, that Debian and Ubuntu no longer use runlevel 5.

Instead, only runlevel 1 (single user mode), and runlevel 2 (normal operation) are used.

So, you could try putting you link in rc2.d.

To find out what runlevel you're currently in, run:

runlevel

in the terminal. For me, this outputs "N 2", which surprised me...

---

### Post by awclemen on 2009-09-15
Bravo! Thanks Keyser - it is running the script.  Unfortunately, it doesn't seems to be running it all the way through - are there any logs I can check for errors (there doesn't seem to be anything in /var/log) - or a way to specify a user to run the script - in case it is a permissions issue?

Thanks again,
Andy

---

### Post by awclemen on 2009-09-18
OK, still meddling with this issue.

so I re-applied my startup links with:

```
update-rc.d /etc/init.d/jboss defaults
```

It appears that when I boot and I go to the console during boot (with ALT+F1) that the jboss script will then be run.  If I boot without going to the console, it doesn't run the script.

Anyone have any ideas or know if any way to log what the init system is doing?

Thanks in advance,
Andy

---

### Post by awclemen on 2009-09-18
OK, it looks like I got this working.  Along with this issue, my network config wouldn't bring up an alias (as shown here: [http://ubuntuforums.org/showthread.php?t=1267270](http://ubuntuforums.org/showthread.php?t=1267270)).  It would seem that if jboss comes up, then the alias won't and vice versa. So to make it all work, I did the following... and it ain't pretty

First, try to get the startup and shutdown on the runlevels correct:

```
update-rc.d jboss start 99 2 3 4 5 . stop 20 0 1 6 .
```

Then create my own startup script for Upstart (which is slowly being used for init).  I created the file /etc/event.d/jboss with the following:

```
# jboss
#
# This service starts the jboss application server

description     "service jboss application server"
author          "awclements"

start on startup
stop on shutdown

console output

script
sleep 45
nohup /etc/init.d/jboss start
end script

```

If there is a better way to start/stop the script in Upstart - please feel free to say so here.  I don't know if jboss is shutting down properly, but since the computer is shutting down, it really doesn't matter, does it?

THEN, I add the network restart in my jboss start up script to keep the alias there.  In /etc/init.d/jboss at the beginning of the script:
```

#restart the network because it is a @&#$*(
/etc/init.d/networking restart

```

restart the computer a couple of times and everything seems to come up now.  There is probably some underlying problem that I am missing, but for the life of me, I can't seem to find it.  So this band-aid will work for the moment.  Hopefully this will help somebody else in a similar bind.

credit, where credit is due:

for the Upstart script:
[http://www.pythian.com/news/810/howto-set-up-oracle-asm-on-ubuntu-gutsy-gibbon](http://www.pythian.com/news/810/howto-set-up-oracle-asm-on-ubuntu-gutsy-gibbon)
for Upstart in general:
[http://www.linux.com/archive/feature/125977?theme=print](http://www.linux.com/archive/feature/125977?theme=print)
[http://upstart.ubuntu.com/index.html](http://upstart.ubuntu.com/index.html)

Now, I'm off to the bar.  see ya!

--Andy

---

