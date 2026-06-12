---
title: "Ubuntu 10.04 stopped booting. Where do I start."
date: 2011-11-17
forum: General Help
---

### Post by CoreJohnson on 2011-11-17
Hi.  

I've a trouble with booting my laptop.  I was uninstalling/reinstalling my Virtualbox and DKMS and now I can't get the machine to boot.

I get the Ubuntu startup splash screen for a few seconds then the screen goes black.  Nothing else.  I try to press ESC when starting up but the same thing happens

I've tried finding a sticky or some info but it's like trying to find a needle in a hay stack with this forum.  I't just takes so long.  If someone has a "or the" link to some quick check stuff I would be thankful. 

And yes I can boot to a liveCD.  I can see whe whole file system.   The host  O/S is Ubuntu 10.04


(How do I go back a kernel?)  How do I even get to a local terminal at this point?.  


Thank you much.

---

### Post by carranty on 2011-11-17
Do you mean you were uninstalling the program virtualbox?  I don't see how that could be responsible for your boot issue. I'm not sure what DKMS is, can you please explain (or send me a link to info) a little about it.

Am I right in thinking the grub menu loads (where you select which OS to boot into), but its after this the boot fails.  Have you tried booting to recovery mode?

> (How do I go back a kernel?)  How do I even get to a local terminal at this point?.  

I don't understand, why do you want to go back a kernel?

---

### Post by CoreJohnson on 2011-11-17
> **carranty said:**
> Do you mean you were uninstalling the program virtualbox?  I don't see how that could be responsible for your boot issue. I'm not sure what DKMS is, can you please explain (or send me a link to info) a little about it.

Am I right in thinking the grub menu loads (where you select which OS to boot into), but its after this the boot fails.  Have you tried booting to recovery mode?



I don't understand, why do you want to go back a kernel?


I know.  I thought it was strange also.  The DKMS is Dynamic Kernel Module Support.[http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support](http://en.wikipedia.org/wiki/Dynamic_Kernel_Module_Support)
It's used with virtualbox so when you update to a new kernel, It will automaticly re runs the setup for the virtualbox driver (vboxdrv) so it works again.  (Virtualbox is always an issue after a kernel update :S )

I'm not sure about GRUB loading ok.  It's seem's like it's not or failing perhaps at that stage.  I just can't get  into it or get anything to check.  

How do you boot to recovery mode.  That's what I need.  Is it pressing ESC at start up?  That's not working either.


I was thinking I could go back a kernel when the DKMS module was loaded and working

---

### Post by carranty on 2011-11-17
Thanks for clarifying. So to update to a new kernel have you recently upgraded your Ubuntu distro, or just moved the virtualbox file to a different computer?  I ask because I still don't see how either virtualbox or DKMS can be responsible for this boot issue.

You'll have to use the liveCD to do this but can you post your /boot/grub/grub.cfg file and also your /etc/default/grub file.

Unless you've set the grub timeout to zero, you should always be greeted by a grub screen when booting up that asks you to choose your operating system. If you've Ubuntu installed there'll usually be a corresponding recovery mode, if I remember correctly this gives you access to various grub options.  If you're seeing the Ubuntu splash screen you must be loading grub first.  I guess the timeout has just been set to zero at some point so you don't see it.  I think holding down the shift key after first turning your PC on will show it (the grub menu).

I've had various problems with grub over the years but I've always got at least a grub_rescue> prompt, I've never had just a blank screen so I'm not sure how much help I'll be.

---

### Post by CoreJohnson on 2011-11-17
> **carranty said:**
> Thanks for clarifying. So to update to a new kernel have you recently upgraded your Ubuntu distro, or just moved the virtualbox file to a different computer?  I ask because I still don't see how either virtualbox or DKMS can be responsible for this boot issue.

You'll have to use the liveCD to do this but can you post your /boot/grub/grub.cfg file and also your /etc/default/grub file.

Unless you've set the grub timeout to zero, you should always be greeted by a grub screen when booting up that asks you to choose your operating system. If you've Ubuntu installed there'll usually be a corresponding recovery mode, if I remember correctly this gives you access to various grub options.  If you're seeing the Ubuntu splash screen you must be loading grub first.  I guess the timeout has just been set to zero at some point so you don't see it.  I think holding down the shift key after first turning your PC on will show it (the grub menu).

I've had various problems with grub over the years but I've always got at least a grub_rescue> prompt, I've never had just a blank screen so I'm not sure how much help I'll be.



I edited the grub file,  set the time out from 10 to -1.  The the grub_default=0 to 1.  I rebooted. I got to the gurb recovery screen once.  I selected recovery mode.  I watched everthing go threw until what seemed like the end and it should have loaded the gui.  It did the same black screen.  I tred it again to go to a much older kernel and it wont show the recover screen again.  
I tried it again and it's back to the exact same.  I'll have to post it later.  I don't think it's GRUB not.  I have to stop before this think goes threw the wall.  I might just have to reinstall.  I'm losing to much time trying to fix it.  I need to get some work done.  Fixing computers of all things  lol.
I'll post back later. Thanks

---

### Post by carranty on 2011-11-17
I agree, it doesn't sound like a grub issue.  I've never upgraded my kernel, so not sure what to suggest.  Hopefully someone with more experience will come along with some advice.

EDIT : What made you decide to upgrade your kernel in the first place if you don't mind my asking.

---

### Post by CoreJohnson on 2011-11-18
> **carranty said:**
> I agree, it doesn't sound like a grub issue.  I've never upgraded my kernel, so not sure what to suggest.  Hopefully someone with more experience will come along with some advice.

EDIT : What made you decide to upgrade your kernel in the first place if you don't mind my asking.

There's a possibility my hard drive is failing.  It's just so  coincidental.  I'm duplicating my drive as a backup then am going to  reinstall on a new one.  It was due for a cleaning anyways :).  Thanks  for your help though.  I usually update to the newest kernel when the  updates come out.  

So is there anyone who has wrote a good  artical on things to do when your ubuntu box does not start.  A good  sticky or something?

---

