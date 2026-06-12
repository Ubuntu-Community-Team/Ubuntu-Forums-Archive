---
title: "skype on startup"
date: 2009-12-30
forum: General Help
---

### Post by DavidFourer on 2009-12-30
I installed Skype and it starts when I boot.  I want to turn that off.  I looked in System>preferences>startup apps, and Skype is not listed.  What is starting it up?  Where do I go to remove it?

---

### Post by Leppie on 2009-12-30
this happened to me when i hadn't closed down skype before shutting down with the save session option enabled. even when switching this option off afterwards, it still keeps coming up. i resolved it by switching the option back on, made sure skype wasn't running when rebooting and then switching the option off again once back in ubuntu.

i suppose there's some configuration file where you can remove it, but i haven't been able to locate it (yet).

---

### Post by DavidFourer on 2009-12-30
That worked.  Now I remember turning off the save sessions box.  I see there is an option to "save the current session".  Once saved, it appears to stay saved.  So I think I can turn off all unwanted apps, go to sys>pref>startup>options, and click "remember currently running applications".

---

### Post by arubislander on 2009-12-30
> **Leppie said:**
> .. made sure skype wasn't running when rebooting ...

Great that you guys solved the problem on your own and shared here! But really when tinkering with your sessions you do not need to reboot to see the effects. Logging off and back on is enough (and quicker).

---

