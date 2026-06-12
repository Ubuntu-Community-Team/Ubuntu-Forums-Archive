---
title: "Monitor resolution"
date: 2005-02-27
forum: General Help
---

### Post by matgorb on 2005-02-27
I have an "old" 15" monitor from 1998 FUNAI 15GD, and it is not recognize by the Ubuntu installer, which is not really a problem by itself as I ran xf86config and made it work. However, I got the frequency settings from the Internet, from a page which said that the maximum resolution is 929x696, but I tried it a 1024x768, just to see, and it's working fine, I was thinking that the limitation of a screen in term of frequency and resolution will do what I use to get with other screen, no display because of some kind of out of range frequency. But the monitor worked just fine for 2 weeks now, with no apparent problem, and I can go higher.
As i said it is an old monitor, so it is not a problem to change it if it fails, but is it really damaging it, or do I just get wrong specs???

mat

---

### Post by Wim Sturkenboom on 2005-02-28
I suppose you've modified the HorizSync and VertRefresh in your X configuration file with the info you found on the internet.
If so, there is no issue. X will stay within those limits and your monitor will not get damaged.

I've checked two sites, and they gave the same info, so I assume that the below is correct:
30-70kHz   50-120Hz

---

### Post by matgorb on 2005-02-28
Yes I did that exactly, but I'm not suprised by the frequency, more with the resolution, as you must have seen on thos website, the max is below 1024x768, and still I can run it with no apparent problem at 75Hz, and even 85Hz. I have no real problem doing so, as this screen is going to be replaced at some point, but is that a normal behaviour for the screen to accept higher resolution, I mean, where is exactly the limitation in the number of pixel it can display?

---

### Post by Wim Sturkenboom on 2005-03-01
The **electronics** of CRT screens don't know about resolution. The resolution is determined by the mask (a metal plate with apertures) that is located in front of the phosphor.
```
[FONT=FixedSys]


_________________
__  __  __  __  __
   ^
   |

       M   P
        |    |
---->        |
        |    |
             |
        |    |
             |
        |    |
[/FONT]
```
A beam of electrons (the arrow above) goes horizontal from left to right over your screen. It will either hit the mask or go through the mask and hit the phosphor. When it hits the phosphor, it will glow (what you will see as light).
The more holes in the mask, the higher the resolution.

---

### Post by Wim Sturkenboom on 2005-03-01
The **electronics** of CRT screens don't know about resolution. It generates a beam of electrons that hit the phosphor on your screen. The resolution is determined by the mask (a metal plate with apertures) that is located in front of the phosphor.

```
[FONT=Fixedsys]
__________________ P
__  __  __  __  __ M
   ^
   |
   |
   B
[/FONT]
```A **b**eam of electrons (the arrow above) goes horizontal from left to right over your screen. It will either hit the **m**ask or go through a hole in the mask and hit the **p**hosphor. When it hits the phosphor, it will glow (what you will see as light). If a lot of electrons hit the phosphor, it will be bright and if a few hit the phosphor, it will be not as bright).
Next the beam moves back to the left and a little down and the process repeats. This continues till it reaches the bottom after which the beam goes back to the top and the process is repeated.

From this, I hope it's clear that the more holes there are in the mask, the higher the resolution in a CRT.

Your monitor supports a max of 929x696 which is the number of holes in the mask.

I've left out the info for colour monitors, although the principle stays the same, but there are three beams and three different phosphors.

---

