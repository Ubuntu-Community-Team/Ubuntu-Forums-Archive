---
title: "High CPU after Lynx Upgrade."
date: 2010-05-02
forum: General Help
---

### Post by EoRaptor013 on 2010-05-02
Used update-manager to update from 9.10 to 10.04 on my Dell E1750 laptop. After fixing some issues with booting, all seems well... Except that my CPU is running continuously above 70% and full speed (2Ghz), and the system is overheating. I believe the overheating is due, in part, to the fact that Lucid Lynx seems to break the Dell i8K monitor drivers. But, what's causing the system load?

The three top processes are XOrg, something called indicator-apple, and indicator-sound. What are the indicator processes, why do they use so much CPU resources, and what can I do to fix them? 

Thanks!

Randy

---

### Post by UbuNoob001 on 2010-05-03
> **EoRaptor013 said:**
> ...Except that my CPU is running continuously above 70% and full speed (2Ghz), and the system is overheating. I believe the overheating is due, in part, to the fact that Lucid Lynx seems to break the Dell i8K monitor drivers. But, what's causing the system load?

The three top processes are XOrg, something called indicator-apple, and indicator-sound. What are the indicator processes, why do they use so much CPU resources, and what can I do to fix them? 
Randy


Randy, You are not alone. I too, with a dell insp 1545 am having same problem. Even with no major programs open one processor sticks at 100 while the other is 50 ish.   A restart fixed the problem temporarily. 

Also check your system monitor and see if Firefox is using Java/Npviewer.bin both of which stayed in the process cue AFTER FF closed for me hogging 90%.   I am having similar over heating problems. 

here is another post like yours you may want to follow : [http://ubuntuforums.org/showthread.php?t=1470116&highlight=lucid+cpu](http://ubuntuforums.org/showthread.php?t=1470116&highlight=lucid+cpu)

---

### Post by EoRaptor013 on 2010-05-03
I don't regularly use Firefox - mostly Google-Chrome. But, following your link, and looking around, Chrome might have similar problems. OTOH, CPU's run hot ~70% with no browser running. Main culprit appears to be these two indicator threads: indicator-apple; indicator-sound. So far, haven't determined what those are; particularly "apple." 
Thanks.

---

### Post by ossi1970 on 2010-05-26
I had the same problem. CPU-usage was always over 70%. I stopped the service "indicator -sound" and immediately the CPU-usage of both cores dropped to around 10% even with Firefox and VLC-Player running.

---

