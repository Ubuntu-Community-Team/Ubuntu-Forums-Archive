---
title: "System lockup in 11.10 afer installing nvidia-current, horrible/sluggish performance"
date: 2011-12-13
forum: General Help
---

### Post by Sim-I-Am :} on 2011-12-13
Hi there, I've recently upgraded (clean reformat/install) to 11.10 and am loving Gnome3/Gnome-shell very much.
However, I seem to be having some sort of issue with nvidia drivers. I have a Gateway P-6860FX with a 1.8GHz Core2Duo cpu and a nvidia 8800m GTS 512mb card. 
Upon first login, I have four options for nvidia drivers in jockey; nvidia-173, nvidia-173-updates, nvidia-current, and nvidia-current updates. The first entry (nvidia-173) is activated and "In use", but just about anything on-screen is incredibly laggy/jumpy (ie, gnome-shell animations, file/web browsing actions like scrolling, etc.) almost to the point of being unusable....
When I try to activate the nvidia-current drivers (and, of course, reboot), the performance is 100% better, everything runs smoothly and responsively, but the computer locks up after about 60 seconds afer logging in....

I've tried using the x-swat ppa's, i've tried using the drivers from the official nvidia site, I've tried purging all nvidia-related packages/installations and reinstalling -- I've tried just about every possible solution google could turn up for me, but with no success....

In my frustration, I wiped the ubuntu partition and installed Fedora 16, but despite the fact that I have had no stability issues so far and everything has been running relatively smoothly for me, Fedora just can't quite match up to Ubuntu in terms of support and compatibility....And I can't afford spending the extra time to re-learn what meager terminal knowledge I've acquired in my 3 years of using Ubuntu (ie, using yum vs apt; no PPA support; different terminal functions, etc)

I've tried reinstalling twice, but this issue has come up both times.

You can read more [HERE]("http://askubuntu.com/questions/86554/system-lockup-in-11-10-afer-installing-nvidia-current-horrible-sluggish-perform")

As always, any help will be greatly appreciated. Please guys -- tell me there's hope; don't make me go back to windows.... >.<

EDIT: I am going to reinstall again tomorrow and have the installer NOT "Download updates while installing". Will report back....

---

### Post by Neobuntu on 2012-01-21
Wow. I can't believe no one has helped you yet. This is what happens when the community is disrespected, instead of fostered. ..and I'm say with **time saving**, and respectful transitions, so that we're not in a constant state of broken beta projects.

Meanwhile, **I'm using Mate temporarily**, and all is well with my Nvidia card, and the "recommended" additional driver. I've also found Plymouth, requires that choice.

I wish I could offer a fix. My Gnome Shell was working; until I installed the Addition (Nvidia) Drivers. Now, even when I remove it and reboot, Gnome Shell just stops at login, with background, panel, and free moving mouse pointer, that does nothing on click! It's the Gnome Shell specific Composting, perhaps.

**Unity (and 3D) works, ironically**. Oh Joy! [sarcasm]. That composting must be in order; with Nvidia 3D.

The kicker is, I'm not sure mine is falling back to Nouveau; when the Additional Nvidia drivers are removed! Perhaps that's why Gnome shell worked, on clean install, and before installing additional drivers. I usually install the Nvidia drivers first. Not this time. Gnome shell is now still broken, even after additional drivers are deactivated. 

Well, we got new, and we're driving people away; like mad. I want new. Not like this!

BTW. This is **NOT**, because of a push for greater user ease. We can not fail to stabilize, and save time, for all types of users. These problems are **NOT** because we are doing that. They are **NOT**, because tablets and phones have smaller screens. This is a leadership, and goal problem. We need progression. Progress can't be trashed by too much beta software! You can't break things just to get people to fix them. That's not what we're all about, IMHO.

Every release, is a long term service release; truth be told. [It's not the end date, that matters. **It's time savings!**]

What we need to do, is go to rolling releases, but with special clean install ISO's, **only** when the core requires this (perhaps yearly). Everything else, can be done through regular updates. Nothing should be pushed-out until it is better tested. We've got to encourage more widespread testing, of the release candidates, and do that work where it belongs. You can not use new Windows refugees, to beta test your distribution; while calling it a ready release! That's a lose/lose deal. It's stagnation. 

You've got to remember what Ubuntu is. The ready releases are not test beds, in any version. Ubuntu is a smoothing of Debian, and should work out of the box (with easy upgrades), and with **sane** choices. You see, there's working, and there's really built-out, flexible working well. There's far to much, "10 Things to fix Ubuntu" (which takes to much time to develop; after an "official release"); where you've just lost the general public. You can't do this without the community. You can't do this with just geeks (like me). We also need non-technical users, and respecting them, will not hurt us, it will complete us (Ubuntu).

We're just entered the age of development, for "granny and the geeks"; in parallel. That's the secret. We **can** do both. We must, or we **can** die to marginalization.

I've not ruled out the possibility of corruption, with todays collective hits, to open distributions, and working better out of the box. But, I'd never blame plain incompetence, on corruption.

---

### Post by Neobuntu on 2012-01-31
The positive spin on this reality, is to just use Mate; for now.

---

