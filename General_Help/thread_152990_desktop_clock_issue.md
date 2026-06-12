---
title: "desktop clock issue"
date: 2006-03-31
forum: General Help
---

### Post by zapcojake on 2006-03-31
I was running Breezy 64 on my computer and I have went back to 32 bit.  My hard drive is in 3 partitions:/,home,storage.  When I reinstalled 32 bit Breezy I didn't format /home.  Since the reinstall the clock on my desktop runs a little over double time.  I went into my bios and checked the system clock and it is working fine.  I was wondering what to do to fix this.  Thanks--Jake


--I was cruising the howtos and found an amd double clock something or another, My cpu resources with nothing running hover around 2 percent.

---

### Post by RoboJ1M on 2006-03-31
First off, apologies for this being nothing to do with your problem.

When you re-installed Ubuntu, how did you do it without losing all of you stuff on /home?

I also have two partitions, but I'm worried that when I re-install It will put home on / and I'll lose owenership of all my files.

Thanks,

J1M.

---

### Post by frizzl on 2006-03-31
i had a similar issue... not sure if this is your problem but you could try it!

sudo gedit /etc/default/rcS

Change UTC=yes to UTC=no. Then save and exit.

see the thread - [http://www.ubuntuforums.org/showthread.php?t=152605](http://www.ubuntuforums.org/showthread.php?t=152605)

---

### Post by zapcojake on 2006-03-31
In response to J1m's question-- Start the installer as normal, when the partitioner starts up it gives some options one of which is to manually partition.  Select this option.  You need to remember where your stuff is on the disk so you don't format the wrong partition.  mount and format root select your home partition and mount it at /home but select "no, keep exixting data" instead of "yes, format it"  as long as you use the same username as before yor desktop and home will be just as it was before with the exeption of any updates and programs you installed after the initial install.  There is a great howot about how to back up and restore your system in the howto section.  It creates a tarball of root that you can copy back to a fresh install.  If you are a noob the sooner you get familiar with tar the easier life will be.  Good luck.

---

### Post by RoboJ1M on 2006-04-01
Nice one, cheers mate.

I'm glad I know it's possible before I actually go and try it :)

Some of my Solaris and LEAF knowledge translates, kinda..
So I guess I am mostly reduced to n00b...
...oh the shame.

Ta,

J1M.

---

### Post by zapcojake on 2006-04-01
J1m-- didn't mean to imply you were noob, only that fi you were learning tar would be handy, sorry about that.  I gave Solaris a test drive a while back, if you can run that Linux will be a snap.  also, Automatix has a backup program that is graphical and has some good options, just in case.


After more research I have discovered that my problem is the run of the mill amd 64 prob.  The howto Option #1 fixed.

---

### Post by RoboJ1M on 2006-04-02
No worries, my knowledge is so out of date I might as well be a n00b. ;)

Last time I touched linux there was none of this new fangled kernel "modules" ><

Ta,

J1M.

---

