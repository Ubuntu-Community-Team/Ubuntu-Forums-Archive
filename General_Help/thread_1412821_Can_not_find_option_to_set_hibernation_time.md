---
title: "Can not find option to set hibernation time"
date: 2010-02-21
forum: General Help
---

### Post by nicocarbone on 2010-02-21
Hi. This may be a noob question, but I can't find the option to set the computer to hibernate after a given idle time. In the Power options there is an option to suspend, but not to hibernate. 

Is there other way to set the hibernation time? 

Thanks you,

---

### Post by pi/roman on 2010-02-21
Open up configuration editor:
gconf-editor

Then go to /apps/gnome-power-manager/actions/sleep_type_ac
You can change that setting to hibernate your computer when it is inactive.

---

