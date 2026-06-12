---
title: "General Disarray Help"
date: 2009-08-30
forum: General Help
---

### Post by djuke04 on 2009-08-30
I love Ubuntu.

With that being said, it gives me grief.  I use it for a media center pc, mainly, and also a laptop (two).  I use them all everyday.  After a couple of weeks, maybe sometimes even a couple months, they start acting up.  Different symptoms on different platforms, never the same.  They slow down.  They restart and forget they have desktop effects.  They don't shut down.  They freeze.  They can't send stuff over the USB and the Network, but they can receive.  It's a wide variety of symptoms, truly bizarre.  I can't find a link between them, and while I can usually find a thread or two about a specific problem I'm experiencing (with hit-or-miss luck on a fix for it) the problems don't disappear, but more appear, more and more quickly, until I have to bail - copy my important files (music, docs, contacts etc) to a USB hard drive (which can be a problem if the USB is acting up...) and re-install everything from the beginning.

Now that I've got thru this cycle on each machine a few times (3-4), I'm trying to think big picture here.  I'm gonna go ahead and blame myself for these problems, but I still wanna know what I'm doing wrong. 

What sort of general maintenance does Ubuntu require? 
Should I always allow system update to run? (Many problems occur right after updates)
Can you think of anything in particular that needs to be done in a certain way to maintain system integrity?
Is there a "system restore" type of feature where you can have Ubuntu check itself for errors or run any self-diagnostics? 

I use these systems regularly, and consistently, each for the same basic tasks (e-mail, photos, music, movies, web-browsing, etc.).  Then suddenly, out of the blue, putting music on the iPod gets unbearably slow.  Video doesn't play, or is glitchy, doing multiple tasks freezes the system, transferring files over a network gets steadily slower until it's crawling along at a few kb/s. All over the course of maybe a couple weeks, the systems get so unreliable and frustrating, I have to erase them and start over.  Re-installing and getting all the features back to how I liked and had them working for a while takes hours and hours, per machine.  

Does anybody else have these problems? How are people dealing with them?

Thanks

---

### Post by Liolikas on 2009-08-30
What sort of general maintenance does Ubuntu require? 
sudo apt-get update
sudo apt-get upgrade
Or in GUI same (all updates install periodically, do not make huge skips like for few weeks).

Should I always allow system update to run? (Many problems occur right after updates)
Yes, but if problems occur you should track them down what update created what problem and post in forums or bugzilla or find solutions. If you do no upade for lets say 3 mounts then go 800 Mb update and 6 problems appear so * and *. But if 2-3 updates cause 1 problem is is not hard to track it down.

Can you think of anything in particular that needs to be done in a certain way to maintain system integrity?
Just do not create mess like using hell know what ways to install things instead of Synaptic (apt-get).

Is there a "system restore" type of feature where you can have Ubuntu check itself for errors or run any self-diagnostics? 
No. Windows system restore also just uses huge file to reinstall things in state it was few days ago and checks for nothing just removes and install things to past state. 

Does anybody else have these problems?
me no but I am Gentoo user not Ubuntu.

---

### Post by jerrrys on 2009-08-30
[size=5]**...8.04 lts...**[/size]

---

### Post by Liolikas on 2009-08-30
> **jerrrys said:**
> [size=5]**...8.04 lts...**[/size]:D It is no support at all instead of long term support? I do not feel good advertising other distribution on Ubuntu forum but if someone sick of so much updates just go Debian stable and stay with Firefox 2.x and have fun.

---

### Post by djuke04 on 2009-08-30
I only use "apt-get" or the Add/Remove Software application.  I let it update and do everything it wants, every time it asks me to.  I know people will say "long term stable" this or that, but the reason I'm on Jaunty is because the other versions stopped working, and upgrading fixed their issues - and brought more of them.  

Right now I'm looking at having to rebuild again, again.  I just want to know how to keep this from happening, again and again.  

At current, I can't use USB really, and also transfers over the network are terribly slow.  Both start out quickly and then gradually decrease to the point where they will never finish.  Any ideas on this?

System Monitor doesn't pretend like it's using much of its resources, and during a transfer, everything will freeze, work for a second, freeze for five, work for one etc etc.  How do I figure out what is causing this?

---

### Post by Liolikas on 2009-08-30
**dmesg** should show what is going on. But is little hard to read for not kernel professional. Maybe just post dmesg here when you encounter something strange?

But basically I was also upset with **apt-get dist-upgrade** command so moved to other distributions (Arch then, but now I am not Arch user). But for sure Arch has its own disadvantages.

---

### Post by jerrrys on 2009-08-30
> **Liolikas said:**
> :D It is no support at all instead of long term support? I do not feel good advertising other distribution on Ubuntu forum but if someone sick of so much updates just go Debian stable and stay with Firefox 2.x and have fun.

it just works ;)

---

### Post by djuke04 on 2009-08-30
So is Firefox a suspect in why there is such unstability in the system? Or is it just that the Debian stable system can't upgrade to 3 or 3.5?

---

### Post by djuke04 on 2010-01-16
Alright, months later I'm back in this thread.  I've had to rebuild three times since I started it.  Ubuntu is simply taking too much time to maintain now.  I REALLY want to support Linux, but it is simply too taxing.  I'm spending ten hours a week+ just trying to fix problems.  I know it's a cliche comparison, but I've never had to do this with Windows - maybe ten hours a year, rounding up.  Right now i'm begging to be convinced not to just put XP back on and stop the fussing.  

It used to be a point of pride that I used Linux and I would try to convert friends, or at least expose, but now I can't even brag about it and I sure as hell can't put it on a friends computer knowing that if they have any experiences like mine for the past year and a half that I'm gonna get a call to come and look at yet another busted Ubuntu installation.

Right in the middle of a movie, after the end of a STUPID long week, it gets freezy and glitchy (like it has many times before) and then stops altogether - the screen goes blank, and it doesn't do anything for twenty minutes.  So I force it off, and then it doesn't think it has a hard drive.  The live session fsck says no errors the first time, but when it still doesn't think it has a hard drive, the second live session fsck says there are tons of filesystem errors.  WTF?! 

Everyone else on here seems to have such a pleasant experience with this software - what am I doing wrong???

---

### Post by gspat on 2010-01-16
This sounds like a hardware problem... either your HDD or the HDD Controller may be going south on you... or it could be a bad cable.


More than likely, switching to windows at this point would give you the same troubles eventually.

---

### Post by djuke04 on 2010-01-16
It's not the HDD itself, because I've tested it and it's fairly new.  I have an SSD for my main drive, with the OS and important files on it, and two other SATA drives as storage.  I'm not sure what it would look like if the hard drive controller was going badly, but I suspected I was getting some strange induction with the solid state drive because everything works when I have the case open and the drive hanging out the side.  Heat is definitely not an issue in this build, and I will replace the cables on GP.  

Thanks for your reply!

---

