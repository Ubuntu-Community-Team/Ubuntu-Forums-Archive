---
title: "Suspend on Laptop Lid Close?"
date: 2011-08-17
forum: General Help
---

### Post by Thedark7 on 2011-08-17
Hi,

I have settings set for my new HP laptop to suspend ubuntu (installed with wubi) when the laptop's lid is closed. However, that's not exactly what happens. 

When I close the lid, the keyboard backlighting, screen, and processor fans go out. When I open the lid, everything powers back on, but the screen is blank. I have to manually shut down the computer and turn it on again to get back to work. Any solutons?

[s] EDIT: If I manually suspend, then close the lid, everything works fine...[/s]

EDIT 2: Actually, no it doesn't. When I manually suspend, the keyboard and everything go off. But when I close and open the lid, it repeats the behavior mentioned before and I must restart. (if I close and open the lid quickly, the laptop doesn't seem to register the lid being closed and I can  press the power button to take it out of the suspended state) :confused:

---

### Post by frankbooth on 2011-08-17
[LIST]
[*]What HP model is it?
[*]Have you searched for a bug report on [Launchpad]("https://bugs.launchpad.net/")?
[/LIST]

You could also change the current behavior if no other solution seems available.

Either launch the power manager by pressing *ALT+F2* and type *gnome-power-preferences* or launch it through the terminal:
```

gnome-power-preferences

```

---

### Post by Thedark7 on 2011-08-17
It's an HP ENVY 14,

Everything is looking good in Power Preferences.

I'm not the only one with the problem:

[http://ubuntuforums.org/showthread.php?t=1497647](http://ubuntuforums.org/showthread.php?t=1497647)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/618813](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/618813)
[https://bugs.launchpad.net/ubuntu/+bug/695667](https://bugs.launchpad.net/ubuntu/+bug/695667)

Like I said, manually suspending works fine, but closing the lid messes everything up.

---

### Post by ofnuts on 2011-08-17
> **Thedark7 said:**
> It's an HP ENVY 14,

Everything is looking good in Power Preferences.

I'm not the only one with the problem:

[http://ubuntuforums.org/showthread.php?t=1497647](http://ubuntuforums.org/showthread.php?t=1497647)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/618813](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/618813)
[https://bugs.launchpad.net/ubuntu/+bug/695667](https://bugs.launchpad.net/ubuntu/+bug/695667)

Like I said, manually suspending works fine, but closing the lid messes everything up.There are similar problems on other machines that are the result of an incompatibility with BIOS settings or fixed by a BIOS update. I'm not saying this is the case here, but it's worth a quick jaunt in your BIOS settings.

---

### Post by scorp123 on 2011-08-17
I all of a sudden had the same issue on my 6 year old HP dv2108EA and Ubuntu 10.10: the previous update to the 2.6.35-30 kernel had a regression, thus breaking suspend on my laptop. I had to go back to the original kernel 2.6.35-22 that came on the installation CD. Now the latest update a few days ago (kernel is now at 2.6.35-30 #56) fixed it again.

What you could do: You could test if the same problem also occurs with other kernel versions too and/or other Ubuntu versions? If no and other kernels and/or Ubuntu versions (e.g. 10.10 vs. 11.04) work: then there must be a bug in the kernel and a future update should fix it (make sure you report it on Launchpad). If yes and the problem is there no matter what kernel version (e.g. the kernel that shipped with the CD vs. a freshly updated kernel) and no matter which Ubuntu release (e.g. 10.04 LTS vs. 10.10 vs. 11.04 vs. 11.10-preview) is used then it's something in your computer's BIOS and a BIOS-update (or downgrade?) might help.

---

