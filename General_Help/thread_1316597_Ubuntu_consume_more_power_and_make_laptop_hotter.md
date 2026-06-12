---
title: "Ubuntu consume more power and make laptop hotter?"
date: 2009-11-06
forum: General Help
---

### Post by zey on 2009-11-06
i have installed ubuntu (9.10-karmic) on my laptop. i see it consume more power. my battery going down faster. and from sensors-applet, it shows that ther CPU temperature is high enough.

i compare it with windows XP.

is that something normal...???

or something wrong..??

or ubuntu is just not perfect yet??

---

### Post by SunnyRabbiera on 2009-11-06
Laptop battery management in linux can be flaky sometimes, some work better then others.
It all hangs on optimization, when windows is pre installed on a laptop it is optimized by who makes it.
What kind of computer you have?

---

### Post by P4man on 2009-11-06
Nothing is perfect and certainly no OS is.
But you can try this; install powertop

```
sudo apt-get install powertop
```

then run it as root

```
sudo powertop
```

copy / paste the results here so we can look in to it.

---

### Post by zey on 2009-11-06
BENQ joybook R46
DVD ROM and CD burner.
intel pentium dual core T4200 2.0 Ghz
2 GB memory.
250 gib HD.

what is the effect of sudo rm -rf ???

is that related with power consumtion and CPU temperature??

---

### Post by P4man on 2009-11-06
> **zey said:**
> BENQ joybook R46
what is the effect of sudo rm -rf ???

Who told you to run that ? It will wipe your harddisk. DO NOT use it.

---

### Post by aquavitae on 2009-11-06
sudo rm -rf is part of a very dangerous command that deletes anything. rm deletes, but sudo gives it root privileges so that it can delete anything. -rf forces it to delete all folders recursively.  The part that is missing is where it should delete.  If anyone gives you a command to run that looks anything like that, don't run it without being absolutely sure you know what it does.  You can always post the command on the forums to get other opinions on it!

As for the power consumption, have you checked the power settings, in the system menu?

---

### Post by 3rdalbum on 2009-11-06
Windows XP is an ancient operating system with very low system requirements (because it was made to run on completely obsolete computers); it will naturally use fewer resources than today's most powerful Ubuntu :-)

I'd check that you don't have any runaway processes using up lots of CPU time; check the System Monitor first. If there's nothing that's using lots of CPU power, then try Powertop and follow the suggestions provided by that program.

If you can hit single digits in the "wakeups-per-second" figure with everything idle, then you're doing well.

---

### Post by zey on 2009-11-06
i have installed powertop. this is my screenshot.

---

### Post by P4man on 2009-11-06
> **zey said:**
> i have installed powertop. this is my screenshot.

That looks pretty okay to me, assuming you were doing something (even touching the mouse) or running something in the background.  powermanagement for your cpu is certainly working.

If you close all open apps and dont touch the machine for 10 seconds, does the C3 % get closer to 100% ?

---

### Post by aquavitae on 2009-11-06
> **3rdalbum said:**
> Windows XP is an ancient operating system with very low system requirements (because it was made to run on completely obsolete computers); it will naturally use fewer resources than today's most powerful Ubuntu :-)

Not necessarily.  I find that modern, powerful ubuntu generally uses less resources than ancient XP.  Especially since the linux devs do actually try to optimise their code and improve performance.

---

### Post by 3rdalbum on 2009-11-06
It seems a bit high - mine is around 130-150 with Opera open.

---

### Post by 3rdalbum on 2009-11-06
> **aquavitae said:**
> Not necessarily.  I find that modern, powerful ubuntu generally uses less resources than ancient XP.  Especially since the linux devs do actually try to optimise their code and improve performance.

I take back the word "naturally" :-)  The latest Syllable uses fewer resources than Windows XP. The latest Haiku is less power-hungry than XP. You can still run a basic NetBSD system on 16 megs of RAM.

But Windows XP is designed specifically to work with older processors, because when it was released, they were the latest new processors!

---

### Post by seenthelite on 2009-11-06
> **3rdalbum said:**
> I take back the word "naturally" :-)  The latest Syllable uses fewer resources than Windows XP. The latest Haiku is less power-hungry than XP. You can still run a basic NetBSD system on 16 megs of RAM.

But Windows XP is designed specifically to work with older processors, because when it was released, they were the latest new processors!

When XP was released in 2000 it ran easily on those old computers but if you have SP3 and all the latest updates its a totally different situation.

---

