---
title: "What command do I use to see my BIOS?"
date: 2009-12-07
forum: General Help
---

### Post by dpeizero on 2009-12-07
On..ubuntu 9.10 karmic koala (I love typing that. koalakoalakoala<3)...

Yeah. That. :D

---

### Post by u.b.u.n.t.u on 2009-12-07
It depends on the mainboard, BIOS, and if branded.

For me to access BIOS it is the "Delete" button shortly after boot.

If you have your mainboard manual, best to check that.

---

### Post by adaucourt on 2009-12-07
> **dpeizero said:**
> On..ubuntu 9.10 karmic koala (I love typing that. koalakoalakoala<3)...

Yeah. That. :D

This guy maintains a good list that you can try:
[http://michaelstevenstech.com/bios_manufacturer.htm](http://michaelstevenstech.com/bios_manufacturer.htm)

---

### Post by SuperSonic4 on 2009-12-07
BIOS (**B**asic **I**put **O**utput **S**ystem) is independent of OS - the only time the OS would interact with it is when the user flashes the BIOS to upgrade it (a very risky procedure which can screw the motherboard so don't do it)

Best way is to look for a DEL or F2 button when turning on the PC

---

### Post by burton247 on 2009-12-07
The OS shouldn't make a difference. The BIOS gets loaded first, then MBR and hopefully grub. (I think that's right)

Basically, restart your computer, before the boot menu pops up it should tell you which button to hit to access your BIOS.

What computer is it out of interest?

---

### Post by SuperSonic4 on 2009-12-07
> **burton247 said:**
> The OS shouldn't make a difference. The BIOS gets loaded first, then MBR and hopefully grub. (I think that's right)

Basically, restart your computer, before the boot menu pops up it should tell you which button to hit to access your BIOS.

What computer is it out of interest?

Yep, that's right, the very first bit of grub is on the MBR which directs the computer to wherever /boot is. I would put POST between BIOS and MBR

---

### Post by burton247 on 2009-12-07
Oh i see, cheers for clearing that one up

---

### Post by u.b.u.n.t.u on 2009-12-07
> **adaucourt said:**
> This guy maintains a good list that you can try:
[http://michaelstevenstech.com/bios_manufacturer.htm](http://michaelstevenstech.com/bios_manufacturer.htm)

Good post, and bookmarked!

---

