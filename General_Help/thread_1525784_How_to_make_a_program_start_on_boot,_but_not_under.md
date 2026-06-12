---
title: "How to make a program start on boot, but not under root?"
date: 2010-07-07
forum: General Help
---

### Post by [CPR]-AL.exe on 2010-07-07
I need to make my website autostart after reboot. I may just add it to rc.local, but i don't want it to start under root. 

How could it be done?

---

### Post by StuartN on 2010-07-07
> **'[CPR]-AL.exe said:**
> I need to make my website autostart after reboot.

You could add it to a specific user's crontab, with the time setting **@reboot**, which is "Run once, at startup" according to **man 5 crontab**.

---

