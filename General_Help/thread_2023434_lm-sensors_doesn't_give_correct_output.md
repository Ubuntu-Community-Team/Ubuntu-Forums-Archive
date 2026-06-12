---
title: "lm-sensors doesn't give correct output"
date: 2012-07-12
forum: General Help
---

### Post by Kols on 2012-07-12
Hey sportsfans!

So, a while ago, I installed lm-sensors, and when given the command
$sensors
it gave an output similar to this one;

# sensors
w83697hf-isa-0290
Adapter: ISA adapter
VCore:     +1.50 V  (min =  +0.59 V, max =  +0.06 V)
+3.3V:     +3.25 V  (min =  +0.56 V, max =  +2.05 V)
+5V:       +4.95 V  (min =  +0.91 V, max =  +0.05 V)
+12V:     +11.86 V  (min =  +1.46 V, max =  +0.06 V)
-12V:     -11.70 V  (min = -14.58 V, max =  -7.01 V)
-5V:       -5.20 V  (min =  -2.49 V, max =  -6.50 V)
V5SB:      +5.46 V  (min =  +0.00 V, max =  +0.86 V)
VBat:      +3.55 V  (min =  +0.26 V, max =  +1.09 V)
fan1:      3850 RPM  (min = 112500 RPM, div = 2)
fan2:      0 RPM  (min = 3461 RPM, div = 2)
temp1:     +33°C  (high =   +32°C, hyst =    +8°C)   sensor = thermistor
temp2:     +48.0°C  (high =   +80°C, hyst =   +75°C)   sensor = diode


Now, this is what I get when executing

$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +53.0°C  (crit = +100.0°C)
temp2:        +48.0°C  (crit = +82.0°C)

It seems to be using some kind of virtual device, but the temperature seems to be correct.
 
How do I restore the old output?

Please advice.

-Ole-Jørgen

---

### Post by Cheesemill on 2012-07-12
```
sudo sensors-detect
```

---

### Post by Kols on 2012-07-12
Thanks for answering!
Although I succeeded the wizard now, I did it during initial installation too.
It didn't solve my problem though, $sensors still give the above output.

Other suggestions?

---

### Post by QIII on 2012-07-12
So when you do sensors now, is the acpitz-virtual-0 bit *ALL* you are getting and nothing else?

---

### Post by Kols on 2012-07-12
> **QIII said:**
> So when you do sensors now, is the acpitz-virtual-0 bit *ALL* you are getting and nothing else?

That's correct. Same output as before;


$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +53.0°C  (crit = +100.0°C)
temp2:        +48.0°C  (crit = +82.0°C)

---

### Post by QIII on 2012-07-12
I'm still not clear.

Before, you were ONLY getting the long output and now you are ONLY getting the short output?

---

### Post by Kols on 2012-07-12
> **QIII said:**
> I'm still not clear.

Before, you were ONLY getting the long output and now you are ONLY getting the short output?

Yep, that's exactly the case. Before, I got the "long" output as in the opening post. Now on the other hand, even after completing the wizard over again, answering yes to all prompts (and getting, as I can recall, the same results), I get the "short" output.

---

### Post by QIII on 2012-07-12
Did you do 

```
sudo service module-init-tools restart
```

after doing sensors-detect before doing sensors?

---

### Post by miegiel on 2012-07-12
If what **[COLOR="DarkOrange"]QIII[/COLOR]** said didn't help, post output of:
```
sudo sensors-detect
```
and
```
cat /etc/modules
```
(in a code box please, use the **#** button in the post editor)

---

### Post by QIII on 2012-07-12
Can you give me some hardware info?

I just installed Xubuntu on a Toshiba Satellite for someone and I am getting the same behavior on that machine.

---

