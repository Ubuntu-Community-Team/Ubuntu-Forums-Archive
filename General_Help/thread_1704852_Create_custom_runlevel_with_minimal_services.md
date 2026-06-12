---
title: "Create custom runlevel with minimal services"
date: 2011-03-11
forum: General Help
---

### Post by simon303 on 2011-03-11
Hi,

I am going to have to be running some simulations on my computer as part of my final year project.  They are going to be long (i.e. about a day to run) and so I am looking into ways to speed them up.

One way I am looking at is stopping every non-essential process (i.e. GUI, networking, etc) to leave more CPU free for the simulation.  I could install a minimal system, but I want to choose between whether I am running minimal or full, possibly after boot.  I know it is possible to control what services are running by using runlevels, and think what I want is to create a custom runlevel that only has minimal services running.

So, my questions are:
1) What services are essential, and what aren't
2) How do I change what services a runlevel uses (I have looked at /etc/init and /etc/init.d, but need a little more guidance or another method)
3) How to change the runlevel (either after boot, say with telinit or similar, or during boot)

I would be grateful for any assistance, or possible other ways of giving the simulation "more CPU"

---

### Post by btindie on 2011-03-11
Ubuntu doesn't really use runlevels in the sysvinit sense. Your best bet is to edit the grub commandline just before your system boots. The only advantage you'll get by running it in text only mode is that X and the display manager won't be running. I wouldn't have thought the other services you've got installed would be taking up much CPU time.

Take a look at [this]("http://blog.troyastle.com/2010/06/boot-to-single-user-mode-in-ubuntu-1004.html") then at step 5 when he's on about modifying the kernel args, don't. Just append the word 'single' to the end of the line. If you do
```
grep single /etc/init/*
```you'll see what it does. You can delete the word 'splash' if you don't want the splash screen on startup. You can of course create a new boot entry in grub if you're going to do this alot, but it's quite easy to remember..

If you've got some heavy daemons installed and running such as MySQL, you can manually stop them once the system has started

---

### Post by lithopsian on 2011-03-11
Look in /etc/rc2.d.  That is a list of symlinks that will be executed when you enter runlevel 2, which is the default.

/etc/rc1.d is a list of symlinks that will be executed when you enter single user mode.

/etc/rc0.d is a list of symlinks that will be executed when you shutdown.

/etc/rc6.d is a list of symlinks which will be executed when you initiate a reboot.

/etc/rcS.d is a list of symlinks that will be executed every time you enter any runlevel.

/etc/rc3.d is generally an exact copy of rc2.d but not used.  I suggest you start hacking away at it and tweak your login so you can switch to runlevel 3.  If you completely bork it up then you can just go back to runlevel 2.

Some of these services are tiny tiny daemons that you'll hardly notice, but some can be hefty things and certainly not all are needed by most people.  In Lucid you'll also have to deal with upstart which hides some of the details from you.

---

### Post by simon303 on 2011-03-11
Thanks, I will have a little play with it and see what is left running.

My main concern was things like the system monitor applet and sensors applet, etc that while they only use a small amount it all adds up.  But thinking about it they are tied to the panels and so if X etc aren't running, then neither will they.

I had heard about the "single" mode, but thought I might need more, and while Ubuntu doesn't really use runlevels (2-5 are the same), I thought I could edit one to be what I needed. However if most the extra services are tied into the graphical environment it might be what I need, maybe with a script to shutdown anything else that is causing a problem.

---

### Post by lithopsian on 2011-03-11
Applets will be run (usually as you) by your desktop or windows manager after you boot.  Services are started (usually as root) during the boot process.  Of course either could be unnecessary or essential, but they are started at different times and in different ways.  Examine your autostart shell script to see what it is kicking off once X has started.

---

### Post by simon303 on 2011-03-11
> **lithopsian said:**
> 
/etc/rc3.d is generally an exact copy of rc2.d but not used.  I suggest you start hacking away at it and tweak your login so you can switch to runlevel 3.  If you completely bork it up then you can just go back to runlevel 2.

Some of these services are tiny tiny daemons that you'll hardly notice, but some can be hefty things and certainly not all are needed by most people.  In Lucid you'll also have to deal with upstart which hides some of the details from you.

I have been having a little look at these, but upstart does seem to hide quite a bit of the detail. And as Ubuntu doesn't really support runlevels getting it to boot into a different runlevel (i.e. not 2) is not entirely trivial.

> **lithopsian said:**
> Applets will be run (usually as you) by your desktop or windows manager after you boot.  Services are started (usually as root) during the boot process.  Of course either could be unnecessary or essential, but they are started at different times and in different ways.  Examine your autostart shell script to see what it is kicking off once X has started.

Booting into single user mode has stopped all the applets, but (obviously) not all the services.  What I seem to be settling for is booting into single user mode, then once in it (or perhaps automatically as the last thing it does on startup) running a script to stop all unecessary services (e.g. cups, network-manager)


The biggest problem I am currently having is going through the output of "ps -e" and working out what everything does.

What I am looking for is a system that literally only needs to run one simulation (self writted c++, not using any system processes), possibly with the option of enabling USB support so I can copy the results onto a memory stick and analyse them on another computer while a new simulation is running on the original.

---

