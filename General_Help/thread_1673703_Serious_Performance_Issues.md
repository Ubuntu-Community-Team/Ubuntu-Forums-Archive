---
title: "Serious Performance Issues"
date: 2011-01-22
forum: General Help
---

### Post by Throne777 on 2011-01-22
I'm running Ubuntu 10.10 x64 with the following setup.
Geforce 6600 GT 128MB
1 gig of RAM
AMD Athlon 64 X2 4200+
Desktop graphics are set on Normal running one of the default themes.
Yeah, it's not a state of the art setup, but it's hardly one step up from a pocket calculator. So why can I not even run two programs at once without my processor hitting 100% use and everything working as if it were one step away from death?
Playing a song on Banshee (I've stripped Banshee down to pretty much bare minimum to avoid hogging resources unnecessarily) whilst browsing the net using Chromium is pushing my computer to the limits. Having a single tab open whilst browsing MetalSucks (for example) and the music keeps cutting out (or repeats a second of the song over and over) whilst it tries to load the page.
Seriously, what the hell?! 
My computer was capable of running Farcry on absolute full spec without any drop of frame rate on Windows XP and now it can't even play a song whilst browsing the web?!
Sometimes my processor will just start running at 100% with nothing in system manager claiming responsibility.
Is my computer cursed or is something (or many things) going significantly wrong?
Or is this just a big issue with the 64 bit version?
I've been running Ubuntu since 5.04 and I've never found the performance so godawful before.

I've taken screenshots of the system monitor so you can see everything that's running on a typical day, if that helps at all.

(I would have posted this in the 64 bit section -assuming it's a 64bit issue, but there's no option to create a thread in that section?)

---

### Post by desnaike on 2011-01-22
[https://help.ubuntu.com/community/32bit_and_64bit#Which%20is%20better?](https://help.ubuntu.com/community/32bit_and_64bit#Which%20is%20better?)

You make the choice.

---

### Post by Spr0k3t on 2011-01-22
I would say something is definitely happening with your computer system.  Does the same thing happen when you are working from a live disc?  What processes are taking over the CPU?  Have you checked the information in dmesg?

If the problem is not related to any one piece of software, 90% of the time it's a hardware related issue.  The hardware issue where the system goes to 100% CPU lock is often tied to bad memory somewhere.  Try using a live disc and run the memtest from the initial boot menu.  If everything passes, grab the hard drive manufacturers software tools and do a 24hour burn/test.  Also, try using a stress test for the video card as well as a heavy number crunching tool to stress the CPU.  I'm almost positive there's a hardware problem if there is no absolute software causing the issue.

Oh yeah, get htop... you will enjoy that more for checking CPU usage.

---

### Post by Brad55 on 2011-01-22
I have a laptop that has 1G ram and a 128mb ATI card with a P4 in it and have not problems running Ubuntu 10.10, and I have all the bells running compiz.

I will tell you that looking at your screen shots you might be able to run faster doing a couple of things.

1. Install Deadbeef music player, here is the link of how to install it. ==> [Deadbeef]("http://www.ubuntugeek.com/deadbeef-ultimate-music-player-for-gnulinux.html")

2. I don't know if you use tomboy or gnome-do if you don't uninstall them or go system/preferences/startup applications and turn them off so they don't start up.

3. If you are not using telepathy-butterfly which belong to Jabber/AIM or some other messenger service than uninstall or turn it off under startup apps if it is there, it's using a lot of ram.

Look in the startup apps and see what you don't need running like I turn off my Bluetooth I don't have any so I don't need it.

---

### Post by Throne777 on 2011-01-24
> **desnaike said:**
> [https://help.ubuntu.com/community/32bit_and_64bit#Which%20is%20better?](https://help.ubuntu.com/community/32bit_and_64bit#Which%20is%20better?)

You make the choice.

I fail to see the relevance of your post. Running 64bit shouldn't (and in my past experience has never) cause huge under performance.

> **Spr0k3t said:**
> I would say something is definitely happening with your computer system.  Does the same thing happen when you are working from a live disc?  What processes are taking over the CPU?  Have you checked the information in dmesg?

If the problem is not related to any one piece of software, 90% of the time it's a hardware related issue.  The hardware issue where the system goes to 100% CPU lock is often tied to bad memory somewhere.  Try using a live disc and run the memtest from the initial boot menu.  If everything passes, grab the hard drive manufacturers software tools and do a 24hour burn/test.  Also, try using a stress test for the video card as well as a heavy number crunching tool to stress the CPU.  I'm almost positive there's a hardware problem if there is no absolute software causing the issue.

Oh yeah, get htop... you will enjoy that more for checking CPU usage.

I've done dmesg, but honestly I've no idea what most of it means and it brings up a lot of information. I can post it in here if you can make heads or tails of it?
I do wonder whether Chromium is eating up my RAM (memory leaking?), maybe by not managing it very well.
I currently have two tabs open one being this page, the other being the homepage for Download Now) and in system processes, Chrome is taking up 9 processes, collectively using 255MB, which seems a tad excessive for what it's doing?

> **Brad55 said:**
> 
I will tell you that looking at your screen shots you might be able to run faster doing a couple of things.

1. Install Deadbeef music player, here is the link of how to install it. ==> [Deadbeef]("http://www.ubuntugeek.com/deadbeef-ultimate-music-player-for-gnulinux.html")

2. I don't know if you use tomboy or gnome-do if you don't uninstall them or go system/preferences/startup applications and turn them off so they don't start up.

3. If you are not using telepathy-butterfly which belong to Jabber/AIM or some other messenger service than uninstall or turn it off under startup apps if it is there, it's using a lot of ram.

Look in the startup apps and see what you don't need running like I turn off my Bluetooth I don't have any so I don't need it.

I have considered getting another music player, but I am rather attached to Banshee. I have noticed every now and again though that it is causing my processor usage to go to 100% for no obvious reason while playing music. I have wondered if it was scanning my collection (it usually has a little icon to show it's doing that and it wasn't there -I've turned off automatic updating just in case it is that).
I've already turned off a load from startup (went back and did some more). 
I use Gnome Do all the time, and I turn off Tomboy when I'm not immediately using it.

---

