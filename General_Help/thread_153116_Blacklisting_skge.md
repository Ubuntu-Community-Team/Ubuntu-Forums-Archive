---
title: "Blacklisting skge?"
date: 2006-03-31
forum: General Help
---

### Post by Lytton on 2006-03-31
I've been working on this incessantly for two full days, and I'm so close to solving the problem, but I've hit a wall.

I'm one of the people who has a Marvell Gigabit NIC, and I've learned mainly through these forums that Ubuntu (Breezy in particular, but I had the problem with Hoary as well) doesn't play nice with those.  So, I know that I need to use sk98lin instead of skge, and I've managed to get it to load at startup, but no matter what I do, I absolutely cannot keep skge from loading.

I have added "skip skge" to /etc/discovery.conf, "blacklist skge" to /etc/modprobe.d/blacklist, and, of course, "skge" to /etc/hotplug/blacklist.  For good measure, I have even added another blacklist file in /etc/hotplug/blacklist.d.  All this, and skge still loads on every reboot, without fail.

What can I do to banish this horrible thing from my system and actually get my internet to work?  I tried installing SuSE, and it was very easy to get sk98lin up and running.  None of this blacklisting was even necessary.  I was really hoping to be able to use Ubuntu, though.

I have to thank the community here for helping me get this far.  Now, are there any suggestions on how I might finish the job?

---

