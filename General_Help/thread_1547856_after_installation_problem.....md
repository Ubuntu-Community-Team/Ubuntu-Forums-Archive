---
title: "after installation problem...."
date: 2010-08-07
forum: General Help
---

### Post by amite on 2010-08-07
i have been using linux for few months on my laptop and i am quite happy with it. now today i installed ubuntu 9.10 my old desktop,it installed smoothly but now  when i start it start without any trouble but after few seconds it hangs[keyboard,mouse doesn't respond].how long i wait,it doesn't work.
sys config:
intel pentium4[1.86 ghz]
1gb ram
40 gb hard disk[15 gb of ubuntu partition]
dual boot with windows7[ubuntu installed after windows7]

As i have installed windows7[10 gb partion]and it's working good(bit slower but okay),so i thought their is no problem with system configuration.
i need help what to do now.........:(

---

### Post by corrytonapple on 2010-08-07
Do you get to the desktop or login screen?

---

### Post by amite on 2010-08-07
yes,i logged in successfully,but after log in  every time system hang after few seconds .

---

### Post by navaneethan on 2010-08-07
I think trivial mother board support for your ubuntu system, which happened me too in debian

---

### Post by ajgreeny on 2010-08-07
What exact hardware, particularly graphics card?
Let's see the output of ```
sudo lshw -C display
``` in terminal from the live CD which I assume did work.

---

### Post by dino99 on 2010-08-07
might be the graphic driver not activated (system admin hardware driver)

boot into recovery mode to see errors during boot (hold "shift" key down at end of bios process to see the grub menu if it was hidden)

---

### Post by amite on 2010-08-07
> **ajgreeny said:**
> What exact hardware, particularly graphics card?
Let's see the output of ```
sudo lshw -C display
``` in terminal from the live CD which I assume did work.
live cd also didn't work.when i click on Applicatin tab drop-down menu appeared,when  i clicked accesories it hangs ,same as with regular instalation.to recover need to use reset button.

---

### Post by amite on 2010-08-07
when boot in safe mode every test give positive result.
lshw  -C display give following result:
description : VGA compatible controller
product : 82945G/GZ Integrated Graphics Controller
vendor : Intel Corpration
.
.
width : 32 bits
clock : 33 hz
capabilities : msi pm bus_master cap_list rom
configuration : driver=i915 latency=0
resources : irq:16 memory:fea80000-feafffff ioport:dc00(size=8) memory:dooooooo-dfffffff(prefetchable) memory:fea40000-fea7ffff

---

