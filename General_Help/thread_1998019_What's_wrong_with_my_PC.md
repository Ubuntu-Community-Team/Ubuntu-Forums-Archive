---
title: "What's wrong with my PC?"
date: 2012-06-06
forum: General Help
---

### Post by uqbar on 2012-06-06
I am running Kubuntu 12.04 on my desktop PC.
Which, I'd say, it's rather powerful:
- CPU i7 970
- RAM 12GB 1333 MHz
- HD 1.2 TB Barracuda 10K rpm
- NVidia GeForce 210
- MB ASUS P6X58D-E, BIOS 0701

Now, the desktop experience (with either GNOME or KDE) isn't "blazing fast" as I'd expect.
Large file copies, disk-to-disk and disk-to-USB, as well as DVD burning, make my desktop unresponsive, also when just editing a text file in VIM.
Now I'm testing a "low latency" kernel but I'd say my PC has plenty of power not to need such a "tweak".

My questions are:
How can this be possible?
How can I "fix" such an issue?

Thanks in advance for any kind of useful information.

---

### Post by mastablasta on 2012-06-06
you will start by troubleshooting the CPU consuption. 
 
what does command ```
top
``` 
show
or maybe if you use htop (utility).
 
something must be cloging up your CPU or GPU. Have oyu installed proprietary drivers. if so, did you check if there are any known issues with proprietary drivers?
 
 
 
i have a much much weaker CPU and graphics and yet KDE is fast and responsive with most effects turned on.

---

