---
title: "Canonical tracking software"
date: 2010-08-10
forum: General Help
---

### Post by StuartN on 2010-08-10
I assume that uninstalling / disabling the new package canonical-census will have no adverse effects? It is not something that I would choose to install if it was on offer, so I don't intend accepting it by stealth.

[http://www.phoronix.com/scan.php?page=news_item&px=ODQ5MA](http://www.phoronix.com/scan.php?page=news_item&px=ODQ5MA)

[QUOTE="Phoronix"]**Canonical Begins Tracking Ubuntu Installations**
*Posted by Michael Larabel on August 09, 2010*

Just uploaded to the Ubuntu Lucid repository for Ubuntu 10.04 LTS (and we imagine it will appear shortly in Maverick too for Ubuntu 10.10) is a new package called canonical-census, which marks its initial release. Curious about what this package provides, we did some digging and found it's for tracking Ubuntu installations by sending an "I am alive" ping to Canonical on a daily basis.

The canonical-census v0.1 description is simply "canonical-census - send "I am alive" ping to Canonical." When looking at the Debian package source to this Python program, "Send an "I am alive" ping to Canonical. This is used for surveying how many original OEM installs are still existing on real machines. Note that this does not send any user specific data; it only transmits the operating system
version (/var/lib/ubuntu_dist_channel), the machine product name, and a counter how many pings were sent."[/QUOTE]

---

### Post by elliotn on 2010-08-10
Why wanna remove what wont help

---

### Post by mutrax on 2010-08-10
Why delete? Since it's fully transparent (hence "open source"), helping the cause won't hurt anyone and will give a more correct install number. This will allow ubuntu gain some street cred among manufactures etc..

I'm installing it by default if it helps.

---

### Post by StuartN on 2010-08-10
> **mutrax said:**
> Why delete? Since it's fully transparent (hence "open source")

"Fully transparent" would be showing me the contents of each upload, and requesting my permission.

I do not intend having an application run on my system, which a private company (Canonical) can subsequently update to view any data they choose.

---

### Post by m4tic on 2010-08-11
> **StuartN said:**
> "Fully transparent" would be showing me the contents of each upload, and requesting my permission.

I do not intend having an application run on my system, which a private company (Canonical) can subsequently update to view any data they choose.

Classic linux stereotype right here. reason why app developers move away from this platform is that people like you do not offer feedback. usage statistics are part of evolution, continue being paranoid my friend.

---

### Post by Noz3001 on 2010-08-11
I just installed it. Seems like nothing has changed ;D

---

### Post by badbradmx on 2010-08-11
so the program is there so canonical can trace how many ubuntu installations are around, its hard to track a open source project when people can pass on CD's

---

### Post by hawthornso23 on 2010-08-11
I find it odd that you distrust Canonical to the extent that you won't let a program send an innocuous ping, on the grounds that it might in some implausible future be updated to send other stuff.

This is bizarre. You are apparently running a whole operating system supplied to you by Canonical. If you don't trust Canonical that seems a rather odd thing to do.

Do you update your system regularly? If so then Canonical could put spyware on your system any time it wanted. It wouldn't need an innocuous census program to be present in order to do it.

Of course if Canonical turned to the dark side we'd catch them at it pretty quick - that is the virtue of open source. And why would they - it would destroy them overnight as a company.

The bottom line is you've got to trust the suppliers of your operating system. If you don't trust Canonical you  shouldn't be running Ubuntu, it is as simple as that.

---

### Post by five0xpres on 2010-08-11
> **hawthornso23 said:**
> The bottom line is you've got to trust the suppliers of your operating system. If you don't trust Canonical you  shouldn't be running Ubuntu, it is as simple as that.

Exactly.  As long as they restrict it to just reporting a live installation of their OS, I don't see the dangers of this kind of statistical data gathering.  It's really not that much different than your web browser reporting it's basic info to a website via the user agent.

---

### Post by bodhi.zazen on 2010-08-11
> **m4tic said:**
> Classic linux stereotype right here. reason why app developers move away from this platform is that people like you do not offer feedback. usage statistics are part of evolution, continue being paranoid my friend.

I see open source as free as in I have the freedom to modify my system, including the source code if I wish, to run the way I wish.

Personally I always perform a minimal install and install only the applications I want to use. I find that is easier then starting with a full system and removing things I do not like.

No need to insult people and accuse them of paranoia simply because they wish to modify their systems.

To answer the OP question, yes you can remove canonical-census (as you found out).

---

### Post by darolu on 2010-08-11
I do believe there should be some sort of notification about this application **if** it indeed is intended to be installed by default; just like the Debian packages-survey thing, the installers ask you if you want to send information about the apps you use to Debian. Users must have the liberty to choose.

Now, if I understood the article right, most of us don't have to worry about it as this "canonical-census" is for OEM installations only.

I agree with bodhi.zazen about the minimal install and build up from there.

---

### Post by StuartN on 2010-08-13
> **darolu said:**
> Now, if I understood the article right, most of us don't have to worry about it as this "canonical-census" is for OEM installations only.

I am a long-time Dell-Ubuntu customer, and my guess is that Dell is probably the OEM customer that requested this feature from Canonical. Somehow, I don't expect that my next new Dell will pop up an opt-in dialog with full disclosure.

I see that the topic has generated a lot of heat and little light, so probably nobody cares, but my objections are on the basis of security, potential change of purpose, the closed nature of the collected data and the precedent that OS tracking software would set.

> **m4tic said:**
> reason why app developers move away from this platform is that people like you do not offer feedback

"People like me"? Did you count my feedback?

---

