---
title: "How to disable blank screen when laptop lid is closed?"
date: 2009-12-28
forum: General Help
---

### Post by CONCORAN on 2009-12-28
Is there a way to set power management such that when laptop lid is closed, the screen doesn't go blank? I don't see the option in 'Power Management Preferences'.
I have some problem with a hinge on my laptop. Each time the screens bends forward by a bit, it seems to send 'lid closed' signal to OS which causes blank screen. However, upon pushing the lib back to original doesn't bring Ubuntu back, but blank screen persists. I am not sure why.

---

### Post by pbrane on 2009-12-28
That may not be a hinge problem. You could have a flat panel cable pinching. Try setting the Power Management Setting to suspend and see if your computer actually suspends. If it doesn't then you may have another issue.

But if you want to just disable the action you can run the onfiguration editor and under **/apps/gnome-power-manager/event_when_closed_battery**, just uncheck that option.

If that doesn't work try the **/apps/gnome-power-manager/buttons/lid_ac** and **lid_battery**
options. Just change one or both to "nothing".

Funny that the power manager GUI doesn't have the "nothing" option.

---

