---
title: "Speakers not giving any sound output (headphones working OK)"
date: 2010-07-08
forum: General Help
---

### Post by Mthbk1 on 2010-07-08
Speakers not giving any sound output (headphones working OK). Am I missing something?
Also while shutdown, my system is giving 3 beeps in succession (from ibuilt speaker)

---

### Post by Gregorybekkers on 2010-07-08
What kind of sound card and chipset do u have?
cause there are some difficulties with some chipsets that can be solved by adding a file.

---

### Post by Dustin2128 on 2010-07-08
hm, simplest answer is usually the correct one. Go to a terminal and type 'alsamixer' and make sure the speaker's volume is above 0. Happened to me more than once.

---

### Post by Mthbk1 on 2010-07-08
> **Dustin2128 said:**
> hm, simplest answer is usually the correct one. Go to a terminal and type 'alsamixer' and make sure the speaker's volume is above 0. Happened to me more than once.
 
Thanks for reply, all the levels are above 0.
@Greggory I am using ubuntu 9.04 with Intel G45 express chipset. (uses sigmatel drivers with windows)
I have used ubuntu for more than 4.5 years now but this kind of problem, I've encountered for the first time :|

---

### Post by lidex on 2010-07-08
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

Can you give some history? Is this an upgrade? Did it work before? When did it stop working, etc?
Your previous reply states you're using jaunty, but your panel says karmic.

---

