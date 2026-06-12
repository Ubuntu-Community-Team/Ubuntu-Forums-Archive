---
title: "config hack help"
date: 2009-12-21
forum: General Help
---

### Post by moneymonk on 2009-12-21
My wife is a teacher and inherited a couple Eee Acer mini notebooks through a now defunct program at her school.  the program gave the kids these laptops with xubuntu on them for free, however, they had to complete 40 hours of math and english workshops on the laptop before it would be unlocked to be used as their own. she would like to re-purpose one of these minis without logging 40 hours of 6th grade math and reading drills into it.  

it looks like the machine boots to X for a second at which point the educational program takes control and locks-up the laptop. i booted to recovery mode and got into a root shell, but i cant figure out where this educational program lives and how to hack it out.  

any ideas would be helpful.  I have used ubuntu extensively in the past, but im admittedly a little rusty.

thanks-

mm

---

### Post by Iowan on 2009-12-21
I'm just flailing in the dark, too, but check the */etc/rcX.d* directories to see what may be starting in various runlevels.

---

### Post by Leppie on 2009-12-21
try installing sysv-rc-config, it will show you everything that gets started for all runlevels.

---

### Post by synapsys on 2009-12-21
You could always install a fresh copy of xubuntu.....

---

