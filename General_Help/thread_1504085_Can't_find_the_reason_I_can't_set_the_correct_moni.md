---
title: "Can't find the reason I can't set the correct monitor resolution!!"
date: 2010-06-07
forum: General Help
---

### Post by CoreJohnson on 2010-06-07
Hi.  

I'm not sure why this is so difficult.  I decided to upgrade to 10.04 from 9.04 after an update messed up my graphics and I had to get some work done rather then sift threw a mound of sparsely detailed possibilities.  Also I'm not an leet coder.

So really I've installed 10.04 on many machine's with many different video card's and many different monitors.  But to some magnificently obscure reason I'm unable to set the correct resolution on any single computer.  Ati, Nvidia.  Not intel on second though.

I've managed to scrounge up some tidbits of info on the new KMS (kernel-mode-setting) technology.  I've run threw a few suggestions threw out the forums and across the net.  I've tried al sorts of drivers.  I've tried removing the xorg.conf but I've seen little info on why that is other then it is not needed.  I've added things to /etc/default/grub, I've removed things. I've gone threw synaptic and removed everything Nvidia and reinstalled it.  This by the way is always off a fresh install every time.

So here it is.  I'm at the end of my rope.  I know this must be some new way of doing things but It just seems odd that every computer I've tried has failed me.  I need the correct resolution to work.  I can't keep burning the eye's out of my head looking for possible solutions on crappy resolutions.  

I'm sorry for the rant.  I'm frustrated and seriously considering switching to Redhat despite having to pay for there service's.
Could anyone shed some light on my gloomy situation.  I want to keep promoting Ubuntu with out saying "if you can get such and such working"

Thanks

---

### Post by Mark Phelps on 2010-06-07
What you are experiencing is typical of new Ubuntu releases.  In every release, they change some major stuff "under the hood".  If you're lucky, in the case of YOUR machine, this will make things better.  If you're not so lucky, they will at least not make things worse.  If you're really unlucky, they make things a lot worse.

With the recent two Ubuntu releases (9.10 and 10.04), video drivers seemed to have fared worse than in the older releases.  I've been running open source drivers since ATI dropped fglrx support for my card over a year ago -- and haven't had a video-related problem since.

But, there's no "miracle cure" that is going to work across machines -- and across releases.  What you have been doing is quite typical of some of the hoops you have to jump through to get a new Ubuntu release to work.

The "good news" is that, with the LiveCD option, at least you can discover hardware-related problems BEFORE you install the latest releases -- and then, as I have, decide to stay with the previous release until they work out the new problems.

---

### Post by CoreJohnson on 2010-06-07
That is a fair point to some degree. I think I read that post some other place too ;) I just was hopping for a little more info on the subject.  I have found it rather difficult to find much info on how these changes are being implemented.  Other then the release notes, do you or anyone know of a central location for ubuntu graphic/driver/hardware/software information.  Like a comprehensive guide to new graphic's technology's.  I'm sure something is in the works.
Being it is an LTS and all.  
I would like to offer my service's for such an endeavor, but I just feel I would lack the amount of time that was properly needed to research/master such a task.
Perhaps in many moons when I've be able to hone my skill set.

---

### Post by wilee-nilee on 2010-06-07
Mark Phelps makes some good points. I think the only difference with the LTS is the long term support so some additional stuff is added in that it is supported longer, but some things are added to the new release that are not put in the LTS.

Meerkat out of the box in it's development stage had support for a ati card that neither Karmic or Lucid didn't.
It may only be, not more support but that it defaults to the generic driver I'm not sure, as I have never had to do driver installs for a card, if it doesn't just work I find a distro that does, the lazy approach.

---

### Post by CoreJohnson on 2010-06-07
True.  But on a second thought.  Is your display not a fundamental component of any desktop.  That's where most of the work is done is it not?.  As strong as a terminal alone is, black and white.  Ahhemm.  Green and black alone is enough to crack a mind. I would think that the focus around the thing you look at the most would have a high priority. Perhaps have a better degree of detail and documentation.  In an LTS version of course.  Unless it is still in it's infancy with the intent of being worked on as the next few months or years proceed. The graphics issue's anyways.

---

### Post by wilee-nilee on 2010-06-07
> **CoreJohnson said:**
> True.  But on a second thought.  Is your display not a fundamental component of any desktop.  That's where most of the work is done is it not?.  As strong as a terminal alone is, black and white.  Ahhemm.  Green and black alone is enough to crack a mind. I would think that the focus around the thing you look at the most would have a high priority. Perhaps have a better degree of detail and documentation.  In an LTS version of course.  Unless it is still in it's infancy with the intent of being worked on as the next few months or years proceed. The graphics issue's anyways.

The manufactures are not writing drivers for open source by and large so, I think this is just the limitation of only so much can be done by any group trying to write drivers that will work. It would be awesome if all the drivers were available, so that a person could pop in any open source, and it just works, but this isn't even possible with computers made to run proprietary software. I used to go over to the W7 forums to try and help the dual-booters, and would see all kinds of problems that were with that proprietary OS. I had to close my account there it was really a grub paranoia, and people who would never go near the cli to do some basic work. And just hardheaded people with guru status whatever that is LOL, that had some basic gui fixes and cried it's grubs fault, if their easy fix didn't work that made it very unpleasant to deal with them. Nice people by and large but there is a group that runs the help part of the forums like a Stalinist state.

I would agree that it ain't much without a monitor thats for sure.

---

### Post by CoreJohnson on 2010-06-14
> **wilee-nilee said:**
> The manufactures are not writing drivers for open source by and large so, I think this is just the limitation of only so much can be done by any group trying to write drivers that will work. It would be awesome if all the drivers were available, so that a person could pop in any open source, and it just works, but this isn't even possible with computers made to run proprietary software. I used to go over to the W7 forums to try and help the dual-booters, and would see all kinds of problems that were with that proprietary OS. I had to close my account there it was really a grub paranoia, and people who would never go near the cli to do some basic work. And just hardheaded people with guru status whatever that is LOL, that had some basic gui fixes and cried it's grubs fault, if their easy fix didn't work that made it very unpleasant to deal with them. Nice people by and large but there is a group that runs the help part of the forums like a Stalinist state.

I would agree that it ain't much without a monitor thats for sure.

It would be nice if more hardware company's were more receptive to the Linux culture.  Otherwise it is left up to the supporters of the distro to graciously speed there time developing the drivers and supporting changes as they happen.  I can see it getting better but it's still a challenge sometimes.  

Is the new way of supporting graphics cards in the kernel much better ??

---

