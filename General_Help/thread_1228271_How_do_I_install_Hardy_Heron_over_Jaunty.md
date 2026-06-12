---
title: "How do I install Hardy Heron over Jaunty?"
date: 2009-07-31
forum: General Help
---

### Post by tomasterisk on 2009-07-31
I am interested in reverting to Hardy Heron on my dual-booted computer. Could someone tell me how to install this from the CD, replacing Jaunty but leaving my other partition (Windows XP) intact.

Thanks in advance.

I am writing this right now using the Hardy CD. I had forgotten how simple and uncluttered it was. Maybe from now on I will just go from one LTS to the next. I am not so enamored with effects, but prefer reliability.

---

### Post by wojox on 2009-07-31
This thread tells you how:

[http://ubuntuforums.org/showthread.php?t=1156261](http://ubuntuforums.org/showthread.php?t=1156261)

---

### Post by tomasterisk on 2009-07-31
> **wojox said:**
> This thread tells you how:

[http://ubuntuforums.org/showthread.php?t=1156261](http://ubuntuforums.org/showthread.php?t=1156261)

Thanks!

---

### Post by tomasterisk on 2009-07-31
OK. That worked like a charm. Well, it took a while, but I'm OK with that. I am now back in the version of Ubuntu that I first had.

---

### Post by tomasterisk on 2009-07-31
Next question: I remember that there was a way to keep your computer retro (to keep from having post-Hardy updates). Does it have to do with configuring synaptic, or what?

---

### Post by michy99 on 2009-07-31
I think that by default, Hardy only receives security updates.

---

### Post by slakkie on 2009-07-31
> **tomasterisk said:**
> Next question: I remember that there was a way to keep your computer retro (to keep from having post-Hardy updates). Does it have to do with configuring synaptic, or what?


Check the file /etc/update-manager/release-upgrades

Prompt=lts is the thing you want. But this is, like said, enabled by default.

---

### Post by tomasterisk on 2009-08-01
> **slakkie said:**
> Check the file /etc/update-manager/release-upgrades

Prompt=lts is the thing you want. But this is, like said, enabled by default.

Thanks. I checked out the file and saw this:

[COLOR=DarkSlateGray]# default behavior for the release upgrader
#
[/COLOR] [COLOR=DarkSlateGray]
[DEFAULT]
# default prompting behavior, valid options:
#  never  - never prompt for a new distribution version
#  normal - prompt if a new version of the distribution is available
#  lts    - prompt only if a LTS version of the distribution is available
Prompt=lts[/COLOR]

Does that last line signify that that is what it is set on now? The reason why I ask is that red arrow on my top panel telling me I have "381 updates" that I need to take care of. Can I be sure that these are all safe for me, that I won't, after I install these, I won't start the whole teethgrinder all over again of huge fonts, unclickable windows etc?

[COLOR=Blue]Update:[/COLOR] OK, never mind. I worried about nothing. I decided to start updating and can see that they are all Hardy updates. Good.

After the previous experience with updates in Jaunty I guess I just got paranoid.

---

