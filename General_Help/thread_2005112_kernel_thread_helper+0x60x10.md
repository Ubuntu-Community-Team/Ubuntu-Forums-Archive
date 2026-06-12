---
title: "kernel_thread_helper+0x6/0x10"
date: 2012-06-16
forum: General Help
---

### Post by goruzedri on 2012-06-16
Hello,
I am new at Ubuntu and I wanted to try it because I was having troubles with Windows Vista; to be more specific, in windows vista i was working as always when suddenly it appeared a blue screen with a legend I was unable to read because of the short time it appeared on screen and it rebooted making the same process. I made a clean installation of ubuntu in my laptop, at the start it seemed to work well but nowadays when I try to turn it on for start working it just don't boot in, a black screen with lots of codes I do not understand appear and it won't do anything. Sometimes it boot in but suddenly another black screen with more codes appear saying "Fixing recursive fault but reboot is needed!" so I turn it off and when I turn it on the kernel thread helper screen comes up and it does not boot. I have been searching on the internet for some information and I have foun some things about changing the acpi option to off,but when I do it the kernel message do not appear but the screen remains in black and it does nothing, I have also tested memory from BIOS and from the memtest that comes with ubuntu but it says there are no problems.
The laptop is hp Compaq6720s with an Intel Celeron.
Beforehand I am thankfull for your answers,
goruzdri
P.D. I'm attaching a picture of the screen with the kernel thread helper code.

---

### Post by matt_symes on 2012-06-17
Hi

In the first instance, try booting with the kernel boot flag

```
acpi=off
```

Kind regards

---

### Post by goruzedri on 2012-06-17
Thank you, but as I have mentioned before, I have already done that. If you have another suggestion for me to do, I will really appreciate that. Thank you

---

### Post by matt_symes on 2012-06-17
Hi

> **goruzedri said:**
> Thank you, but as I have mentioned before, I have already done that. If you have another suggestion for me to do, I will really appreciate that. Thank you

I wanted to make sure you had definitely tried the acpi=off flag in the kernel boot parameters as i was a tiny bit unclear about your first post. 

From the stack trace, the problem does look it may be an ACPI problem. 

Have you tried any of the other acpi=... boot flags ?

Is there a BIOS update for your PC ?

Kind regards

---

