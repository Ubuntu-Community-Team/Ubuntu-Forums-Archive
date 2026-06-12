---
title: "Message Menu Doesn't Stay Open"
date: 2011-10-11
forum: General Help
---

### Post by CrusaderAD on 2011-10-11
Has anyone else experienced this when the messaging menu (with chat, broadcast, etc) doesn't stay open? You click it and it disappears right away? You have to click and hold to do anything.

---

### Post by swing_chef on 2011-10-17
> **CerealCypher said:**
> Has anyone else experienced this when the messaging menu (with chat, broadcast, etc) doesn't stay open? You click it and it disappears right away? You have to click and hold to do anything.
I have this same issue, though I've not made any progress on it.  I'm running the stock 11.04 with updates (as of today).  I see the same issue with the rest of the menus in the top-right.  I have, however, made two interesting discoveries that could possibly aid in the fix:
1. I performed the same installation steps in a Virtual Environment, and did not have these issues.
2. It could be related to timing, as I've noticed if I do an extremely short "tap" on the mouse instead of a "click", I can occasionally get the menus to stay open.  Using "xev", I do not see multiple registries of the mouse click, so it looks like it has something to do with the menus themselves.

---

### Post by swing_chef on 2011-10-17
Found a current bug that accurately describes my problem:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/874041](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/874041)

This is for duel-monitor setups.  On one screen, the menus work find, but not on the other.

---

### Post by CrusaderAD on 2011-10-17
> **swing_chef said:**
> Found a current bug that accurately describes my problem:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/874041](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/874041)

This is for duel-monitor setups.  On one screen, the menus work find, but not on the other.

Nice! You're right, it's a dual monitor issue. The menus on my right monitor work fine. It's not a big deal, just annoying. If I ever find a fix, I'll post it.

---

