---
title: "Lucid, Lenovo G530 Wont Idle."
date: 2010-05-05
forum: General Help
---

### Post by jamadei on 2010-05-05
Hi I have a Lenovo G530 4446-23u. For some odd reason I'm having really high number of Wakeups from Idle when I'm running powertop it's almost reached 40,000.. I could use some serious help with this. My fan seems to never shut off. I've attached my terminal running Powertop so you can see. If you need anything else from me let me know. Thanks

---

### Post by dino99 on 2010-05-05
install hdapsd, tp-smapi-dkms, tp-smapi-source, module-assistant with synaptic

then: sudo update-initramfs -u

sudo grub-mkconfig && update-grub

---

### Post by jamadei on 2010-05-05
> **dino99 said:**
> install hdapsd, tp-smapi-dkms, tp-smapi-source, module-assistant with synaptic

then: sudo update-initramfs -u

sudo grub-mkconfig && update-grub

What does this do sir?

---

### Post by jamadei on 2010-05-05
> **dino99 said:**
> install hdapsd, tp-smapi-dkms, tp-smapi-source, module-assistant with synaptic

then: sudo update-initramfs -u

sudo grub-mkconfig && update-grub

This is stuff for Thinkpads? I do not have a thinkpad.

---

### Post by dino99 on 2010-05-05
its specific packages for Lenovo

need to install them then config the system

i suppose you know how to find synaptic (system admin synaptic)

---

### Post by jamadei on 2010-05-05
> **dino99 said:**
> its specific packages for Lenovo

need to install them then config the system

i suppose you know how to find synaptic (system admin synaptic)

yeah I do. I'll give it a whirl but I dont think it has to do with the high wakeups from idle. I believe this is a deeper issue within the Kernel.

---

### Post by dino99 on 2010-05-05
> **jamadei said:**
> This is stuff for Thinkpads? I do not have a thinkpad.

as you might know, thinkpads has been sold by IBM to Lenovo, so thinkpads=lenovo

---

### Post by dino99 on 2010-05-05
> **jamadei said:**
> yeah I do. I'll give it a whirl but I dont think it has to do with the high wakeups from idle. I believe this is a deeper issue within the Kernel.

hdapsd modify the buil-in module of default kernel, thats why you need it

---

### Post by jamadei on 2010-05-05
> **dino99 said:**
> as you might know, thinkpads has been sold by IBM to Lenovo, so thinkpads=lenovo

Yup I know that. But it's a Lenovo G530. not a Lenovo Thinkpad Sir. I installed everything so now what should i do?

---

### Post by jamadei on 2010-05-05
> **dino99 said:**
> hdapsd modify the buil-in module of default kernel, thats why you need it

Yeah, that didn't do anything. the number of wakeups-from-idle in powertop are extremely high.

> 


Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (30.6%)         2.17 Ghz     8.3%
polling           0.0ms ( 0.0%)         1.67 Ghz     0.0%
C1 mwait          0.0ms ( 0.0%)         1333 Mhz     2.8%
C3 mwait          0.0ms (69.4%)         1000 Mhz    88.9%


Wakeups-from-idle per second : 31792.7  interval: 0.1s
no ACPI power usage estimate available

Top causes for wakeups:
  38.3% (  inf)   [kernel scheduler] Load balancing tick
  21.7% (  inf)   chromium-browse
  15.0% (  inf)   [extra timer interrupt]
   8.3% (  inf)   rhythmbox
   5.0% (  inf)   xchat
   3.3% (  inf)   gnome-terminal


I'm alittle concerned with '[kernel scheduler] Load balancing tick" it always seems high.

---

### Post by dino99 on 2010-05-05
> **jamadei said:**
> Yup I know that. But it's a Lenovo G530. not a Lenovo Thinkpad Sir. I installed everything so now what should i do?

watch the differences  :p

good info can be found into .Xsession-errors (/home, unhide the file into menu) and: system admin log viewer

---

