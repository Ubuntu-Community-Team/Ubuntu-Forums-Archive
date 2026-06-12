---
title: "Ubuntu Server &quot;not meant&quot; to suspend or hibernate?"
date: 2010-09-06
forum: General Help
---

### Post by xDwarf on 2010-09-06
Hello everyone,

after long hours of testing and thinking (and suffering ;) ) I have finally settled for Ubuntu Lucid Server (AMD64) for a home server. Tasks include AFP (Apple) filesharing with Avahi, torrenting, webserver, printserver, backup solution, possibly later Asterisk, etc...
I use ssh to administer the server with the occasional x-forwarding. I do not use a graphical environment such as Gnome.

After hours of searching forums, troubleshooting, etc. I have configured the server to my liking (not quite yet finished). As one of my primary considerations was consuming little power (within the constraints of a standard cost-efficient PC architecture with 4 HDDs) I wanted to be able to suspend and/or hibernate the server when not required. After installing pm-utils (and faking a monitor with the nomodeset and xorg.conf mods), this was possible (I use pm-suspend and pm-hibernate by ssh).

Now I encounter a flurry of issues. When I wake from suspend:

[LIST]
[*]gigabit ethernet no longer works (found a work-around)
[*]CPU power management no longer works (need to enable "conservative" with another work-around)
[*]my CPU, which is untervolted by BIOS and stable at 1.05V, has 1.25V after waking (I have not been able to revert this to 1.05 without a shutdown/new boot - not even reboot will fix it)
[*]hdparm no longer functions, my HDDs which usually spin down nicely thanks to my editing of hdparm.conf, no longer do so after wake from suspend/hibernate
[/LIST]

Now I can spend days trying to find work-arounds for every little thing with scripts in /etc/pm/sleep.d/ but I ask myself the question, am I doing something fundamentaly wrong? Is Ubuntu Server not meant to handle suspend? Are there better or "more correct" ways of using suspend which would prevent these errors? Does everyone who would like to utilise suspend have to go through this?

ACPI is enabled in the BIOS by the way, so is wake-on-lan, which I use to wake the server after sleep.

I am appreciative of any help/comments.


EDIT: Just to clarify, all the issues above ONLY occur after a suspend (or hibernate) and subsequent waking of the server. When I start the server normally (from a full power off), everything works as I want it to.

---

### Post by rtimai on 2010-09-06
xDwarf, I've found that although Ubuntu Forums often provide good advice, it's not the ONLY place to find it. I often get mature and well-written solutions by Google:

[http://blog.dustinkirkland.com/2008/12/ubuntu-server-suspendhibernate-for.html]("http://blog.dustinkirkland.com/2008/12/ubuntu-server-suspendhibernate-for.html")

Oops, I didn't mean the above URL had a solution. However everyone posting there shares your intention, and you may get good leads there.

---

### Post by tgalati4 on 2010-09-06
The desktop version with laptop mode handles hibernate and suspend more robustly.  For home server use, the desktop mode without the gui--just log into the terminal under "sessions" will provide nearly the same performance as the server kernel.

---

### Post by xDwarf on 2010-09-07
Thanks for your responses so far, so I guess it's not just me ;)
The situation does sound rather desolate. Well, I'm sure that will be adressed in the future as home servers are getting more and more power efficient and people are becoming more aware of efficiency (just take a look on how many people write about low-power home servers).
I'll grab what I can get from your articles, else I'll just leave it running 24/7 (yes, I know many say that should be the case for a server anyways but the times are changing!).

*Why not "regular/desktop" Ubuntu?* I tested it and for my server there is just way to much "junk" and I prefer to install what I need rather than trying to find and uninstall everything I don't need. For this application I MUCH preferred the installation procedure and subsequent configuration of Server vs. Desktop. The time wasn't wasted during this test either, as I could apply a lot of the "hacks" I needed to the Server variant (such as Avahi having to start AFTER Netatalk else it will broadcast nothing).

---

### Post by tgalati4 on 2010-09-07
As you have noticed, there really isn't a version of Ubuntu that is optimized for home/low-power/mostly-sleeping servers.  Once you have spent the time getting everything to work and slimmed down the way you want, you can respin your ISO and make a home server Ubuntu version to share.

I agree, starting with the desktop version to slim down with is tedious, but that is the only way that I know of to get all of the proper sleep scripts to function.

I have a Dell PowerEdge server that I use for hacking, but it stays off when I'm not using it.  I have Wake-on-Lan set up so it cold boots remotely whenever I need to use it.  This allows you to use the normal server configuration and you simply shut down when you are finished using it.  I have a delay in my WOL script to allow for the cold boot time before trying to log in remotely.  This is a headless server.

This method is not as convenient or as quick (2 minutes to boot versus 10 seconds to resume) but it certainly is the easiest way to keep a functional server that sleeps most of the time.

---

### Post by xDwarf on 2010-09-07
I've already invested so much time that I will not go back to Ubuntu Desktop unless i find myself with way to much time one day -or week- (unlikely).
Your solution with WOL (via my router with Tomato Firmware) is what I use currently. Since I may be using Asterisk on the server soon I'll have to keep it on all the time anyways (unless I'm on vacation or something for many days/weeks, then I'll shutdown/WOL).
Luckily I thought ahead for this build and bought components for a relatively low-powered system (under 40W for a bog-standard undervolted Sempron 2.7Ghz with 3 of the 4 disks spun down).

But I guess if I have the time and energy, I can try to figure out some more work-arounds for my issues. Most of these simply consist of restarting services or forcing settings after boot. This is not something I want to include in a "custom" ISO as it is quite specific to my hardware and server needs, although of course I am willing to share my approaches!

Oh and by the way: how do I re-initialize hdparm after waking under Lucid (it's not a simple /etc/init.d/hdparm restart anymore)? Does anyone know? I have read several threads with udev and what not but nothing seems to restart hdparm so that it reads my hdparm.conf settings (it reads those settings perfectly when booting normally or rebooting).

---

