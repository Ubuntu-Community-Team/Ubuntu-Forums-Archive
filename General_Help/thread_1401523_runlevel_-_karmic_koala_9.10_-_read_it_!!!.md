---
title: "runlevel - karmic koala 9.10 - read it !!!"
date: 2010-02-08
forum: General Help
---

### Post by rnerwein on 2010-02-08
hi
i have no problem ( not yet any more ).
but i have a question to the development:
--> who had the mangificent idea to change the philosopy of more than 30 year old runlevels ( 0, 1,2,3,4,5,6 ). now when the system is full up who -r and runlevel gives you ==> 2
can anybody imagine how many scripts which are using commands like "who -r", "runlevel"
or parse utmp are give up working. i think a couple of thousends. portability is written in unix with capital letters . please send me a message if you plan to change the runlevel    to "S"
that i can modify my scripts. thank you
ciao:o

---

### Post by Leppie on 2010-02-08
the philosophy of runlevels is still there. the default runlevel is still 2.
for me who -r still reports the correct runlevel:
```
who -r
         run-level 2  2010-02-07 21:53
```
however, the startup process is changing drastically (should be complete with lucid's release). ubuntu is shifting from sysv-rc to upstart, maybe this is where your scripts encounter difficulties? before everything was a sequential process, with ustart several different processes are started during boot to speed up the boot process. so maybe your scripts were being executed at the wrong moment (e.g. too early)?
runlevels can still be used normally, i've set my runlevel 3 to be without x and when i issue telinit 3 x will be killed.

hope this helps.

---

### Post by rnerwein on 2010-02-08
hi
i expected: who -r ====> 5 ( X is up )
ok it's differnt here - but try google: search for "runlevel unix"
mostely you will find explanations like the follwing:
Runlevel 0: Halt System - To shutdown the system
Runlevel 1: Single user mode
Runlevel 2: Basic multi user mode without NFS 
Runlevel 3: Full multi user mode (text based)
Runlevel 4: unused
Runlevel 5: Multi user mode with Graphical User Interface
Runlevel 6: Reboot System

Runlevels 1 and 2 are generally used for debugging purposed only, and are 
not used during normal operations. Most desktop linux distributions boot into 
runlevel 5, which starts up the Graphical Login Prompt. This allows the user 
to use the system with X-Windows server enabled. Most servers boot into 
runlevel 3, which starts the text based login prompt.

Linux runlevels can be changed on the fly using the init tool. If you want to 
switch from text based operations to the Graphical Interface, you just have to 
type in 'telinit 5' in the root prompt. This will bring up the Graphical 
Interface in your system.
thanks for quick reply
ciao

---

### Post by i.r.id10t on 2010-02-08
Debian - which is one of the oldest still existing distros and is what Ubuntu is based on - has always used runlevel 2 for multiuser w/ network mode, and if [XGK]DM is installed it is called from that.

The runlevels you are referencing are what Redhat and others have always used.

---

### Post by Leppie on 2010-02-08
> **i.r.id10t said:**
> Debian - which is one of the oldest still existing distros and is what Ubuntu is based on - has always used runlevel 2 for multiuser w/ network mode, and if [XGK]DM is installed it is called from that.
+1, just look into tools like "apt" and "alien", these are typical Debian packages.

if you want the default runlevel to be 5, you can set it like that in your /etc/init/rc-sysinit.conf. if you  do edit this, you will have to check all other upstart scripts as well though...

---

### Post by john newbuntu on 2010-02-08
The runlevels you have described is typical of most *nix systems.  But because runlevels do not deal well with hardware dependencies and is not flexible, Debian and its variations have switched to upstart(or some such thing), which is an event based init daemon.

Instead of starting and stopping jobs/tasks when runlevel changes, upstart makes changes automagically when an event changes, for example when a new hardware is added or when a new event is emitted by a job etc.  You do not need to do a telinit or manually indicate that something changed.  This is why in Karmic, runlevels 2 through 5 are pretty much the same. 0,1 and 6 are the same as it was in System V.  In karmic, the runlevel concept is still maintained as Leppie mentioned but might get replaced fully at some point.
In general, newer scripts need to move off of checking runlevels and check other things like status of upstart jobs or event statuses, although I am not sure on recommendations by the designers.

---

### Post by rnerwein on 2010-02-08
hi
ok i am giving up - 
it's the first time i saw a system in runlevel 2 runing X, now i now i noticed it.
25 years unix - time changed. 
by the side here my systems ( debian never used other linux systems since 1994)
root@solaris:~> who -r              ( solaris 10 )
         run-level 3  Feb  8 15:02                   last=2

root@suse:~> who -r                 ( suse 11 )
         run-level 5  Feb  8 15:31                   last=S
Mon Feb  8 15:44:03 CET 2010

root@gaileg:~> who -r               ( suse 9 )
         Runlevel 5   Feb  8 07:47                   last=2

root@ubuntu:~/tmp 16:55-> who -r    ( karmic koala 9.10 )
         Runlevel 2   2010-02-08 16:50

i'll mark this thread solved
ciao

---

### Post by Leppie on 2010-02-08
you only need to get used to this Debian runlevel thing... but it's not hard to get used to (i was a bit confused as well after Slackware).

---

### Post by blackbelt_jones on 2010-08-26
Okay, so how do I get into text mode from a Lucid Live CD?  Nevermind, I should start a new thread.

---

