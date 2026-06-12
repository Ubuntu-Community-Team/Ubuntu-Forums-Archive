---
title: "Power manager hangs and shutdown, suspend fails"
date: 2011-09-10
forum: General Help
---

### Post by andersq on 2011-09-10
I've recently (since a couple of days) gotten acquainted with an annoying problem. Not sure when it appears but after some time of use, sometimes several suspend/resumes, the system starts behaving strange. It does no longer react to closed lid or power button pressing and applications like Firefox, System Monitor and Power Manager stops responding.

Using menues to suspend only locks the screen (which I can unlock).

Using menues to shutdown starts a shutdown, but complains about Power Manager not responding. If I ask to close it the shutdown continues but gets stuck after the Ubuntu splash shows. Only hard shutdown solves it.

Ubuntu 11.04, Lenovo Thinkpad T60p, second HDD in DVD bay automounting in fstab (could that be the problem?).

---

### Post by andersq on 2011-09-18
Bumb.

Does not happend very often (once every two days) but it very annoying.

---

### Post by andersq on 2011-10-01
Seems almost gone now. Hasn't happened in a week now. Maybe it was just a short pre-autumn depression.

---

### Post by andersq on 2011-10-25
Ok. It's back again. Still super annoying. I have noticed however that it sometimes takes unusually long for the computer to get into sleep. Like there is some kind of delay that prevents the going to sleep process to start.

For example; I close the lid because I need to do something, wait for a minute to check if it goes to sleep or not which it doesn't, leave the computer with the lid closed and when I come back some ten minutes later it is soundly asleep.

If I try putting it to sleep then realise that it will not and instead want to shut it down thought the menus, there are some programs that have stop responding. So far I have managed to not lose any important data (by saving, saving and saving), but for ex Rhythmbox, Firefox and the Power Manager come up as not responding. And most of the time the shutdown halts at the shut down splash screen.

Still running 11.04 btw.

---

### Post by andersq on 2011-10-31
It seems like I have found a solution! Or at least a way around the issue.
While testing around a bit I found that the problem only seems to appear when GKrellM is running or has been running. I have no idea how that is related, but it seems to work better without it anyway.

So good bye GKrellM.

Anybody got a tip of another sysmon that is as super lean and can monitor temperatures and fan speeds?

/Anders

---

### Post by andersq on 2011-11-08
Ahrg! It's still there. This is the most annoying thing I've had to deal with since I installed Ubuntu for the first time back in the hedgehog days.

I would really appreciate any input here. Is my description missing all kinds of accuracy? Is this a known bug without solution? Should I just reinstall the whole thing and hope it's not there next time?

---

