---
title: "RAM maxed out in 10.04"
date: 2010-07-14
forum: General Help
---

### Post by republicson on 2010-07-14
I have 512mb of RAM, which has served me well on all previous ubuntu installations. Now, after upgrading to 10.04, I am using 85-90% of my ram according to System Monitor, by only running an Internet browser (either chromium or firefox). Trying to navigate file menus or (horrors!) run OpenOffice.org, just adds to the sluggish nightmare.

Other than my open programs, nautilus, gnome-panel, and wnck-applet are the only things over 1 mb. Beam.smp, metacity, clock-applet, etc are the next highest. 

Any suggestions on how to speed the thing up?

---

### Post by kerry_s on 2010-07-14
how bigs your swap? is it on?

---

### Post by dcstar on 2010-07-14
> **republicson said:**
> I have 512mb of RAM, which has served me well on all previous ubuntu installations. Now, after upgrading to 10.04, I am using 85-90% of my ram according to System Monitor, by only running an Internet browser (either chromium or firefox). Trying to navigate file menus or (horrors!) run OpenOffice.org, just adds to the sluggish nightmare.

Other than my open programs, nautilus, gnome-panel, and wnck-applet are the only things over 1 mb. Beam.smp, metacity, clock-applet, etc are the next highest. 

Any suggestions on how to speed the thing up?

Turn off video effects.

---

### Post by renkinjutsu on 2010-07-14
You may also want to switch to a lighter DE rather than use gnome.

---

### Post by snowpine on 2010-07-14
As of 10.04, 1gb ram is the recommended minimum for Ubuntu: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Assuming your hardware allows it, a RAM upgrade is your best bet.

If you are stuck with only 512mb for whatever reason, I would recommend installing a lightweight desktop environment such as Xfce or LXDE.

You might also look into disabling Compiz desktop effects and checking whether you're using the correct hardware driver for your graphics card. Graphics problems can definitely contribute to an overall "sluggish" feeling, especially things like navigating menus (which you specifically mention as a problem).

---

### Post by republicson on 2010-07-14
Swap is 980 mb with 278 in use when ram is at 80%.

I switched to 'none" in the "visual effects" tab under "appearance". It is still a problem though.

Seems like XFCE is the right move. I'll give it a try.

---

