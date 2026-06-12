---
title: "Ubuntu 10.04 fails to start ScreenSaver &amp; lock system) at idle time"
date: 2010-07-20
forum: General Help
---

### Post by TheHemming on 2010-07-20
hello all,

I recently switch my work laptop from Windows XP to Ubuntu 10.04, and it's been relatively seamless.  A co-worker also did the same, and have hit a bit of a snag.

We both have our screensaver set to lock our screen when the system is idle (timeout value doesn't matter).  However, once and a while, the screen saver doesn't activate.

Should the screensaver fail to activate:

1 - the desktop is exposed for employees to view
2 - anyone can actually interact with the desktop for a few seconds before it clicks over to being 
3 - the first password entered is always incorrect (but works correctly the second time).

We are treating this as a security concern.  Manually locking the laptop with Ctrl+Alt+L functions correctly every time, but I want to know that this should work correctly long term in case I forget to manually lock the screen.

Issue #1 & #2 are the biggest problem.  Should the screen fail to lock, anyone can openly view my desktop.  Also, the amount of time from interaction to the OS actually locking itself in response is enough ... say to ctrl+f and send an email to someone (5-10 seconds).

Here are my system specs as of now:

Ubuntu 10.04 32-bit on a Dell Inspiron D630
Intel(R) Core(TM)2 Duo CPU T7250  @ 2.00GHz
MemTotal:        3095296 kB
uname > 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
video drivers > NVIDIA-Linux-x86-256.35.run
wifi > added hardware driver from Canonical
all updates completed up to todays releases.

the Laptop is docked for connectivity to 2 monitors, to which both have integrated USB hubs connecting through the dock.  There are no actual USB devices connected right now.

---

### Post by whyza on 2010-08-10
same problem but a little simpler.

after logging in , idle timer seems to set off screensaver as expected, but after using the desktop for some time, an unknown event seems to cause the idle timer to never kick in ( happens every session ) and as such screensaver does not activate ( I have no password option enabled )

tried restarting gnome-screensaver and it does not help, so its not the screensaver, but the idle timer that seems the issue.

any solutions ?
any further way to diagnose/debug ?

---

### Post by pwyller on 2011-01-10
This is the main reason I moved to Ubuntu - Windows 7 stopped going into idle and running a screen saver. I tried everything under the sun to fix it to no avail. Then, about 1 week ago I installed Ubuntu and life was great -- screensaver worked and no more pixel burn!
 
Until last night... no more screensaver or power down; the machine will not go idle again. the ***only*** thing that I did was plug my Samsung Galaxy S into the USB to charge (first time for this under the new OS)... So, the perhaps it is the Samsung USB drivers causing havoc.
 
Thoughts?

---

### Post by Samatva on 2011-01-14
Curious.... both my home and work 10.04 systems are now failing to invoke the screen saver lock (set to 15 minutes) and I too plug in my Galaxy S (Epic 4g)....

I will do some experiments and report back (may take a few days to get around to it!).

Any ideas?

---

### Post by Samatva on 2011-01-14
Curious.... both my home and work 10.04 systems are now failing to invoke the screen saver lock (set to 15 minutes) and I too plug in my Galaxy S (Epic 4g)....

I will do some experiments and report back (may take a few days to get around to it!).

Any ideas?

---

### Post by Schuby007 on 2011-03-10
I'm encountering something similar with a Dell Optiplex GX280 that I just installed Ubuntu 10.04.1 on. Screensaver and DPMS was working, but the system wouldn't go to sleep. After about a day the screensaver won't even come on anymore. It's very frustrating.

I created a new thread with my problem before I found this thread.

[HTML]http://ubuntuforums.org/showthread.php?t=1704366[/HTML]

 I can see why most businesses are still choosing Windows over *nix. As a  systems admin, it's very difficult to convince clients to go with  Ubuntu when it's into its 10th version and still has problems like this.

---

### Post by Schuby007 on 2011-03-10
UPDATE: after several restarts, the screensaver has come back on. I have no idea why. However I strongly doubt that it will be consistent. This would support the idea that something in the system is interfering with the idle timer.

---

