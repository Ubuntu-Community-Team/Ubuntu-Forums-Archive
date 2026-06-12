---
title: "Natty crashes frequently"
date: 2011-05-09
forum: General Help
---

### Post by gregalynch on 2011-05-09
I just upgraded to Natty on a (almost brand new) HP pavilion dm4t.  I'm finding that it crashes pretty frequently, in a variety of ways that might or might not be related.

1) Sometimes (every 2-3 days) it will just blink out and go back to the login screen.  This usually happens within a minute or so of logging in.  If I log in again after this, it will usually crash again.  A restart of the system typically will make the problem go away for at least a few sessions.

2) If I leave the computer on for a while, the screensaver will freeze and nothing can get me back to the desktop.  Processes seem to still be running behind it (I left some music playing once and the music continued to play, but the screen was black and I couldn't get back to my desktop - I had to do a hard shutdown)

3) A perhaps unrelated problem, every ten sessions or so when I log in the indicator applet will be gone and an error telling me that indicator applet failed to load (or something to this effect)

Btw I'm using ubuntu classic rather than unity (just because I like it better).  I haven't used Unity enough to know whether these problems also occur with it.

---

### Post by mattgraham1234 on 2011-06-06
i confirm this problem.

---

### Post by linuxinstalledfromhdd on 2011-06-06
I confirm this as well

---

### Post by drvista on 2011-06-14
i confirm

---

### Post by pd1108 on 2011-06-14
I too confirm the problem.  There is no set pattern in the crash.  I am using a HP Core Duo processor, 4GB RAM, Nvidia graphics and two hard disks (160 and 250)

The other problem frequently faced is that it loses its wireless connection if machine is idle for a while

---

### Post by marl30 on 2011-06-14
Hmmm. I was having some of these issues in Kubuntu 11.04 right after I upgraded to Linux kernel 2.6.39. I ran Kubuntu for a while before and never use to have any of those issues, so I thought it was kernel related. I replaced it with Ubuntu, and so far so good. 

I haven't enabled the backport and the experimental repos though, as I did it two days ago and updates gave me some weird issues that caused me to reinstall.

---

### Post by dsx724 on 2011-06-25
I have munin monitoring server uptime and Natty crashes every 3 days like clockwork between 9PM and 10PM EST.  June 14th, June 17th, June 20th, June 23 and it's going to crash on June 26.  This is a really glaring problem.

System configuration is as follows:
Core i3-2100
H67 Motherboard
Dual ATSC Tuner
RAID 10 MDADM

It does a minireboot and returns to the login page.  Some services aren't started.

---

### Post by notwoz on 2011-10-30
> **dsx724 said:**
> I have munin monitoring server uptime and Natty crashes every 3 days like clockwork between 9PM and 10PM EST.  June 14th, June 17th, June 20th, June 23 and it's going to crash on June 26.  This is a really glaring problem.

System configuration is as follows:
Core i3-2100
H67 Motherboard
Dual ATSC Tuner
RAID 10 MDADM

It does a minireboot and returns to the login page.  Some services aren't started.

I realize that this thread has been inactive for a while. Has anyone come up with a solution?

In my case, I end up with a login page, even though my installation is configured to login automatically. Thus, it would seem that the system does not do a normal reboot.

You don't say anthing about your graphics hardware. To me it seems that the graphics driver is a very plausible suspect!  (I have a ATI Radeon HD 3450 and the driver is AMD's FGLRX.)

---

### Post by Frau_Munitz on 2011-10-31
I've been having this problem every two days (if im lucky) recently it was today when I lost some dcument i was working on for my class. 

Because of this Im considering going back to 10.04 or even changing distro. Is there a distro that any of you recommend? One that is pretty stable and doesnt have all the bugs of Natty?

---

### Post by notwoz on 2011-10-31
> **Frau_Munitz said:**
> I've been having this problem every two days (if im lucky) recently it was today when I lost some dcument i was working on for my class. 

Because of this Im considering going back to 10.04 or even changing distro. Is there a distro that any of you recommend? One that is pretty stable and doesnt have all the bugs of Natty?

I have tried changing the desktop from Unity to Gnome. So far I have not had any more crashes, but it's less than 24 hours since I changed.

---

### Post by Frau_Munitz on 2011-10-31
> **notwoz said:**
> I have tried changing the desktop from Unity to Gnome. So far I have not had any more crashes, but it's less than 24 hours since I changed.

How can i change to gnome?

---

### Post by gregalynch on 2011-10-31
When I had Natty I tried using Gnome (ubuntu classic), but I still had the crashing problems.  I'd suggest you upgrade to Oneiric; I haven't had the problem anymore since doing that.

---

### Post by Qboy61 on 2011-10-31
I was using Natty and now I'm using Oneiric.  My Unity session crashes (mostly when watching video) and leaves me at the login prompt as many people here have indicated.  If I uninstall the Hardware Graphics Driver for my Nvidia 3800M graphics in my HP8740W I no longer crash out of unity.  Though some video seems a little stuttery without a graphics driver.

---

### Post by Voluntarist on 2011-10-31
> **gregalynch said:**
> 
2) If I leave the computer on for a while, the screensaver will freeze and nothing can get me back to the desktop.  Processes seem to still be running behind it (I left some music playing once and the music continued to play, but the screen was black and I couldn't get back to my desktop - I had to do a hard shutdown)


I have had a similar problem on my desktop computer. Whenever I leave it for a while, and it goes to screensaver, when I come back and wake it up I'm stuck with a blank white screen and a mouse.

I also have been getting white screens when I maximize stuff.

It kind of pisses me off that that Ubuntu has taken a few steps back in terms of stability. I used to never have problems on my two computers with Ubuntu which weren't caused by user screw ups, now it's so frequent it's annoying.

---

### Post by linuxaddix on 2011-11-01
ubuntu 11.04 is my personal favorite and have never had any real problems with it.i never do the upgrade way cause there is always conflicts of repositories.try doing a fresh install.and see what happens.

---

### Post by Frau_Munitz on 2011-11-05
I tried rolling back to 10.04 but for some reason the computer wont recognize the usb installer... I really like 11.10 but the freezing, sudden crashes and return to the login menu and rendering my touchpad useless doesnt cut it for me...

---

### Post by linuxaddix on 2011-11-06
ive found that the girst time you log in to 11.10 follow it by an immediate logout.and of course log back in.everything runs smoother after doing so.i dont know why though

---

