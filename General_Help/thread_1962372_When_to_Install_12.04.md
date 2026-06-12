---
title: "When to Install 12.04?"
date: 2012-04-21
forum: General Help
---

### Post by ttoolin on 2012-04-21
I have been awaiting the formal release of 12.04, before installing it.

Is there any disadvantage in doing a clean install of the beta, which is at a very late stage, over waiting until it is officially released, and then doing a clean install, then?

Thanks!!!!!

---

### Post by jadtech on 2012-04-21
the releasee I upgrade to today is working looking and working fine if ya dont want to wait  go for it I do recomend reading  all the documentation for it :) 

and if you have amd 64 bit dual core and amd ati video card dont forget to install apt python-apt before you do the upgrade  and do the up grade from the terminal or it will most likely fail ..

but this upgrade even has the ati 3d  all working fine for me

---

### Post by Hungry Man on 2012-04-21
Been using it for weeks. It's great.

---

### Post by Metul Burr on 2012-04-21
i haven't had any problems yet, been using it for acouple weeks

---

### Post by raja.genupula on 2012-04-21
if you want a stable 12.04 then wait for its release .

even some problems came if you don't care means you can go with it . 

what I'm trying to say is May be sometimes serious issues may cause and takes you to a fresh install . 

but many of our friends saying its fine so choice is yours my friend .

---

### Post by Metul Burr on 2012-04-21
You could just install the beta and test it out for a week and then do a fresh install when it's out. Then you can choose then to update and continue or do a fresh reinstall.

---

### Post by elliotn on 2012-04-21
it's almost here so just wait a bit

---

### Post by mörgæs on 2012-04-21
As a general rule people should wait 1-2 months after release before installing. If you don't have a particular reason to switch then stay with 11.10.

Moreover, if you have an Nvidia screen card: The closed-source drivers are in a bad state, so stick to the open-source (Nouveau) ones, if you for some reason have to use 12.04.

---

### Post by dcstar on 2012-04-21
> **mörgæs said:**
> **As a general rule people should wait 1-2 months after release before installing.** If you don't have a particular reason to switch then stay with 11.10.
........

That good advice only applies to sensible people, too many want to be "Crash Test Dummies" and then fill these forums with problems in the weeks after initial release while things are fixed.

A note to those who already have been or will be using 12.04 as soon as it is available: I suspect a lot of those who try to help in these forums will basically disappear for a month or so to avoid the usual storm of "Help me, I'm desperate" posts that flood the forums after **every** new Ubuntu release.

Good luck to those brave (silly?) enough to remain.

---

### Post by Mark Phelps on 2012-04-21
> **dcstar said:**
> That good advice only applies to sensible people, too many want to be "Crash Test Dummies" and then fill these forums with problems in the weeks after initial release while things are fixed.

FINALLY  A sense of reason!  You are to be applauded for saying this.

My own way of asking the same question (having done Ubuntu upgrades since the 7x days) is "How soon to you want to start dealing with the problems and breakage that a new release always brings?"

But, that is not in keeping with the "If it's NEWER, it must be BETTER" obsession that many folks have.

The only thing NEWER guarantees is DIFFERENT -- and that is not always better.

IF Canonical would ever get around to building a roll-back capability, where you could click a menu entry and get your OLD install back, I would encourage people to upgrade as soon as they could.  But until then, I agree with this approach.

---

### Post by jadtech on 2012-04-21
I am using 12.04 right now and it is running very well, I don't recommend any who is using there computer for work job and income take there only computer take the risk of installing as there only OS at all..

beta version of any software is not for the weak of heart or anyone not into learning how to deal with issues on there own ..

---

### Post by The Cog on 2012-04-21
I agree that if you need to ask the question, then it's probably better if you wait for a couple of weeks after the formal release. The first couple of weeks after release often see a some bug fixes for issues that get noticed by the large numbers of people who install as soon as it's released.

---

### Post by ttoolin on 2012-04-21
Thank you, everyone, for your input.  I appreciate all of the points that were brought up.

I'll consider it, some, through the day, but I'm probably make a backup of the important data on my 11.04 machine and go ahead and install the beta.  I'm not an ubuntu superstar, but I am savvy enough to deal with much of the stuff that may pop up.

If I decide to, or need to, I can reinstall again, my backup should be recent enough to be useable.

Thanks again for all of the comments.

---

### Post by mörgæs on 2012-04-21
Good, please mark the thread 'solved'.

---

### Post by dcstar on 2012-04-21
> **Mark Phelps said:**
> 
..........
IF Canonical would ever get around to building a **roll-back capability**, where you could click a menu entry and get your OLD install back, I would encourage people to upgrade as soon as they could.  But until then, I agree with this approach.

That highlights the main problem with these "upgrades", and it can be basically be solved by having the normal Ubuntu install create a separate /home partition by default and then installing any new Ubuntu release in its own, separate root partition. The initial Ubuntu install could ask the user if they want to reserve space for the next version (and 20GB isn't that much to set aside these days) and then there would be two partitions set aside for the future installer process to utilise.

The install process could extract the installed packages list from the old system and then install the same (or equivalent) packages on the new version. Migrating configuration etc. is also done as part of this process **if** the user wants to do this (some of us like a clean install).

People would then simply have the option of booting their old system or the new system and still access the same User data (within the constraints of changed structures that can occur for some apps).

Having this sort of setup would negate so many ongoing issues with Ubuntu and push it further up the tree as a viable replacement for most other OSs.

---

### Post by houseworkshy on 2012-04-21
The seperate /home is an excellent idea ( in general not just for new releases )  but there can still be problems when the bootloader is also changed.  I remember a tidal wave of "arrrhs" at the last switch.  Virtualisation is safer if people want to test stuff that isn't stable yet and only have one machine.

---

### Post by tmaranets on 2012-04-21
> As a general rule people should wait 1-2 months after release before installing. If you don't have a particular reason to switch then stay with 11.10.
Your probably right. Errors are often occur when a new OS is released. I'll Wait a little bit to make sure it is stable. That is why I don't get preview releases anymore. Thanks for the notice morgaes!!!

---

