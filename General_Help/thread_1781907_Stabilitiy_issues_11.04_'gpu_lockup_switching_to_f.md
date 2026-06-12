---
title: "Stabilitiy issues 11.04 'gpu lockup switching to fbcon'"
date: 2011-06-14
forum: General Help
---

### Post by jonnyboysmithy on 2011-06-14
Hi guys,
 I have been having some problems with my 11.04 install, occasionally (like every 5minutes-3hours) my screen freezes nothing responds except the mouse still moves and thats it. I usually try to restart x (ctrl+alt+print-scrn+k) after a while it'l say some random long number and behind that 'gpu lockup switching to fbcon' then a scrambled screen of what i was doing. complete lockup.. this is very frustrating.
It seems to be getting worse as for firefox its slower than ever.

My cpu is a pentium 4 3.0ghz with 1gb ram
heres what graphics card I'm using:
jotham@jotham-desktop:~$ sudo lspci | grep -i vga
[sudo] password for jotham: 
01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a3)

Any help much appreciated!!

---

### Post by jonnyboysmithy on 2011-06-14
By the way, effects like desktop cube are enabled and working

---

### Post by jonnyboysmithy on 2011-09-29
Turned out the driver I was using was experimental and unstable, after installing the correct driver everything runs smooth.

---

