---
title: "Suspend, worked yesterday, not today?"
date: 2010-05-26
forum: General Help
---

### Post by keypox on 2010-05-26
Not sure if an updated caused it?  Dont think so.  

But on my desktop p35 ds3l motherboard suspend worked great.  Today it no longer works.  Harddrives spin down, but fans stay on, monitor goes blank but stays on.   Computer wont come out of this state. 

Anyway to diagnose what the problem is?  Sleep logs or something? Thanks, suspend is a top priority for me :(.

---

### Post by stonhaus on 2010-05-26
I am receiving the same behavior. I have a thinkpad T500 with intel graphics. Suspend had been working flawlessly in 10.04. I know that I applied updates, but nothing special. 

When I try to suspend. The Screen goes black and the suspend light just flashes. It went on for about an hour the other day without ever fully suspending.

I am not sure which logs to take a look at. The pm-suspend log has some entries in there, but nothing seems recent.

---

### Post by joeyjoejo on 2010-05-27
Hi both,

I've got almost exactly the same problem. I've opened a bug report some time ago (I've had this problem since installing Lucid).

Everything worked fine in the last release. Suspend is one of the most important things for me - because I use it all the time - and I think a lot of other people feel the same way. The need to periodically do hard-resets has actually corrupted some data on the drive, and I can't even boot the latest kernel... I really can't understand why no one takes this seriously...


see bug report:
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/575924](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/575924)

---

### Post by keypox on 2010-05-27
i dont understand what happen to make sleep stop working. I have tried just from a fresh install without updating same thing.  

Tried 64bit and 32 bit. When i get some time today, I will search for how to find the logs of sleep events.  IF there is any. 

Oops sleep = suspend

I might even try mint :( blahh

---

### Post by stonhaus on 2010-05-28
Alright, I got sleep and resume back.

I installed the Ubuntu-X PPA ([https://launchpad.net/~ubuntu-x-swat/+archive/x-update]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")s)

From the Console:
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo aptitude update
sudo aptitude upgrade
```

---

