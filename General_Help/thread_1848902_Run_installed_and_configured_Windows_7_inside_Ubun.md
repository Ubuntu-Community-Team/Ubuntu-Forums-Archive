---
title: "Run installed and configured Windows 7 inside Ubuntu"
date: 2011-09-23
forum: General Help
---

### Post by EiEiOO on 2011-09-23
Ubuntu 11.04 For Windows)
Windows 7 (64 bit)

Hi All,
I would like to run my currently installed and configured Windows 7 os from within Ubuntu. I know I can install a new instance of Windows using VirtualBox but I want to make my current Windows system with applications and data available form Ubuntu

The end result I want will be running Ubuntu but launching Windows with already installed applications and settings as needed (from within Ubuntu)

TIA
EiEiOO

---

### Post by Slim Odds on 2011-09-23
You can try... but the Virtual Machine will NOT appear as the same hardware as the real hardware.

At least the following will be different: display adapter, network card, memory size.

---

### Post by seawolf167 on 2011-09-23
So... clone your Windows partition with [Clonezilla]("http://www.clonezilla.org"), then restore it to the VBox you have setup. [Here ]("http://jlorenzen.blogspot.com/2010/07/restoring-clonezilla-image-using.html")is a little blog post on it - its pretty easy, I've had to do it a couple times to get files off old images for computers I no longer have/need/use.

---

### Post by haqking on 2011-09-23
> **seawolf167 said:**
> So... clone your Windows partition with [Clonezilla]("http://www.clonezilla.org"), then restore it to the VBox you have setup. [Here ]("http://jlorenzen.blogspot.com/2010/07/restoring-clonezilla-image-using.html")is a little blog post on it - its pretty easy, I've had to do it a couple times to get files off old images for computers I no longer have/need/use.

+1 i do it all the time.

However data changes wont reflect of course, so good idea to place data on an external drive or partition accessible from both

---

### Post by SecretCode on 2011-09-23
See this thread, on this forum: [Boot an existing XP (Physical HD) install with VirtualBox - Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=769883)

And [virtualbox.org &#8226; View topic - HOWTO: Windows 7: In both VM and native -- VBox3.x](http://forums.virtualbox.org/viewtopic.php?f=28&t=33356) at [http://forums.virtualbox.org/](http://forums.virtualbox.org/).

eta: As noted below, be very aware of the issues of reactivation that you may face.

---

### Post by Mark Phelps on 2011-09-23
If what I read in the past about doing this is still correct, this about one of the WORST ways to run Win7 possible!

Why?

Because when running Win7 in the VB, the "hardware" is different -- requiring it to be reactivated.

Then, if you go back to running it natively, guess what -- the "hardware" is different (again) -- requiring it to be reactivated -- again!

What the testers said was that every time they switched from VB to Native, they had to reactivate Win7.

And, as you can probably guess, to guard against "piracy", MS has already established a policy that several activations inside a short period will PERMANENTLY deactivate your copy of Win7.

So, if you want to bork up your Win7 so it won't work anymore, go ahead and do this.

---

### Post by haqking on 2011-09-23
> **Mark Phelps said:**
> If what I read in the past about doing this is still correct, this about one of the WORST ways to run Win7 possible!

Why?

Because when running Win7 in the VB, the "hardware" is different -- requiring it to be reactivated.

Then, if you go back to running it natively, guess what -- the "hardware" is different (again) -- requiring it to be reactivated -- again!

What the testers said was that every time they switched from VB to Native, they had to reactivate Win7.

And, as you can probably guess, to guard against "piracy", MS has already established a policy that several activations inside a short period will PERMANENTLY deactivate your copy of Win7.

So, if you want to bork up your Win7 so it won't work anymore, go ahead and do this.

+1

Agree.

If you really want a copy of your build in a VM then clone it and back into a VM, which may require activation again in the VM, but at least its the once.

Have data on external shared drive, but the OS itself will be independent of the other

---

