---
title: "Swappiness baffles me... Any explanations?"
date: 2012-05-23
forum: General Help
---

### Post by blackbird34 on 2012-05-23
Hi
I've been reading stuff on and off about Ubuntu's swap and lots of people saying low swappiness is good, etc. So when i installed Precise i put the swappiness at 5, thinking i had a decent system (Intel Celeron 900, less than 2 year old computer, 2GB RAM, 2.5 GB swap partition...). Unity, Cinnamon, even Gnome fallback seemed sluggish quite often.

Then I read [this]("http://kerneltrap.org/node/3000") article, that explains the complete opposite: putting swappiness at 100 makes the system faster! Turns out to be true, too. I don't get it at all (but i'm very pleased :D)...

How come?? Can anyone explain?

---

### Post by MadmanRB on 2012-05-23
You mean a swap partition?
Yes a swap partition can be useful especially on older machines, the problem is that swap is on your hard disk drive and it will only be as useful as that said drive.
So it wont always make things faster

---

### Post by ajgreeny on 2012-05-23
Have a good read through [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) which hopefuly will make things a bit clearer for you.

---

### Post by blackbird34 on 2012-05-23
I've read them more or less already, been with Linux a year, but what I really wanted to know (to make myself clearer) is WHY so many guides suggest putting swappiness so low (5 or 10) (as in here: [https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F) )when me putting mine to 100 suddenly makes my machine fly (in comparison to 5 or 10)? I don't see the logic really...

---

### Post by anaconda on 2012-05-23
in my experience putting a big value to swappiness will cause swap to be used even if there are lots and lots of free RAM.

Can't understand how that could make the system faster since RAM is a lot faster than swap space.

different thing if most of RAM is already in use.

---

### Post by wilee-nilee on 2012-05-23
The article is rather old.

---

### Post by blackbird34 on 2012-05-23
Well, that's what I thought too, until I chanced upon [this debate : http://kerneltrap.org/node/3000]("http://kerneltrap.org/node/3000"), read otherwise, aand had a go with it... Mystery.
If one uses, say, 90% of one's RAM, does that make the box slower (as the system might be looking for the right processes etc.) than if one uses (let's say) 20% of RAM?

---

### Post by wilee-nilee on 2012-05-23
> **blackbird34 said:**
> Well, that's what I thought too, until I chanced upon [this debate : http://kerneltrap.org/node/3000]("http://kerneltrap.org/node/3000"), read otherwise, aand had a go with it... Mystery.
If one uses, say, 90% of one's RAM, does that make the box slower (as the system might be looking for the right processes etc.) than if one uses (let's say) 20% of RAM?

 What is your ram amount?

---

### Post by blackbird34 on 2012-05-24
2GB... Which has always been plenty... (see first post ;-) )
I Just don't get this as my present experience seems to flatly contradict everything i have read on the subject. Maybe i'm dreaming.

---

### Post by diesch on 2012-05-24
With  a high swappiness value there's more RAM available for disc caches which can speed up your system, especially if your disc is slow. 

On the other hand it can make the kernel to swap out parts of some programs so you may notice a delay sometimes, like when switching between applications.

Low swappiness values help to avoid this delay at the cost of less RAM for disc caches.

Could you post the output of
```
 vmstat -s 
``` in some typical situation where your system feels faster with  a high swappiness?

---

### Post by blackbird34 on 2012-05-24
nad@Nad:~$ vmstat -s
      1981040 K total memory
      1905608 K used memory
       992056 K active memory
       759080 K inactive memory
        75432 K free memory
        76256 K buffer memory
       974732 K swap cache
      3071996 K total swap
       139532 K used swap
      2932464 K free swap
       568135 non-nice user cpu ticks
         3282 nice user cpu ticks
       124866 system cpu ticks
      2521822 idle cpu ticks
        85363 IO-wait cpu ticks
            5 IRQ cpu ticks
         1341 softirq cpu ticks
            0 stolen cpu ticks
      7692136 pages paged in
      3859268 pages paged out
       113693 pages swapped in
       168684 pages swapped out
     16880824 interrupts
     50059693 CPU context switches
   1337795282 boot time
        33489 forks

How does disk cache work and what sort of files does it contain? User files such as documents and media files one is currently listening to? When does it go away (at shutdown, at logout, on closing the application that created it?...)

---

### Post by rng on 2012-05-24
I had converted standard swappiness of 60 to 10 and I found the swap being used much less often- a predictable response. Converting to 100 may have some special meaning and effect.

---

