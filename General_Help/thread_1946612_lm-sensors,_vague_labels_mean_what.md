---
title: "lm-sensors, vague labels mean what?"
date: 2012-03-25
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-03-25
I installed lm-sensors and it gives me  4 temperatures but only one of them, one for a hard drive, is properly labeled. The other 3 are temp1, temp2, and temp3. Is there any way to tell what those are? There are some equally vague inI where I is an integer I'm curious about.

---

### Post by mcduck on 2012-03-25
Not really, lm-sensors is simply reading raw data from any sensor chips it recognises on your computer, but that data doesn't include any information about what each sensor is actually used for on your motherboard.

The best way is to simply look at the data and try to evaluate if it seems reasonable or not, and what sensor each reading might fit. If you can check temperatures or other sensor readings in your computer's BIOS, then comparing with those values  would be a good way to go.

As a hint, if you make the system do some heavy work, the CPU core sensor would react very quickly to increases and decreases in workload, and should have the highest value. 
CPU socket temperature reacts almost as quickly, and has either the same or a degree or two lower value.

Chipset temperature sensor reacts much slower to the workload, and shouldn't reach as high temperatures as the CPU sensors do.

And finally, any case/ambient sensors should give a relatively stable reading more or less around the ambient room temperature where the computer is located (of course depending on how god ventilation your case has).

---

### Post by Bobhuber on 2012-03-25
> **Dreamer Fithp Apprentice said:**
> I installed lm-sensors and it gives me  4 temperatures but only one of them, one for a hard drive, is properly labeled. The other 3 are temp1, temp2, and temp3. Is there any way to tell what those are? There are some equally vague inI where I is an integer I'm curious about.
Following up on mcduck's post after you figure out what they are (BIOS is a good place to start if it has a hardware screen) you can actually change the names you are seeing with the sensors command by renaming (Example > temp1 to Sys Temp) in the /etc/sensors3.config. Sensors will give you the name of the chipset to modify in the file. 
Heres an example of mine.
```
chip "f71889ed-*" 
    label fan1 "Cpu Fan"
    label fan3 "Sys Fan"
    label temp3 "Sys Temp"
    compute temp1 @+7,@-7
```

---

### Post by Dreamer Fithp Apprentice on 2012-03-25
Thanks, guys. I'll come back and mark this solved as soon as I've actually made that work. Sounds like the answer.

---

