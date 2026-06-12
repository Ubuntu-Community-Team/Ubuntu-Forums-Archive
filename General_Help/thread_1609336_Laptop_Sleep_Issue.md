---
title: "Laptop Sleep Issue"
date: 2010-10-30
forum: General Help
---

### Post by RaviPatel on 2010-10-30
I know there has been a few threads about this topic already, and even a few bug reports, but I've been following them all and nothing seems to work. I also think my problem is slightly different to other similar ones.

I'm using Ubuntu 10.04  and basically - my laptop hangs when waking up from suspend of hibernate. It just shows a black screen for ages, and I have to hard power off. 

The slightly odd thing though, is that I used be dual booting with Windows 7 and when I was, the suspend and hibernate features with Ubuntu worked fine. I recently wiped my laptop and installed Ubuntu as the sole OS, and only then did the suspend issues start.

Maybe this could help solving the problem? I'm not sure, but any help or advice at all would be greatly appreciated.

Thanks.

---

### Post by RaviPatel on 2010-10-30
Anyone, please? Any advice at all would be massively appreciated.

---

### Post by RaviPatel on 2010-10-31
Anyone? Sorry to keep bumping this, but I really want this feature to work.

---

### Post by RaviPatel on 2010-10-31
Okay so I think I've found a fix - but got one slight problem with it. Hopefully it's quite simple for some to figure out.

Here is the solution:

[http://ubuntuforums.org/showthread.php?t=1371844](http://ubuntuforums.org/showthread.php?t=1371844)

However, when I try to install the xserver-xorg-video-radeon_6.12.1-0ubuntu2_amd64.deb packages, it gives me the following error. 

(see attached image)

I have uninstalled the old version of xserver-xorg-video-radeon that was installed. I can't figure out what it means.

Anyone got any clues?

---

### Post by RaviPatel on 2010-10-31
Please? Someone? Anyone? Really desperate to fix this.

---

### Post by RaviPatel on 2010-11-01
Sorry to bump again, but does anyone have any ideas at all. Pleeeease?

---

### Post by Z06Gal on 2010-11-01
Mine did not work till I realized powermanagement-interface was not installed.  I installed it via synaptic and it works great.  Maybe it is something this simple.  :)

---

### Post by maxsideburn on 2010-11-01
I guess I'm one of the few laptop users who just doesn't see a need for "sleep" mode.

My laptop seldom leaves the charger for more than 30 minutes, and if I really need to save power I just shut it down and restart it later. Ubuntu boots fast nowadays, about as fast as mine recovers from "Hibernation" under Windows.

---

### Post by RaviPatel on 2010-11-01
Thanks alot for the reply. I didn't have that package installed actually, so I've installed it now. I've not had chance to test it fully yet (usually my laptop went to sleep okay, and if I wanted to wake it within like an hour, it would be fine - it's for periods longer than that where it has problems, so I will test it properly overnight I guess) but I will report back when I have. 

Thanks! Hopefully that will work.

And yeah, I guess it's not that big a feature really, it's just I'm in the habit of suspending now, so I'd rather just have it working. Hope it works anyway. Will let you know.

---

### Post by Z06Gal on 2010-11-01
> **RaviPatel said:**
> Thanks alot for the reply. I didn't have that package installed actually, so I've installed it now. I've not had chance to test it fully yet (usually my laptop went to sleep okay, and if I wanted to wake it within like an hour, it would be fine - it's for periods longer than that where it has problems, so I will test it properly overnight I guess) but I will report back when I have. 

Thanks! Hopefully that will work.

And yeah, I guess it's not that big a feature really, it's just I'm in the habit of suspending now, so I'd rather just have it working. Hope it works anyway. Will let you know.


If you go to system - preferences - power management you can click on that and set it up however you want to.  :)

---

### Post by RaviPatel on 2010-11-01
Okay so I just tested it for a decent amount of time, and it did the same thing - blank screen on waking up. Gutted. I've configured it the correct way using the power management thing, but that's not seemed to work.

Does anyone have any ideas at all regarding the dpkg error that I'm geting when trying to downgrade my video drivers. I think if I can do that it will solve my problem.

---

### Post by SaintDanBert on 2010-11-01
You might need to dig deep into the bits to discover which of the several power manager, suspend, acpi, etc parts are installed. You might have several and they might get in each other's way. I don't know why this happens, but it happened to me. Things better after cleanup.

Also, before you try to suspend-to-ram (sleep) or suspend-to-disk (hibernate) make sure that you un-mount, un-dock, and remove anything that is not part of your native laptop. If this works, add them back one-by-one to discover which gives the failing grief. I had this problem, too.

Bonne chance,
~~~ 0;-Dan

---

### Post by RaviPatel on 2010-11-03
> **SaintDanBert said:**
> You might need to dig deep into the bits to discover which of the several power manager, suspend, acpi, etc parts are installed. 

Thanks for the reply, mate. How would I go about doing this exactly. Which packages are needed/obsolete/get in another ones way.

---

### Post by SaintDanBert on 2010-11-03
(grin) (blush) When if find out, I'll post something here... (heavy sigh)

Make sure that you have a swap partition -- not file, [highlight]partition[/highlight]. Make sure that your swap partition has a base size that will store 100% of your physical ram [highlight]PLUS[/highlight] a little extra (lagnaippe) should any active swap space be in use at the time of suspend processing. Using 0.5 GB lagnaippe would likely be enough. *NOTE -- A 32-bit install will use 3GB ram but stumble with 4GB ram. (4GB is 2**32 bytes while 32-bits enables 2**32-1 bytes.) You need the PAE extension package with 4GB installed with a 32-bit release. Very little traditional swap space use is likely with 3 or 4GB ram. That does not mean zero use is always the case. *

Seriously, I have two "identical" laptops. While I did nothing extraordinary during the install or in follow-up, the low level acpi and power management (and udev and udisk and upstart) are different between the two.

Let me offer the following links as a place to start digging. 
(Standard warnings apply.)  Suspend and resume are **kernel** topics.

[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)
--and--
[https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume)

The literature uses the term "suspend" and "hibernate".
The former is **suspend-to-ram**. I say, SLEEP.
The latter is **suspend-to-disk**.  I say, HIBERNATE.
The literature uses the term "resume" regardless of which "suspend" happened.

----------
Standard Warning #1 -- When in a hole, step #1 says "stop digging."
(ugh) I know its bad, but I couldn't resist.

Cordially,
~~~ 0;-Dan

PLEASE post links or details that you discover to this thread. Others are struggling (blush) too and we can help everyone.

---

### Post by RaviPatel on 2010-11-04
Thanks alot, mate. I will give it a read and hopefully it will sort my problem.

---

