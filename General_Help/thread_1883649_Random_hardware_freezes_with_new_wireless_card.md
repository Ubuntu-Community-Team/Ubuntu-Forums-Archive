---
title: "Random hardware freezes with new wireless card"
date: 2011-11-19
forum: General Help
---

### Post by captainmnb on 2011-11-19
I recently installed a new wireless PCI card (Linksys WMP600N, rt2860 driver) in my desktop. Now I get unpredictable hardware freezes. The screen locks up, no input works (or at least alt-SysRq-REISUB doesn't do anything), and any sound that's playing starts repeating like a broken record. This happens anywhere from right after logging in to half an hour later.

I had been having some trouble getting the wireless card to work at 5GHz, so I reinstalled the driver from the Ralink website, which I suppose may have messed something up. Using the old wireless card seems to avoid the problem, but that could also be because of me unknowingly messing something up while removing/installing the cards. I am currently running from a live CD and I haven't seen a freeze yet, but again, it's fairly unpredictable.

I'm running Ubuntu 10.04 64-bit on a custom-built PC.

Any ideas as to where to begin diagnosing or fixing this problem?

---

### Post by captainmnb on 2011-11-21
I'm now pretty sure that the problem is the wireless driver, which was downloaded from the Ralink website and installed using this guide: [http://en.gentoo-wiki.com/wiki/Ralink_RT2860](http://en.gentoo-wiki.com/wiki/Ralink_RT2860)

If I add the relevant module to /etc/modprobe.d/blacklist, I don't get any freezing, but of course I cannot then use the wireless.

Anybody know what might be causing the freezing, how to fix it, or whether there's another driver that might work for the card (Linksys WMP600N)? I've spent a lot of time Googling and searching this forum, but I haven't had any luck.

---

### Post by captainmnb on 2011-11-30
Brief update:

The freezing seemed to stop on its own temporarily, but then the wireless refused to connect 90% of the time. In the process of trying to fix that, I reinstalled the driver (again), and now the freezing is back.

Still no ideas from anyone?

---

