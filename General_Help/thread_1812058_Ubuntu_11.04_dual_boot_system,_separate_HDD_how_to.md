---
title: "Ubuntu 11.04 dual boot system, separate HDD how to remove the Windows 7 option."
date: 2011-07-25
forum: General Help
---

### Post by Trilogin on 2011-07-25
I have two HDD's in my computer, one with Windows 7 and one with Ubuntu 11.04. I get a dual boot option after my motherboard posts which allows me to choose between the two operating systems.

If I choose Ubuntu, it then loads a purple screen which I would call (correctly?) a splash screen or a loading screen. Then I get another option, it says Ubuntu 11.04 generic or Ubuntu 11.04 recovery mode or Windows 7 loader.

How do I remove this choice? I want it to load directly into Ubuntu after I choose the option initially from the dual boot screen. I do not want to be asked twice what I want to load. 

Any help is appreciated :) Thanks!

---

### Post by Mark Phelps on 2011-07-25
Since you're getting the choice twice, that implies that you installed via Wubi -- in which case, Windows will present its first OS Selection menu (with only one entry for Ubuntu), GRUB then presents a second menu (with multiple entries for Ubuntu).

Is this what you're seeing?

If so, I don't believe there's any way around this as the menus are a side-effect of installing via Wubi.

---

### Post by Trilogin on 2011-07-25
I did install via WUBI.This is good information to know. Thanks!

---

