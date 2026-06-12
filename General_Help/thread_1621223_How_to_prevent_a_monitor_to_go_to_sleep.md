---
title: "How to prevent a monitor to go to sleep"
date: 2010-11-14
forum: General Help
---

### Post by DeMus on 2010-11-14
Hi,
I have a Samsung Syncmaster P2370 23" full HD monitor and don't want it to give me black screen after several minutes of doing nothing with the computer.
I turned off the screensaver and in the powermanager I chose to Never put the monitor to sleep.
Still, after several minutes, the screen goes blank. Is there another setting in Linux responsible for this or could it be the monitor itself who is doing this?

---

### Post by amauk on 2010-11-14
possibly it's the monitor itself
most monitors have an onscreen display menu, see if there's anything in there about it

---

### Post by DeMus on 2010-11-14
> **amauk said:**
> possibly it's the monitor itself
most monitors have an onscreen display menu, see if there's anything in there about it

I looked in the monitor menu but can't find anything related to this.
When I bought it there was a CD with a windows driver but of course no Linux driver. I can have a look at the Samsung website if I can find something there.

---

### Post by mc4man on 2010-11-27
In the past where one particular monitor went to sleep independent of screen saver/power management settings I used to be able to stop by - 

Setting the time to idle in 'screen saver' to less than the time the monitor was going to sleep. Then setting power management to 'never'.
I don't think things work quite the same now - power management kicking in about 1 min after computer considered 'idle'
So..

The other way that worked for sure was to add a section to xorg.conf (added at end, 1 space from last section

```
Section "ServerFlags"
        Option	"BlankTime"	"0"
        Option	"StandbyTime"	"0"
        Option	"SuspendTime"	"0"
        Option	"OffTime"	"0"
EndSection
```

---

### Post by DeMus on 2010-11-28
> **mc4man said:**
> In the past where one particular monitor went to sleep independent of screen saver/power management settings I used to be able to stop by - 

Setting the time to idle in 'screen saver' to less than the time the monitor was going to sleep. Then setting power management to 'never'.
I don't think things work quite the same now - power management kicking in about 1 min after computer considered 'idle'
So..

The other way that worked for sure was to add a section to xorg.conf (added at end, 1 space from last section

```
Section "ServerFlags"
        Option	"BlankTime"	"0"
        Option	"StandbyTime"	"0"
        Option	"SuspendTime"	"0"
        Option	"OffTime"	"0"
EndSection
```

Thanks mc4man, but I managed to find another solution in an other thread.
With "xset -dpms" it is possible to switch off dpms
With "xset s noblank" it is possible to stop the screen from being blanked. Add this to .bashrc and make sure the file is executable.
Thanks anyway for giving your reaction to this older thread, I really appreciate it.

---

