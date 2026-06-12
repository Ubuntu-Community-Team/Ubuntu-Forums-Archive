---
title: "Live CD help"
date: 2009-11-03
forum: General Help
---

### Post by deathuntert on 2009-11-03
So I burned my live CD and when I boot from it I get the screen where I can choose what I want to do, I choose "try ubuntu without any changes to your computer" and I get a loading screen then the screen goes black and freezes like that, but I can press ctrl+alt+delete and that restarts the process, what should I do?

---

### Post by RedSingularity on 2009-11-03
Have you tried an alternate cd?  Those usually work if the regular one does not.

---

### Post by Larry Linux on 2009-11-05
Unfortunately, this is a big problem with many laptop installations using 9.10. There seems to be an Xorg problem relating to ACPI.

What you need to do is this..when booting the live CD, when you reach the point where it asks if you want to install, etc...do this.

Press enter on F-6

In the right corner you will see "acpi=off"

Highlight "acpi=off" using the checkmark. This will turn off ACPI

The CD should then boot as normal.

But as a caution, turning off ACPI can mess with the power management of your computer and the cooling fan. Turning off ACPI is not meant to be a long term solution, but only a test. At this point, unless the bug is fixed, I would recommend using 9.04.

---

