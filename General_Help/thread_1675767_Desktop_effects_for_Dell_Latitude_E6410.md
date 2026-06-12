---
title: "Desktop effects for Dell Latitude E6410"
date: 2011-01-26
forum: General Help
---

### Post by eogorma on 2011-01-26
Hi,

I recently purchased a Dell E6410 with an Intel Core i5. I eventually overcame the black screen issue when installing Ubuntu and now things are working well.

My only issue is I still can't enable Desktop Effects. I have successfully installed *Compizconfig Settings Manager* but I believe my issue is with my graphics card. l*spci | grep VGA* gives me

00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

When I go into System->Administration->Hardware Drivers it says 

*No proprietary drivers are in use on this system*

Is there anyway I can get NVIDIA drivers installed? I have tried many forums and all seem to be coming up blank!

Cheers
Eamon

---

### Post by cascade9 on 2011-01-26
More nVidia optimus problems..... :( 

At the moment, if there isnt a way to force the nvidia GPU or disable the intel video chip in the BIOS, then no, there is nothing you can do to get the nvidia card going.

*edit- unless it is switchable graphics. I dont think it is from a quick search, but its hard to tell for sure....I wish that hardware manufacturers would make it clear in model 'xxxx' uses switchable graphics or optimus.

---

### Post by gordintoronto on 2011-01-26
The E6410 has a wide range of configurations. Are you sure your unit includes an Nvidia card? If so, your issue is how to activate the card, as Cascade9 said.

---

### Post by eogorma on 2011-01-26
Thats my problem actually, my unit does not include an Nvidia card, otherwise it would be detected under System->Administration->Hardware Drivers, right? I have being trying to replace the default vesa drivers (which are incompatible with dektop effects) with NVIDIA ones but I fail every time. Any hints?

---

### Post by gordintoronto on 2011-01-26
Nvidia drivers are for Nvidia video cards. You have Intel video, so you should be looking for drivers from Intel.

---

### Post by cascade9 on 2011-01-26
> **gordintoronto said:**
> Nvidia drivers are for Nvidia video cards. You have Intel video, so you should be looking for drivers from Intel.

+1. 

You'll never get nvidia drivers working with an intel video chip.

---

### Post by eogorma on 2011-01-27
OK that makes sense, cheers!

---

