---
title: "Everything has Gone Blurry"
date: 2009-11-24
forum: General Help
---

### Post by Penguin Guy on 2009-11-24
I was messing around with some Compiz settings and some AMD settings, rebooted and now my computer's blurry - presumably some kind of permanent anti-aliasing. Thing is, I'm not sure which setting did this. It'll take me forever to test each setting one by one to find which one caused this - could someone give me a clue?

P.S. I'm not sure how the print-screen tool works - the screenshot may look normal for you.

---

### Post by Sam on 2009-11-24
Disable motion blur in compiz, and if it don't work, try reseting compiz settings ([compiz config settings manager](apt:compizconfig-settings-manager), preferences, profile > reset to defaults.

---

### Post by Penguin Guy on 2009-11-24
> **Sam said:**
> Disable motion blur in compiz, and if it don't work, try reseting compiz settings ([compiz config settings manager](apt:compizconfig-settings-manager), preferences, profile > reset to defaults.
Thanks! Motion blur wasn't enabled, but as soon as I used the reset defaults option my screen returned to it's usual clarity! Quickest fix for a problem I've ever had! :KS

---

### Post by adrohak on 2009-12-02
I am suffering from the same issue, but resetting the compiz defaults didn't fix it for me! any other ideas?

---

### Post by chadillac83 on 2010-03-02
Disable "Bicubic Filter" in compiz config manager, fixed it for me.

---

