---
title: "Where can i control the FAN of my VGA Slot ?"
date: 2011-01-01
forum: General Help
---

### Post by Trolen on 2011-01-01
The Linux have automatically found drivers for my ATI 4850.The only option that i don't see inside the control center of the Linux is where can i control the FAN of my VGA Slot ? 

Any ideas ?

---

### Post by corrytonapple on 2011-01-01
Hmm, fan control for a graphics card. If so, the drivers should have it where it does that by itself.  I have never used an aftermarket card, so I would not know.  If it is for a slot itself and on the card, then it would have it's own drivers.  Fan control is an issue we all face.  It should be OK, just watch it.  Normally the hardware will turn the fan on itself if the OS doesn't do it for you.

---

### Post by Trolen on 2011-01-02
Yeah,but i want to clock my VGA again,because to some games it opperates much much better.

---

### Post by corrytonapple on 2011-01-02
Again, I am no expert at this, so I am not positive.  The hardware should bring the fan to a correct speed for the clock speed.  You might want to look in the Software Center to see if there is anything that may help you.

---

### Post by Trolen on 2011-01-02
Yeah i have even searched inside the Advanced mode,but didn't find anything that could help me.

---

### Post by Frogs Hair on 2011-01-02
There is OC software for Nvidia cards on Linux , but I can't find any for ATI. You should find out if your card supports fan speed control. Maybe your Google skills will be better than mine today. Its nice to have something like speedfan for overclocking. You may be able set fan speed in the bios.

---

### Post by Trolen on 2011-01-03
Yeah,but i didn't find anything.

ATI on window's has Overdrive.Here it doesn't have.

---

### Post by cascade9 on 2011-01-03
> **Frogs Hair said:**
> There is OC software for Nvidia cards on Linux , but I can't find any for ATI. You should find out if your card supports fan speed control. Maybe your Google skills will be better than mine today. Its nice to have something like speedfan for overclocking. You may be able set fan speed in the bios.

There is rovclock. AFAIK, it doesnt work with evergreen (5XXX and 6XXX) yet, and I'm not even that sure about it working with R700 (HD 4XXX, some 3XXX) and R600 (HD 2XXX, some 3XXX). 

It also doesn thave fan control, so it wont help the OP.

---

### Post by Trolen on 2011-01-03
We need the FAN Control for the Gaming/OC.

---

### Post by corrytonapple on 2011-01-03
> **Trolen said:**
> Yeah,but i didn't find anything.

ATI on window's has Overdrive.Here it doesn't have.
I am not sure, but you might be able to run that program in Wine.
It is always worth a shot.

---

### Post by cascade9 on 2011-01-03
> **Trolen said:**
> We need the FAN Control for the Gaming/OC.

The fanspeed should be dependant on temps, so you shouldnt need to bump the fanspeed for overclocking. 

If you really want to chnage fanspeed, and rovclock wont do it,  then you might have to do things the hard way using Radeon BIOS editor.

[http://www.techpowerup.com/downloads/1892/TechPowerUp%20Radeon%20Bios%20Editor%20v1.26.html](http://www.techpowerup.com/downloads/1892/TechPowerUp%20Radeon%20Bios%20Editor%20v1.26.html)

---

### Post by Trolen on 2011-01-03
OK thank you.I will search for more information and i think i will do it.

---

### Post by cascade9 on 2011-01-03
No problem. 

I've got to warn you that overclocking by changing video card BIOS settings is more dangerous than from software tools.

---

### Post by Trolen on 2011-01-03
OK I  will try my best :)

---

