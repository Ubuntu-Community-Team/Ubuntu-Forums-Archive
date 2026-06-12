---
title: "No MouseUp until mouse is moved"
date: 2009-12-09
forum: General Help
---

### Post by kazbear on 2009-12-09
Since upgrading to 9.10, I see this problem more times than not.  MouseUp is not recognized until I move the cursor.

Any ideas?

Thanks

Dell Lat D600
Complete reformat and install of 9.10

---

### Post by mihamil on 2009-12-10
I have noticed this too.  I was surprised to not see as much talk about it in the forums.

When I click on some buttons it's like it doesn't completely register until I move the mouse off the button, then it executes whatever it was supposed to do.  

I am also using a D600.  Maybe it's related to Hardware or driver.

---

### Post by aurisel on 2009-12-13
I'm having this problem as well, and I have a Dell Latitude D600 as well.

If anyone scoffs at this problem, I stress that it's a lot more obnoxious than you might think!  Basically, almost every other time that I click on something, I have to move the mouse via the touch pad for the click to fully register.  I also noticed these details:

[LIST=1]
[*]Opening a menu, and then moving the mouse via the touch pad, will sometimes automatically close the menu.
[*]In a situation where the click has only half-registered (e.g.; clicking on a button shows it clearly depressed), I tried moving the track point instead of the touch pad to see if it would exhibit the same situation, and it did not.[LIST][*]Moving the pointer off of a button will remove the "depressed" state from the button, as if I was holding the primary mouse button.[*]Moving the pointer back over the button re-shows the "depressed" state.[*]Moving the pointer with the touch pad is the only way to fully register the click.[/LIST][*]Using the track point exclusively will show the same symptoms.[*]Sometimes, I'll even open a terminal and start to type something, and the typing won't register until I move the mouse with the touch pad.
[/LIST]

I've tried messing around in the BIOS, but with no luck.  Ubuntu 8.10 works fine, so I'm not sure of what the problem is.  There are a few quirks in 8.10; the touchpad has very slow tracking no matter what, but it doesn't exhibit this "no mouse click up" problem.  I've tried creating a new xorg.conf, but no luck there so far.  I'm going to keep trying different drivers in there, to see if that makes a difference.

This problem is so obnoxious.  It's like the computer freezing any time you click on something, even though the computer is not.  It's like having a broken mouse, when your mouse isn't broken.  I could possibly stick with Intrepid, but, I've installed Karmic on other PCs and I like it!

---

### Post by Mr Jolly on 2009-12-30
I'm receiving the same issue on the same hardware, Dell Latitude D600. Like the aurisel said in the previous post, it's well annoying.

---

### Post by aurisel on 2009-12-30
It looks like the Dell Latitude D600, although working great with Karmic in every other way (I love suspend on lid close!), has at least this one glaring issue.  I've been dealing with it for the past two weeks, but, I notice it every day!  I'm not going to give up trying to get things working, and I have this thread bookmarked and subscribed, so as soon as I solve the problem, I'll post here.

Since my last post, comparing xorg.conf files between Intrepid and Karmic--and trying lots of different options/drivers in Karmic--yielded no insight.

kazbear, mihamil, and Mr Jolly, I will check back periodically to see if you've found anything.  We'll figure this out!

---

### Post by praetorivs on 2010-01-02
I receive a similar issue with certain programs:  most notably anything Flash, also Eclipse & derivatives.  The problem was introduced when upgrading from 9.04.

Currently running Ubuntu 9.10 x86_64 on Lenovo Thinkpad T61.

---

### Post by bugloopy on 2010-01-03
I too have a D600 and this exact same problem. I hope someone solves it soon. It is beyond annoying.

---

### Post by EdVedder on 2010-01-13
Buuump.

It's beyond annoying. My Mafia Wars regimen is suffering. My energy is around 3500. I have to hit "Do this job again" a million times a day, and having to wiggle the cursor after each click is killing me. All three of my text-based friendships are in shambles. I actually ..... spoke... to people the other day to avoid having to click-wiggle. If this glitch doesn't get fixed, I may be forced to venture outside of my house for food eventually. I understand you probably think going through this is a healthy thing for me, but I just want my life back.

Nobody has solved this yet? Or do I use this as an excuse to get rid of my pos D600? How can it only affect one kind of computer like this?

---

### Post by bugloopy on 2010-01-13
This solution works for me!
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/444674/comments/24](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/444674/comments/24)

[Timo Jyrinki]("https://launchpad.net/%7Etimo-jyrinki")             wrote             on 2010-01-12:                                                             [ #24]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/444674/comments/24")                                                        A workaround of putting a line "options psmouse proto=exps" in /etc/modprobe.d/psmouse.conf seems to work for me.
Therefore the bug is in the psmouse kernel driver detection code? Or that it's "correctly" detected but the resulting protocol has a bug compared to what the hw actually uses.

---

### Post by aurisel on 2010-01-13
bugloopy!  :KS

I just created that configuration file, unloaded the mouse module and reloaded it, and I could tell right away that the mouse felt more like it did in Intrepid (i.e.; where the mouse did not exhibit this "no mouseup until moved" problem).  Sure enough, it seems good so far, with the only downside being that touch-pad scrolling doesn't work.  I can certainly live with that.  :)

Thank you for the heads-up, bugloopy!

---

### Post by mihamil on 2010-01-14
Seems to work for me as well.

Thanks bugloopy.

---

### Post by unixsamurai on 2010-02-19
Fantastic. I've been fighting this since I upgraded to 9.10 a couple days ago. Kudos to you, my good fellows, kudos!

---

### Post by dead-end on 2010-03-25
Thanks bugloopy.
Fixed dell c840  noclicks and scroll from hell were driving me nuts in Karmic.

For the newbies like me try this:
psmouse.conf did not exist (/etc/modprobe.d/psmouse.conf )
open terminal
gksu gedit /etc/modprobe.d/psmouse.conf   
add line     options psmouse proto=exps      
save and reboot

---

### Post by antonioperez on 2010-10-05
I'm just having the same problem with ubuntu 10.04 and same dell notebook.
I'll try the workaround. Thanks bugloopy.

---

### Post by Bill_MI on 2010-10-17
My Dell C840 had this problem.  I found proto=imps (instead of proto=exps) does cure the problem in /etc/modprobe.d/psmouse.conf.  Either works and I can find little on the difference.

But this changes the whole touchpad system into a simple mouse emulator and removes any ability to configure with a GSynaptics (or whatever that new one is called).  The relationships between Xorg synaptics driver, psmouse, psmouse.conf, xorg.conf and these configuration utilities is clear as mud.

Can we have buttons that work and a configurable touchpad, too?

Any insight welcomed.  TIA

---

