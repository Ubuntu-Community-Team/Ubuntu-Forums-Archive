---
title: "HEEELLLP!! Bleeding edge graphics crashed me!"
date: 2009-09-26
forum: General Help
---

### Post by BarefootSoul83 on 2009-09-26
I was trying the settings in the sticky thread for Intel graphics... The optimal settings were great...but I wanted to try bleeding edge because my dual screen wasnt working.  Bad idea...it crashed my graphics...I cant boot into ubuntu...so I'm using the live cd... 

is there way to get to my normal root? so I can fix this?!?!?!  


HEEEELLLLP!

---

### Post by BslBryan on 2009-09-26
Eject the LiveCD, and start up your computer.

As GRUB is booting, press the Esc key to show the menu.

Boot into Recovery Mode, and when you get to the menu, select "xfix".

This process will be done in less than a second, so it might seem as though nothing actually happened.  It will bring you back to the menu, and either select "drop to a root shell", and enter the command:
```
reboot now
```

Or just select "resume normal boot."

Hopefully, this alone should fix the problem.  Let me know what the outcome is.

---

### Post by BarefootSoul83 on 2009-09-26
no dice....

There are backoff instructions on the ubuntu forum....I just cant get root privileges in live to get to the /etc/apt/sources.list and basic terminal functions for my main machine...all the terminal shows is ubuntu@ubuntu instead of my normal "donald@tux"

---

