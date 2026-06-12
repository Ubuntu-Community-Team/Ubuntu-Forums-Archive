---
title: "Update frequency question"
date: 2006-06-18
forum: General Help
---

### Post by xenomorph99 on 2006-06-18
Is the current frequency of updates typical for Ubuntu? I think this is now about the fourth in a week.

Is it likely to tail off anytime soon? Should people be worried that so many updates are required so often?

Ta,
Xeno

---

### Post by marcozs on 2006-06-18
I think the latest were updating Gnome from 2.14 to 2.14.2 ... anyway if you see how quickly the software is developed in the opensource world I would say it's very nice to have always the latest version available... that's why I like Ubuntu...

---

### Post by 23meg on 2006-06-18
Note that you won't always have the latest available version; after a stable Ubuntu release only security updates are available until the next one.

---

### Post by marcozs on 2006-06-18
Then you can use the backports repos :-)

---

### Post by homersbrain on 2006-06-18
> I think the latest were updating Gnome from 2.14 to 2.14.2 

Is there any way of rolling back the computer to a state before I applied these updates (like in windows)? They have made my dapper system unusable.

---

### Post by marcozs on 2006-06-18
[QUOTE=homersbrain]Is there any way of rolling back the computer to a state before I applied these updates (like in windows)? They have made my dapper system unusable.[/QUOTE]

There is something like "Package->Force Version" in Synaptic, but I've never used it...

---

### Post by xenomorph99 on 2006-06-18
[QUOTE=marcozs]I think the latest were updating Gnome from 2.14 to 2.14.2 ... anyway if you see how quickly the software is developed in the opensource world I would say it's very nice to have always the latest version available... that's why I like Ubuntu...[/QUOTE]

Yes, but it would also be nice to be able to stick with a particular 'snapshot' but whilst also obtaining security updates (if possible).

I feel sorry for those on 56k..they must spend more time updating their system (if they choose to) than anything else.

Ta
xeno

---

### Post by Ramses de Norre on 2006-06-18
When you don't enable backports you should only get security updates.

---

### Post by xenomorph99 on 2006-06-18
How do I do that then? The forum sticky on backports doesn't cover 6.06 and the main backport page (#1 googe hit) is down.

Ta,
Xeno

---

### Post by Ramses de Norre on 2006-06-18
How you disable them? Remove all instances of backports from your /etc/apt/sources.list.
And I don't think there've been backports for dapper yet. All current updates should have been bug fixing or security updates I guess.. 

If you really want to get security only than you could maybe delete the non-security repos too but I'm not sure about the consequences of doing that..

---

### Post by marcozs on 2006-06-18
There won't be any backport until the development of the next Ubuntu version starts... anyway you can disable them also from Synaptic, going in Settings->Repositories and then uncheck the repos where it says Backports...

---

### Post by VitalityChernobyl on 2007-11-07
Posting here rather than making a new thread even though this is an old thread.

Is there any planned frequency to the updates to the backport repo or the security updates or are they randomly published when each is suitably tested and deemed ready for the user base?

---

