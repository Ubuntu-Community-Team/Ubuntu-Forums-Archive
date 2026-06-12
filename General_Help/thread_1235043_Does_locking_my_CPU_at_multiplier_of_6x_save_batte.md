---
title: "Does locking my CPU at multiplier of 6x save battery power?"
date: 2009-08-08
forum: General Help
---

### Post by s3a on 2009-08-08
Does locking my (Intel Pentium-Dual Core) CPU with the CPU Frequency Scaling Monitor at a multiplier of 6x save battery power or not? I ask because there are two arguments one of which is speedstep is better because it overclocks itself so that it can deal with the process faster and consequently go back to idle faster but when it is locked at a 6x multiplier, it does not reach a state of overclocking which itself uses more power.

My goal is to save as much power as possible so that my computer can last long for school purposes. Most of the time, I will be using non-heavy applications such as gnote, openoffice.org or xournal.

Any input would be greatly appreciated as always!
Thanks in advance!

---

### Post by Nepherte on 2009-08-08
cpufreq can automatically tune up or down the frequency when it needs more horse power. In my case it's more tuned down than up so it's hardly necessary to lock it at x6.

---

### Post by mcduck on 2009-08-08
With modern CPU's the decrease in power usage when the CPU is idle is so great when compared to effects different multipliers have to power use that you'll get best results by doing the work as quick as possible to get back to idle state.

So using the "ondemand" governor will save you more power than any other option, as that allows your CPU to spend more time idle.

Anyway, if you want to do something that really saves noticeable amounts of battery time, drop your display's backlight brightness as low as possible. Even dropping from 100% to 80% should have a noticeable effect.


(by the way, speedstep doesn't ever *overclock* the CPU, as overclocking means going *beyond* your CPU's intended frequency. The max speed you get with speedstep is your CPU's default speed, and speedstep just drops to lower speeds to save power.)

---

### Post by dcstar on 2009-08-08
> **mcduck said:**
> With modern CPU's the decrease in power usage when the CPU is idle is so great when compared to effects different multipliers have to power use that you'll get best results by doing the work as quick as possible to get back to idle state.

So using the "ondemand" governor will save you more power than any other option, as that allows your CPU to spend more time idle.
........

Setting the system to "Powersave" will lock the CPU at its lowest possible clock rate and save more power than Ondemand - that is why that setting exists.

Having a CPU spike its clock to save 0.2 seconds on delivering a screen will do little to make a user more productive but use more power than leaving things at their minimum.

---

### Post by 3rdalbum on 2009-08-08
> **dcstar said:**
> Having a CPU spike its clock to save 0.2 seconds on delivering a screen will do little to make a user more productive but use more power than leaving things at their minimum.

Intel disagrees - if moving to a higher performance level saves 0.2 seconds, then that means that the CPU can go into sleep state for 02 seconds longer, saving power.

If you're into saving power, then you MUST install the Powertop program. When you run it in a terminal, it will give you power saving suggestions that you can usually apply just by hitting a key. You can also see what kernel modules and programs are keeping your CPU active; you can change what programs you run to save power, and you could even remove or blacklist any kernel modules that you don't need and that are waking your CPU.

There are also power saving suggestions at the [www.linuxpowertop.org](www.linuxpowertop.org) and [www.lesswatts.org](www.lesswatts.org) websites.

---

### Post by mcduck on 2009-08-09
> **dcstar said:**
> Setting the system to "Powersave" will lock the CPU at its lowest possible clock rate and save more power than Ondemand - that is why that setting exists.

Having a CPU spike its clock to save 0.2 seconds on delivering a screen will do little to make a user more productive but use more power than leaving things at their minimum.

At the lowest possible frequency you'll be using considerably more time to do the same task.

Assuming you have a task that takes  0.1 seconds to do at full speed. So at half speed it'll take 0.2 seconds. Now, you have two options. 0.1 seconds of work at full speed plus 0.1 seconds sleeping with almost zero power usage. Or spending the whole 0.2 seconds working, with power usage almost the same as if you'd run at full speed..

And the effect on user productiveness has nothing to do with saving power. For user 0.2s may be short time, but for your CPU it's very long time.

The settings exist because older CPU's didn't save as much power by dropping to sleep state, and because they might still be useful in some special situations. For example games will keep your system running at max speed as long as you keep on playing, so unlike with normal working tasks doing the job quicker won't get the CPU back to sleeping any quicker. If you were playing a game on battery power you could save power by forcing your CPU to stay at low frequency.

---

### Post by P4man on 2009-08-09
Just to repeat what the others said: "hurry up and go to sleep" saves more power than a lower multiplier, so keep the governor on "on demand".

And install powertop:

> sudo apt-get install powertop
sudo powertop

---

