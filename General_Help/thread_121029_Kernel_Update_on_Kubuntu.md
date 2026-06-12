---
title: "Kernel Update on Kubuntu"
date: 2006-01-24
forum: General Help
---

### Post by noeluylee on 2006-01-24
I just installed my Kubuntu from the scratch. I currently have Kernel 2.6.12-9-386, i used uname -r to check. Do you guys recommend to upgrade my kernel to 2.6.12-10-386?

What's the advantage if I install the 2.6.12-10-386. please bear with me, Im kinda newbie, though been using ubuntu/ kubuntu for 3 months now.

Thanks and I hope I can get your input on this matter.

---

### Post by Jucato on 2006-01-24
Are you running on a i386 machine? coz if not, you might want to try to upgrade to the proper kernel for the proper machine (486,586, or 686). I'm also a bit new here, but I heard that if you're on a 586 or 686 machine, upgrading the kernel improves performance a lot.

---

### Post by asimon on 2006-01-24
I would upgrade. The difference between 2.6.12-9 and 2.6.12-10 are mostly fixed security issues.

---

### Post by moopere on 2006-01-24
[QUOTE=Fenyx]Are you running on a i386 machine? coz if not, you might want to try to upgrade to the proper kernel for the proper machine (486,586, or 686). I'm also a bit new here, but I heard that if you're on a 586 or 686 machine, upgrading the kernel improves performance a lot.[/QUOTE]

To be honest, I haven't seen a lot of evidence for this aside from the ever present rather empirical "it feels a lot faster" types of statements that you see everywhere.

The difference is probably measurable via benchmark, but theres not exactly of lot of readily available benchmarking going on either (or so it seems) so the whole faster/slower kernel compile or not to question seems to sit for most of the time in the realms of urban legend.

It used to matter a lot once upon a time when we were all running 2, 4 or 8MB RAM machines (8MB for the lucky ones) because optimising your kernel to only cater for you specific machine shrunk its size which gave a myriad of benefits (and speed....) - today, almost any machine you try ubuntu on will have 64MB or more, in fact, I think 64MB is the minimum spec for Ubuntu, and with this amount of ram, saving a few hundred Kbyte of RAM will not make a perceptable difference in your user experience.

As for recompiling to make use of newer instruction sets...yep, there might be a difference that can be measured (as I ponder above), but I'd sure like to see a bench or two to back this assertion up.

Cheers,
Craig

---

