---
title: "ASUS UX31 Running Ubuntu 11.10 with WUBI"
date: 2011-10-15
forum: General Help
---

### Post by shakabra on 2011-10-15
[[IMG]http://i55.tinypic.com/2rrl4t2.png[/IMG]]("http://i55.tinypic.com/29m1yqd.png")
[http://i55.tinypic.com/29m1yqd.png]("http://i55.tinypic.com/29m1yqd.png")

I had to use WUBI because I coudn't boot from a microSD card. I'm going to pick up a usb drive later. 

My goal is a full install. Can anybody help? or show this post to somebody who can?

So far the trackpad doesn't scroll. I'll try to point out other bugs. I'm more than willing to post some logs or whatever will help.
[http://i52.tinypic.com/23rss5u.jpg]("http://i52.tinypic.com/23rss5u.jpg")

[COLOR="Red"]Update[/COLOR]
[LIST]
[*]I have managed to get Ubuntu installed just fine using a USB thumb drive.
[*]The touchpad does not function properly due to functionality being taken out of the Linux driver due to patent concerns.(That's how I understand it anyhow.
[*]Sleep completely disables your computer. If your computer goes to sleep you must hard reset it.
[*]Battery life is awful. Especially if you compare it to the times supposedly recorded under Windows7. (I personally did not have Windows loaded long enough to test it).
[*]**Nobody on the entire planet knows how to fix the problem.** 
[/LIST]

---

### Post by kinjowa on 2011-10-18
Any luck getting suspend or hibernate to work?  I've got a UX21 and have been unable to get either to work so far.

BTW, I needed the "nomodeset" kernel parameter to get it to boot.  Did you?

---

### Post by WorBlux on 2011-10-18
what are the sdb and sdc from?

---

### Post by WorBlux on 2011-10-18
Also from the dmesg

"" ACPI FADT declares the system doesn't support PCIe ASPM, so disable it""

Force enable ASPM and see if the solves the hibernation issue.

The SSD is on a pcie module and if the power management isn't working for it, it would be a good explanation of why hibernation is also failing.

---

### Post by Lucradia on 2011-10-18
Isn't it a Hybrid SSD / IDE?

---

### Post by kinjowa on 2011-10-18
> **WorBlux said:**
> Also from the dmesg

"" ACPI FADT declares the system doesn't support PCIe ASPM, so disable it""

Force enable ASPM and see if the solves the hibernation issue.

The SSD is on a pcie module and if the power management isn't working for it, it would be a good explanation of why hibernation is also failing.

Thanks WorBlux.  I tried with both pcie_aspm=off pcie_aspm=force.  Same result.  When I suspect (to RAM) the screen goes black (good!) and then after about 10 seconds, the fan spins up to maximum and the machine is essentially locked up until I power cycle it.

Any other suggestions on how to get suspend working?  I should have mentioned, I get the same result even when I boot into single user (with init=/bin/bash), unload any unnecessary kernel modules and suspend using s2ram.

---

### Post by kinjowa on 2011-10-18
> **Lucradia said:**
> Isn't it a Hybrid SSD / IDE?

Not a hybrid, SSD only.

---

### Post by WorBlux on 2011-10-18
> **Lucradia said:**
> Isn't it a Hybrid SSD / IDE?

I'm sure it's not ide pictures here. It's all solid state. That may be a SATA connection (I can't really tell the difference without a reall close up)

[http://tweakers.net/reviews/2333/3/asus-ux31-kloon-of-koning-hardware-en-aansluitingen.html](http://tweakers.net/reviews/2333/3/asus-ux31-kloon-of-koning-hardware-en-aansluitingen.html)

---

### Post by WorBlux on 2011-10-18
> **kinjowa said:**
> Thanks WorBlux.  I tried with both pcie_aspm=off pcie_aspm=force.  Same result.  When I suspect (to RAM) the screen goes black (good!) and then after about 10 seconds, the fan spins up to maximum and the machine is essentially locked up until I power cycle it.

Any other suggestions on how to get suspend working?  I should have mentioned, I get the same result even when I boot into single user (with init=/bin/bash), unload any unnecessary kernel modules and suspend using s2ram.

Maybe the whole instant on thing is screwing with something Linux excepts to be there or the bios is expecting something to happen that isn't. Maybe check the bios options for power management and just just use the s3 suspend mode.

---

### Post by kinjowa on 2011-10-18
> **WorBlux said:**
> Maybe the whole instant on thing is screwing with something Linux excepts to be there or the bios is expecting something to happen that isn't. Maybe check the bios options for power management and just just use the s3 suspend mode.

That's a good idea...  OK, checked the BIOS.  No obvious settings (not many in general).  I tried a bunch of different ones (SATA instead of AHCI, Intel AT, UFEI).  Same deal.  Thanks again for your help.

---

### Post by Lucradia on 2011-10-18
> **WorBlux said:**
> I'm sure it's not ide pictures here. It's all solid state. That may be a SATA connection (I can't really tell the difference without a reall close up)

[http://tweakers.net/reviews/2333/3/asus-ux31-kloon-of-koning-hardware-en-aansluitingen.html](http://tweakers.net/reviews/2333/3/asus-ux31-kloon-of-koning-hardware-en-aansluitingen.html)

Sorry, I meant to say HDD. I get confused now, as SSD is a type of HDD, just, people don't want to admit that the original HDDs don't have a specific name for them, and thus, confusion occurs.

Both can use SATA, PATA and IDE/SAS, if their hardware is up to the challenge.

---

### Post by cariboo on 2011-10-18
Moved to General help, as this seems to be more of a support thread, than something you would talk about around the water cooler at work.

---

### Post by RR123RR on 2011-10-19
I'm also looking at this, there is an owner thread here:
[http://forum.notebookreview.com/asus-reviews-owners-lounges/618121-asus-ux31e-zenbook-ultrabook-owners-lounge-2.html](http://forum.notebookreview.com/asus-reviews-owners-lounges/618121-asus-ux31e-zenbook-ultrabook-owners-lounge-2.html)

And another general one about the laptop... (just as a reference)
[http://forum.notebookreview.com/asus/582672-asus-ux31-ultrabook-51.html](http://forum.notebookreview.com/asus/582672-asus-ux31-ultrabook-51.html)

cheers!

---

### Post by WorBlux on 2011-10-19
Heard through the grapevine that it might be the usb 3.0 controller that is holding things up.

[http://forum.notebookreview.com/8002379-post17.html](http://forum.notebookreview.com/8002379-post17.html)

---

### Post by RR123RR on 2011-10-19
> **Lucradia said:**
> Sorry, I meant to say HDD. I get confused now, as SSD is a type of HDD, just, people don't want to admit that the original HDDs don't have a specific name for them, and thus, confusion occurs.

Both can use SATA, PATA and IDE/SAS, if their hardware is up to the challenge.

HDD implies Hard **DISK** Drive... 
So, in that sense, SSD is not a type of HDD :)
(sorry for the nitpicking, just thought it might clarify things!)

---

### Post by Lucradia on 2011-10-19
> **RR123RR said:**
> HDD implies Hard **DISK** Drive... 
So, in that sense, SSD is not a type of HDD :)
(sorry for the nitpicking, just thought it might clarify things!)

SSD means Solid-State **DISK** and **DRIVE** and **Electronic _DISK_**.

---

### Post by RR123RR on 2011-10-20
> **Lucradia said:**
> SSD means Solid-State **DISK** and **DRIVE** and **Electronic _DISK_**.

hehe indeed, we really have to put an end to that confusion! ;-)

So anyone made any progress with power management and/or touchpad? :)

---

### Post by wkretzsch on 2011-10-26
I'm really looking forward to getting a ux31 and installing ubuntu on it.  Hope someone can figure out how to deal with these issues.

---

### Post by renselu on 2011-10-27
Anyone managed to fix the bluetooth pairing problem? [http://ubuntuforums.org/showthread.php?p=11398729#post11398729](http://ubuntuforums.org/showthread.php?p=11398729#post11398729)

---

### Post by jeppebundsgaard on 2011-11-12
Hi,
The sleep issue seems to be solved in this thread:
[http://ubuntuforums.org/showthread.php?t=1865577](http://ubuntuforums.org/showthread.php?t=1865577)
- go to page 3-7 to see the solution.

---

