---
title: "Visual effects problem."
date: 2010-08-11
forum: General Help
---

### Post by Fayth on 2010-08-11
Hey all, I've been having this problem ever since I installed Ubuntu a couple weeks back, extra visual effects doesn't stay on for me on startup, I have to manually do it every startup. It's not really a major problem but I would like to know if there's a solution. The graphics card I have is the Nvidia GeForce 8400M GS.

Any help is appreciated :).

---

### Post by sanderd17 on 2010-08-11
Can you install compizConfig settings manager (ccsm) via the software center? There you can select the visual effect and I hope they will stay active after reboot.

---

### Post by Fayth on 2010-08-11
I have ccsm installed though I can't use any of the 3d effects (Yes, I've updated drivers) but the effects still turn off on reboot and I have to turn them on again manually every time...

---

### Post by techunit on 2010-08-11
Do you have a Corei7 by any chance a newer one? It could be defaulting the built in one.

---

### Post by Fayth on 2010-08-14
No I have the Intel(R) Core(TM)2 Duo CPU     T830...

---

### Post by overdrank on 2010-08-14
> **Fayth said:**
> Hey all, I've been having this problem ever since I installed Ubuntu a couple weeks back, extra visual effects doesn't stay on for me on startup, I have to manually do it every startup. It's not really a major problem but I would like to know if there's a solution. The graphics card I have is the Nvidia GeForce 8400M GS.

Any help is appreciated :).

Hi and you can add the command ```
compiz --replace
``` to the start applications under system, preference and this should solve the issue. :)

---

### Post by Fayth on 2010-08-17
I ran that in the terminal and I got this message : > libccs: dlopen: /usr/lib/compizconfig/backends/libgconf.so: cannot open shared object file: No such file or directory
compiz (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
.

---

### Post by shakma on 2010-10-29
Hi!

Just wanted to say that I was having the same problem as the original poster on my Asus EeePC 1005.  I didn't notice until I started using Docky, but it was becoming a real pain having to re-enable visual effects after every fresh boot (although that only happens once a week or less... it still made me dread a reboot that much more).  

Thanks for the tip - adding that code to the startup applications solved my problem!

Peace.

---

