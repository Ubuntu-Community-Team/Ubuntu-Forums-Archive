---
title: "drastic solution?"
date: 2006-04-23
forum: General Help
---

### Post by BruschiOnTap on 2006-04-23
About 10 years ago my family bought a Gateway Destination PC.  This was the model that came with a 32 inch monitor and TV software so that the family TV could double as a computer.  Cool idea, right?  Well, the PC is a 133 mHz with a 586 processor and a motherboard too weak for Win98 and it (barely) predates USB.  It's still running the Win95 that came with it.

Now it's having problems, even though we only use it as a TV and no longer as a PC.  The PC part is clearly on the fritz, only loading in Windows Safe Mode which doesn't load drivers for the TV program.  We could reinstall Windows, but then we'd have to get Intel Smart TV, which I think would be a big hassle considering it's a decade old and Gateway has clearly moved away from things like the Destination.

My question is:  would it be worth installing ubuntu and getting the TV tuner program to see if it would work?  Would this computer even be able to run Ubuntu?  I'm pretty new to this OS but I think it might be able to save us from springing for a new television set...  One problem I can see having right off the bat is that it only has a dial-up modem and we use highspeed internet on our normal computers so we will have to find a way to get software updates and other needs for this dinosaur.  Any thoughts?

---

### Post by IYY on 2006-04-23
I doubt this can run Ubuntu, but you could try Damn Small Linux. It's a live CD, so you don't really have anything to lose.

---

### Post by BruschiOnTap on 2006-04-23
sweet!  I like this live CD idea!  but I still need to get a copy of this TV software on there... I'm sure it doesn't come with damn small linux?

have you got a link where I can d/l the live CD?

---

### Post by Sef on 2006-04-23
> have you got a link where I can d/l the live CD?

[have you got a link where I can d/l the live CD?]("have you got a link where I can d/l the live CD?")

Also you could do a server install and download fluxbox as your window manager.  It is the same one that dsl uses.

[http://doc.gwos.org/index.php/FluxboxSource]("http://doc.gwos.org/index.php/FluxboxSource")

---

### Post by IYY on 2006-04-23
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

I think this is the direct link:

[http://distro.ibiblio.org/pub/linux/distributions/damnsmall/current/dsl-2.3.iso](http://distro.ibiblio.org/pub/linux/distributions/damnsmall/current/dsl-2.3.iso)

---

### Post by dmizer on 2006-04-23
what kind of hardware do you have running the tv?  if you do a server install of ubuntu, and load fluxbox, or icewm for your windows manager, then you will have access to the ubuntu repositories for apt-get.

there is likely to be some ubuntu software to run your tv configuration.  let us know what you have.

here's another link that might be interesting to you ... [http://www.ubuntuforums.org/showthread.php?t=98233&highlight=ubuntu+mini](http://www.ubuntuforums.org/showthread.php?t=98233&highlight=ubuntu+mini)

---

### Post by FLeiXiuS on 2006-04-24
The best part of DSL is that you can custom create an image on the fly with whatever software packages you want.  So once you completely install everything you need, save it as an image where you can burn it later on and boot it up directly.  Problems solved?  Google should have instructions for custom creating DSL loads.

---

### Post by BruschiOnTap on 2006-04-24
Ok, that was a whole bunch of information to sift through... :-k let me try to make sense of some of it, I need things explained to me like I'm a 4-year-old:

-damnsmalllinux has no GUI, which I schmuck like me will need.  and I can fix that by getting IceWM (?)  I'm unclear on what Fluxbox is, exactly...
My next question would be: how do I load software onto the computer while running a live CD?  This computer is no longer capable of accessing the internet, so everything I do will involve compiling a program somewhere else and then loading it from a CD.  Because it will only run in Windows safe mode, it also can't/won't access a network.

I'm having a hard time finding more exact specs for the Gateway Destination, Google searches only bring up people who are discussing its massive monitor.  I've been looking everywhere for its original documentation but so far nothing's turned up.

Thanks for all your help so far!

-BOT-

---

### Post by dmizer on 2006-04-25
just because you can't go online in windows doesn't mean you won't be able to go online for ubuntu.  try a live cd like knoppix or ubuntu live and i suspect you will be surprised.

i suspect that your windows will only run in safe mode because the os has either been infected beyond repair, or something else has damaged the operating system.  especially since you're still running win 98 on it.

remember ... just because windows can't make it go online doesn't mean another os can't.

here's a good website with alot of hardware information on your system:
[http://dead-zone.nanovox.com/destivu-software.html](http://dead-zone.nanovox.com/destivu-software.html)

your box looks like it's going to be a bear to get working in linux.  not impossible, but it looks to me like a video and audio nightmare.

also note, if you still have the OEM dial up modem, it's just plugged in an ISA or PCI slot.  you can remove it and put in an ethernet adapter instead.

---

### Post by BruschiOnTap on 2006-05-03
Haven't had time to get started messing with this but I got some help from someone who knows windows pretty well.  He gave me a couple of suggestions.  If th ey don't work I'm going to try your suggestion, dmizer, and see if the modem will work with ubuntu.  oh, and the os is even older than 98, it's the original version of win95

---

### Post by dmizer on 2006-05-14
[QUOTE=BruschiOnTap]If they don't work I'm going to try your suggestion, dmizer, and see if the modem will work with ubuntu.  oh, and the os is even older than 98, it's the original version of win95[/QUOTE]
i would be terrified of going online with win95.  i believe the site i linked to has drivers for windows 98se ... that would be much better than win95.

if you're running win95 still, that would explain alot of your problems ... lol.

---

