---
title: "Pidgin disconnects on status change"
date: 2010-02-20
forum: General Help
---

### Post by Ronin_301 on 2010-02-20
I'm currently using Pidgin 2.6.2 on Karmic. Status changes work fine if I change it in Pidgin, but if I use the user switching applet to change my status is consistently disconnects my connection to Windows Live (but not AIM or GTalk), claiming that I have "signed on from another location". A quick Google and forums search turned up nothing. Has anyone else had this problem, or know of a fix for it?

---

### Post by neon_it on 2010-02-24
Same problem here.

I think that the problem is the absence of thelepathy framework support in pidgin.

---

### Post by neon_it on 2010-02-24
Removing my account in Empathy solved this issue.

Reference: [Pidgin account disabled on status change (MSN)]("https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/449007")

---

### Post by Ronin_301 on 2010-02-24
> **neon_it said:**
> Removing my account in Empathy solved this issue.

Reference: [Pidgin account disabled on status change (MSN)]("https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/449007")

Worked! Thank you, muchly appreciated.

---

