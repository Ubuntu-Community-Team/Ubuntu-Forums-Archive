---
title: "wrong resolution with ATI radeon 5450"
date: 2011-03-20
forum: General Help
---

### Post by slowwound on 2011-03-20
hi

i got a dell computer running ubuntu. it is equipped with an ATI radeon 5450, using a dell IN2010 1600x900 screen.

when i installed ubuntu, the resolution was just fine. then i installed the ATI driver, and from that moment on, i have that strange behaviour:

when i start ubuntu, the resolution seems set to 1440x900, but stretched to wide-screen mode, so the font is somehow blurry.
when i turn the monitor off and then on again, everything is just fine.

i have catalyst control center installed, and the resolution is set to 1600x900, but i still have the problem that i described.

by the way, the same was on windows...

---

### Post by coffeecat on 2011-03-20
> **slowwound said:**
> when i turn the monitor off and then on again, everything is just fine.

....

by the way, the same was on windows...

Sounds like the problem is in your monitor. There should be an 'auto' button on the monitor. Instead of switching it off and on, try pressing the auto button which will make the monitor retune to the graphics output.

By the way, if everything was working OK with the default open source "ATI" driver, why did you install the proprietary "fglrx" driver"?

---

### Post by slowwound on 2011-03-20
unfortunately, there is no auto-button, and nothing like that.
and if it is, then there are much more buttons to press to find it going through the menu.
so i just turn it on and off.

i went with the proprietary driver, because without it, there are no visual effects, so i thought the ATI driver might be better...

on windows, however, i managed to solve that problem, in a way that doesn't make sense to me, but that's another story (but i didn't change the drivers or something)
just wanted to say, that it can be done, somehow...

---

### Post by coffeecat on 2011-03-20
> **slowwound said:**
> 
i went with the proprietary driver, because without it, there are no visual effects, so i thought the ATI driver might be better...

No visual effects with the open source driver? Which version of Ubuntu are you using?

I know what you mean about hunting through the monitor menu. It's a pity that not all manufacturers give you an auto button.

---

### Post by slowwound on 2011-03-20
i'm using ubuntu 10.10
visual effects were disabled. i don't know what other stuff was not available with the open source driver, because a few hours after the install i got the ATI driver.

that dell monitor doesn't seem to be the best if you don't like trouble shooting :-)
but anyway, paid for it, and i'll try my best to make it work (but since i'm a linux newbie i can't do it on my own)

---

### Post by mr.farenheit on 2011-03-20
are you using the monitor option under the system menu or catalyst to change the resolution?

---

### Post by slowwound on 2011-03-20
mr. farenheit, i don't really understand what you mean ?!?

---

### Post by slowwound on 2011-03-24
today i did the automatic updates, and after that, everything starts just fine, with the correct resolution.

i don't know why, but it works fine now

---

