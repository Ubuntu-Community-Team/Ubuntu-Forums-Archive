---
title: "How to slow down the fan?"
date: 2012-06-23
forum: General Help
---

### Post by Toxic Tom on 2012-06-23
I am running an ubuntu server in my bedroom and the fan is a bit annoying. It seems to spin at a constant rate, regardless of the temperature of the computer. I ran apci -t and it says the temperature is 18 degrees C, so is it ok to slow down the fan? How do I do it?

---

### Post by Paqman on 2012-06-23
Which fan is it? CPU or GPU? If it's the GPU what type is it, and which driver are you using?

---

### Post by Toxic Tom on 2012-06-23
It's the CPU fan

---

### Post by Redblade20XX on 2012-06-23
> **Toxic Tom said:**
> It's the CPU fan

Have you looked into the BIOS for any fan control capabilities such as thermal trip points?

Usually they are located in some advance menu of your BIOS.

-Red

---

### Post by Paqman on 2012-06-24
Make sure it's plugged into the right header on the mobo, and look for a setting in BIOS to enable PWM (Pulse Width Modulation, which allows it to match fan speed to temp).

What temp is the CPU at, and as Redblade20XX suggests, compare that to what the BIOS settings are at. You might have an heat problem, is this an old machine that you've turned into a server?

---

### Post by Toxic Tom on 2012-06-24
Its not that old but it feels warmer than 18c.

I'll try and have a look in the BIOS, thanks!

---

### Post by Paqman on 2012-06-24
BIOS should tell you exactly how hot it is, just touching the heat sink isn't very accurate unless you have calibrated hands and can do a lot of maths.

---

### Post by Toxic Tom on 2012-07-04
OK, so BIOS says the cpu temp is 38 degrees C. I found a setting called smart fan but that has been enabled the whole time. No other settings on there seemed to be relating to the fan, so I think the problem is in ubuntu (it worked fine with windows before).

---

