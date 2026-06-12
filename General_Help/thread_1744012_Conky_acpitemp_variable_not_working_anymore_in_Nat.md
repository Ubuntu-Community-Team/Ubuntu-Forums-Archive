---
title: "Conky: acpitemp variable not working anymore in Natty?"
date: 2011-04-30
forum: General Help
---

### Post by Arcademus on 2011-04-30
Hey,

Long story short: upgraded to Natty via reformat and fresh install, installed Conky, and reused my old .conkyrc file. Whereas the CPU temp displayed just fine in Maverick, Conky returns a permanent "0" value in Natty.

The relevant line from my .conkyrc file:
```
TEMP: ${alignr}${acpitemp}  C
```

I've tried installing and "sudo dpkg reconfigure"-ing lm-sensors and acpi, and rebooting afterwards, with no effect.

Any and all help appreciated, thanks in advance.

---

### Post by craig_ on 2011-04-30
Did you see [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=609745](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=609745) ?

---

### Post by Arcademus on 2011-04-30
Thanks for the reply. I assume that means there's nothing that the user can do on his/her end to rectify this situation?

---

### Post by solitaire on 2011-04-30
you need to change your .conkyrc and swap out $acpitemp
with:
${hwmon temp 1}

---

### Post by speedwell68 on 2011-04-30
> **solitaire said:**
> you need to change your .conkyrc and swap out $acpitemp
with:
${hwmon temp 1}

Thanks, I have been have the same problem as the OP with acpitemp in Natty and your fix worked perfectly.

---

### Post by Arcademus on 2011-05-01
Yep, that solves the problem. Thanks!

---

### Post by vampiretto on 2011-05-06
> **solitaire said:**
> you need to change your .conkyrc and swap out $acpitemp
with:
${hwmon temp 1}

very very very thanks !!! :D:popcorn:

---

### Post by solitaire on 2011-05-06
If you install or run "sensors" in terminal you'll get a readout of all the temp sensors in your machine.

Change the "1" to what ever is the most appropriate.

You may have to run it a few times under different loads to pick the correct sensor to display in Conky.

---

