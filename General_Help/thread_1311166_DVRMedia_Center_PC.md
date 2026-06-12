---
title: "DVR/Media Center PC"
date: 2009-11-02
forum: General Help
---

### Post by Westernill2 on 2009-11-02
So I just installed ubuntu 9.04 on an older pc that I rebuilt with a new mobo.  Also tried to upgrade to 9.10, which failed miserably, didn't they beta test the crap out of this?  Ideally I would like to have this pc work as a DVR and media center.  I have a tuner card installed in the pc and I downloaded mythtv for it, but now I am lost.  What should I do next?  I am new to the linux world.  Any suggestions?  Please help...I can get my pc specs when I get home if anyone replies to this thread.
 
Thanks.

---

### Post by Uncle Spellbinder on 2009-11-02
I know this will be no help, but just to comment....

I gave up on looking for a true Windows Media Center replacement. So much of what I tried was insanely complicated. Seems there is no media center type app that has a *minimal config to go through like Windows Media Center*.

---

### Post by i.r.id10t on 2009-11-02
Get mythbuntu and be done with it

---

### Post by P4man on 2009-11-02
indeed, [http://www.mythbuntu.org/](http://www.mythbuntu.org/) would be your best bet.

---

### Post by Westernill2 on 2009-11-02
> **P4man said:**
> indeed, [http://www.mythbuntu.org/](http://www.mythbuntu.org/) would be your best bet.
 
 
So is that a distro or a program that I have to install...new to this...Thanks

---

### Post by P4man on 2009-11-02
> **Westernill2 said:**
> So is that a distro or a program that I have to install...new to this...Thanks

its a distro. Its based on ubuntu but comes with everything preinstalled. you can even run it off a cd apparently (the frontend at least). Their website and wiki have elaborate documentation to help you get started. Its a very comprehensive solution, its not exactly a simple or light weight tv recorder app, but it will do anything you could possibly want from a pvr and then some.

---

### Post by seeker5528 on 2009-11-02
> **Westernill2 said:**
> So is that a distro or a program that I have to install...new to this...Thanks

It's a variant of Ubuntu, everything from Mythbutnu is installable on any other variant of Ubuntu.

If you install the mythbuntu-control-center this provides a GUI for installing and configuring things related to MythTV. If you already have a working Ubuntu install and you will be using the computer for more than DVR this is the easiest way rather than go through the hassle of downloading a whole other ISO and doing another installation.

If you want to use the box as a dedicated DVR/media center type thing I would download the Mythbuntu ISO and install again as you get an installation that is a little more streamlined/efficient.

The MythTV in Karmic is a big advancement over the previous MythTV versions, but A: it didn't quite hit it's final release (it was in RC rleeases) in time for Karmic was released and B: there were a lot of database changes so probably a higher risk of something happening during the migration of the database from the old format to the new.

Usually the MythTV guys seem pretty good about getting things tested and working reasonably well before release, so for the MythTV part of the equation using and RC version wouldn't bother me so much, but I have not tried it yet so I don't know how much the MythTV configuration has changed. As for the Ubuntu/Mythbutnu part of the equation, there could be some integration issues between the Mythbuntu stuff and MythTV, lirc, mysql, etc... I usually don't expect any big issues there and there is always a chance that your specific hardware might work better with the older version than it does with the newer version.
 
Later, Seeker

---

