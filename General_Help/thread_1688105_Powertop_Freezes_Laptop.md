---
title: "Powertop Freezes Laptop"
date: 2011-02-15
forum: General Help
---

### Post by ngrieb on 2011-02-15
Hi All,
I was reading the forum yesterday, and saw a thread about powertop. Needless to say I tried it on my Toshiba NB305, and thought it might be good to see if I could also get better power usage from my wife's Toshiba A665. The problem is that when I run it on her laptop, it just totally hangs the system, and the caps lock light just sits there blinking. I am not sure why. Is it not designed for x64 systems? Any ideas, or similar problems? I think this laptop has an Intel i5 540M processor, and I am running Ubuntu 10.04x64 kernel version 2.6.32-29-generic.
Thanks in advance.

---

### Post by koleoptera on 2011-02-19
Yeah me too, same problem..I run Ubuntu 10.04 64 bit on an Asus U31F machine...When I start powertop as sudo the system freezes.
When I ran it simply, not sudo, it works with minimum functionality though..
Any reasons why this happens?

---

### Post by Joe_Speedboat on 2011-02-23
I have the same problem on my Asus P31F. It freezes the system completely when running powertop as su.

---

### Post by ngrieb on 2011-02-25
Might have something to do with the quadcore architecture of this laptop. There was a huge post a few months back about random freezing caused by multicores. What procs are you running? 

It was just an afterthought anyways, I really needed it for my NB305 as I am unable to dim the backlight due to some odd kernel glitch (and kernel recompilation seems a bit radical for this one problem). The A665 is much more graphically capable and runs well already. Just thought I could stretch the battery life a bit more than with Windows 7.

---

### Post by koleoptera on 2011-03-06
Same problem here..
Asus P31F, have tried till now 10.04 32bit-10.04 64bit-10.10 32bit and now 10.10 64bit in all systems powertop freezes the sytem when run as sudo..

I am not sure if it has to do with the architecture..I would be interested in seeing if this thing works so if anybody it would be a pleasure..

---

### Post by Gr33nGapion on 2011-04-09
Same problem here with my desktop which runs an Intel i5. Works great on my Eee netbook though..

---

