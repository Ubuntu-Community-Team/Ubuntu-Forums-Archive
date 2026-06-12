---
title: "Windows won't start or reinstall"
date: 2010-11-06
forum: General Help
---

### Post by rhuse on 2010-11-06
Hi.
I'm am new to the forum (I might have been here a couple a years ago when I first installed ubuntu). I just installed ubuntu on my laptop a couple a days ago and all ran well, decided to upgrade to xubuntu and now I get a BSOD everytime I try to boot into windows and a the computer just shuts off when I try to reinstall. I realise that it will be hard for you guys to fix the error but hopefully you can at least help me run some tests to figure out what is wrong.

More details:
1. I hadn't used linux for a couple of year and I wanted to dip my toes again.
2. I installed ubuntu 10.04 via the wubi installer and booted right into it and everything ran great.
3. I was displeased with some minor (gnome)things and needed to do some work so I booted into Vista and forgot about ubuntu for a couple of days.
4. Tonight I started to look into gnome and xfce more and decided to try xubuntu.
5. First i ran a full scan with Microsoft Security Essentials and it found some virus and prompted me to reboot. (I don't remember the virus-name but I believe it was classified as a rootkit)
6. I restarted and booted into ubuntu to follow this guide to install xfce:[http://psychocats.net/ubuntu/xubuntu](http://psychocats.net/ubuntu/xubuntu)
7. I decided I didn't like that desktop environment either (I guess I have changed, they used to be my favorites)
8. I tried to boot into vista again only to get a BSOD (that goes away so fast it is impossible to read) when the loading animation is showing.
9. I guessed I screwed something and decided I needed a reinstall anyway so I plugged in the recovery-cds only to find the computer shutting down during the loading of the reset software.
10. Hoping my computer is just a little warm I let it cool down and try again and the loading goes on for a litte longer but eventually the computer shuts down.
11. I try an old XP-cd and the computer shuts down again.
13. I try to run a grub(?) memory test and the computer shuts down halfway.
12. I boot into xubuntu again to write this.

Laptop
Fujitsu Amilo pro v3405
Vista Pro

I know my computer runs hot some times and infact I belive that my last HD gave up due to that but this time it does not seem to be the harddrive. So I'm thinking the RAM but xubuntu runs fine? What else could it be? Are there any tests I can run from xubuntu to check the hardware?  Is there something else I should be checking? Can it be that the CD/DVD is producing to much heat?

Right now I just wanna factory reset to Vista so I can get on with my work and leave the OS experimenting to another time.

---

### Post by rhuse on 2010-11-07
As a strange turn of events, after a nights sleep, I had no problem booting into Vista. Can it be that the computer cooled down? If so, what type of problem does that indicate?

I concluded that the problem isn't the RAM. I have two RAM-sticks  and tried booting up with just one of them in the computer last night and got the exact same problem. (I tried both sticks)

The problem isn't solved per se but I am happy being able to boot up Vista again to complete my work and I won't experiment more until it is done. Maybe I should go with a standard install of ubuntu the next time and skip wubi.

---

### Post by Mark Phelps on 2010-11-07
If my PC was running so hot that it shut down ... I'd be more concerned about THAT than about which kind of Ubuntu installation I was running.

If your machine is running so HOT in Ubuntu that you have to let it cool down before it will boot properly again ... you're damaging your machine!

What good is running a free OS if it ends up burning up your machine in the process?

But, it's your PC -- your choice.

And, BTW, if it's overheating in Ubuntu, it's not going to matter whether it's  Wubi installation or separate partition -- it will still overheat, regardless.

---

### Post by rhuse on 2010-11-07
> **Mark Phelps said:**
> If my PC was running so hot that it shut down ... I'd be more concerned about THAT than about which kind of Ubuntu installation I was running.

If your machine is running so HOT in Ubuntu that you have to let it cool down before it will boot properly again ... you're damaging your machine!

What good is running a free OS if it ends up burning up your machine in the process?

But, it's your PC -- your choice.

And, BTW, if it's overheating in Ubuntu, it's not going to matter whether it's  Wubi installation or separate partition -- it will still overheat, regardless.


I think you misunderstood me. First of all, Ubuntu was and still is running fine. In fact, yesterday it was pretty much the only thing running at all.

I had (or still have, I haven't restarted my machine since I managed to boot into windows) two problems:

1. Yesterday when I booted Vista I got a BSOD during the loading of the OS. My best guess is that it had something to do with the virus MSE removed or maybe, just maybe, some driver xubuntu installed.

2. When I tried to boot from a cd (XP or vista) or tried to run the memtest one can chose in grub my computer just shut of. I concluded that this must be due to some heating problem becasue the only time I have experiencing something similar was when I accidently covered the fan by having my laptop on a soft surface and it got extemely warm.

BTW: it isn't a RAM problem. I have two sticks of RAM and the problem remained yesterday when I tested the two sticks seperatly (removed one at the time and tried to boot). So I still have no clue what the problem can be but I am reliefed being back in Vista (I need it for my work) and I will probably just hope that it keeps working for the duration of the projekt I am working on (2 weeks) and then I'll look into reseting the machine all together.

---

