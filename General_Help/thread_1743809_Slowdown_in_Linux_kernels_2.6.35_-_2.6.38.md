---
title: "Slowdown in Linux kernels 2.6.35 - 2.6.38"
date: 2011-04-29
forum: General Help
---

### Post by dhernandez on 2011-04-29
I just noticed this problem when I first upgraded to Maverick. Mouse movement would cause crippling slowdown on my machine whenever I used kernel 2.6.35, but for some reason would not in 2.6.32. I was hoping this problem would be fixed in 2.6.38, but it appears that I still have the same problem. Does anyone out there know how to remedy this?

---

### Post by idoitprone on 2011-04-29
This is very odd. Kernel 2.6.37+ should be faster, ever since they intergrated the 200 lines of wonder that improve desktop latency.  I have notice that it is fater However 2.6.38+ has a power regression. You should post your hardware. Your computer should faster not slower

---

### Post by dhernandez on 2011-04-30
Mmk. I have an HP G60 notebook, Celeron Dual-Core processor (1.8 GHz), with 3 GB of RAM.

---

### Post by idoitprone on 2011-04-30
I want to get rid of the obvious. Can you change the mouse speed? Since you upgraded the computer, the computer may revert to default mouse setting.

Go through System->Preferences->Mouse or type  ```
gnome-mouse-properties
``` in the  terminal or run command. Change acceleration and sensitivity to your hearts content.

If it is a hardware - software problem, I do not know what to do. Because I never really had a real mouse problem that need to be fixed

---

### Post by dhernandez on 2011-05-01
Okay, so I should probably clarify. Ever since upgrading to Maverick, I've been experiencing slight slowdown in general with the newer kernels, which has forced me to use older kernels. Mouse movement exacerbates the problem greatly, which is making Ubuntu unsuable. Additionally, when I upgraded to Natty, the problem showed up in 2.6.32, which was the kernel I was using with Maverick. Any ideas guys?

---

### Post by Underdog_RC on 2011-06-09
This may sound strange...but since you're using a laptop, and i'm using a desktop with wireless networking it may be related.  I'm seeing the same issues with 11.04 since upgrading.  Mouse is jumpy (not video related) when loading things, freezes if left untouched for a while and have to hard reboot.  I've read that there are some issues with Atheros based wireless cards (mine is Cisco, but it's an Atheros chipset).  Could be that is the root of the issue?  I don't seem to have it using it on a hard-wired machine here at work an they're at the same build level.  I've rebuilt my computer at home twice with the same results, yet, if I build one here at work (with the same hardware) that is hardwired and then take the drive home and put it in the other machine that is wireless...boom, same issue again. 
 
Seems too much of a coincidence, but i'll leave that up to those that are more experienced than I.  ;)

---

### Post by VanR on 2011-06-09
IMO 2.6.37 is the best kernel I have used. Faster than the previous versions, and not as buggy as the later versions.

---

