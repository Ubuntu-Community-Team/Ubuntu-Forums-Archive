---
title: "Cannot remove Evolution"
date: 2010-12-23
forum: General Help
---

### Post by gdanko on 2010-12-23
Why are we forced to keep evolution components!? I tried to remove them and ended up losing gnome-applets and a host of other things. This is ridiculous. I liken it to IE being tied into Windows.

---

### Post by iosuna86 on 2010-12-23
How are you trying to remove it?

What exactly are you removing?

I removed Evolution last week with no problem via Software Center. The applet removes itself after that so there was no need to remove things from the gnome-panel.

Let's see how you did it and let's try to fix it.

---

### Post by mike555 on 2010-12-23
You need to keep; evolution-data-server common , I don't like it ether , I hope they change it ...

---

### Post by gdanko on 2010-12-23
> **mike555 said:**
> You need to keep; evolution-data-server common , I don't like it ether , I hope they change it ...

I did something like

apt-get purge evolution-pkg1 evolution-pkg2 ....

Upon reboot there was no task bar, no applets, etc.. This is insane.

---

### Post by iosuna86 on 2010-12-23
> **mike555 said:**
> You need to keep; evolution-data-server common , I don't like it ether , I hope they change it ...

That's true, I can see via Synaptic that evolution-common, evolution-data-server and evolution-data-server-common, evolution-indicator, evolution-plugins, evolution-webcal... are currently installed, although Evolution itself is not installed in Software Center.

Is it safe to remove it all?

---

### Post by iosuna86 on 2010-12-23
> **gdanko said:**
> I did something like

apt-get purge evolution-pkg1 evolution-pkg2 ....

Upon reboot there was no task bar, no applets, etc.. This is insane.

It is INSANE, as you said. No clue about that. Have you tried removing the packages from Synaptic? Maybe that's a safer way to do it.

---

### Post by iosuna86 on 2010-12-23
> **mike555 said:**
> You need to keep; evolution-data-server common , I don't like it ether , I hope they change it ...

I just marked evolution-data-server-common for complete removal and it warned me that other packages were to be removed, among which there where gnome-applets and gnome-panel. I safely removed the other packages.

So yeah, that's the only thing you need to keep.

---

### Post by dryphi on 2011-08-31
Why can't you just mark evolution-data-server-common for complete removal, then UNMARK the other packages? Or reinstall them after removing EDSC?
I'm trying to do the same and this whole thing seems silly to me.

---

### Post by IanW on 2011-08-31
It's because the indicator applet _depends_ on evolution-data-server-common, instead of _recommending_ it.

However, Oneiric is defaulting to Thunderbird for email instead of Evolution, so this may change.

---

