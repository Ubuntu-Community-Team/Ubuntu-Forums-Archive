---
title: "Why is Ubuntu so slow?"
date: 2009-09-26
forum: General Help
---

### Post by Muiske on 2009-09-26
Yes, that's right... I can't do anything without at least 5 seconds of delay. Start Firefox? It takes a minute before the screen comes up. Open Nautilus? Before it has read all the files in any directory, a minute has passed. If I open up more than 5 tabs in a web-browser, the system becomes so slow that if I click something, more than a minute passes before something happens. Changing from tab to tab takes a wile too... the whole system feels "muddy" and lethargic.

Is something wrong with my system? Can anyone help?

My specs:
AMD 2500+
512 MB RAM
Nvidia 128 MB

---

### Post by DasEi on 2009-09-26
see top (or htop after installing) and check what eats your performance up

---

### Post by VMC on 2009-09-26
> **Muiske said:**
> Yes, that's right... I can't do anything without at least 5 seconds of delay. Start Firefox? It takes a minute before the screen comes up. Open Nautilus? Before it has read all the files in any directory, a minute has passed. If I open up more than 5 tabs in a web-browser, the system becomes so slow that if I click something, more than a minute passes before something happens. Changing from tab to tab takes a wile too... the whole system feels "muddy" and lethargic.

Is something wrong with my system? Can anyone help?

My specs:
AMD 2500+
512 MB RAM
Nvidia 128 MB

Now tell us what release of Ubuntu your running, did this just start or was it like this from the beginning, how many hard drives and are they RAID, any errors messages during boot-up.

From a terminal type dmesg and see if anything in there is the problem. Also from that terminal type top and see how much cpu% is being used and who is using it.

---

### Post by Bigneil on 2009-09-26
my last pc was similar specs to yours, and it ran ubuntu pretty fast. open up your system monitor and see if there is something stressing your cpu??

have you just installed ubuntu and this is happening from the offset, or did it run fine then start all of a sudden??



last time i had a system run like that for no reason, the Hard drive was shot.

i know this doesnt help much but give us more info and we might be able to help.

does your system run other operating systems ok?

---

### Post by adamant715 on 2009-09-26
Do you have a swap partition?

---

### Post by Bigneil on 2009-09-26
AHH hang on, have you just installed the latest version of ubuntu ??  how about you try installing the tried and tested long term support version first and see what happens, it might run smoother on an older system,  

hardy heron lts version 8.04  

worth a try,  ibex and jaunty  ( ubuntu 8.10 and 9,04)  didn't work too good on my old system.  but heron was ace. it is supported up till 2011 i think.


i could be barking up the wrong tree but if you have only just installed it you have nothing to loose by trying it again or burning a new disk of a different version and giving it a go. if you download an iso when you burn it to disk use a slow write speed.


i can only hope that im being helpful. it's what i would do.

---

### Post by Bigneil on 2009-09-26
also, make sure your drivers for the Nvidia video card are working and enabled.  some cards need to have thier drivers enabled manually. you may get a wee icon appear telling you that drivers are available but you have to download and enable them manually. i had to do this for my wireless card and also my nvidia 5 series pga card.!

---

### Post by credobyte on 2009-09-26
I think it was a bit harsh - I have exactly the same hardware and Ubuntu runs just fine. 
Have you tried to turn off desktop effects ( which may cause such a delay ) ?

---

