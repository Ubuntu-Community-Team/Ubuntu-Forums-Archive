---
title: "Weird scrambled colours, system fails to boot"
date: 2011-11-24
forum: General Help
---

### Post by Mike Loubet on 2011-11-24
Hi there,

I added a new fan to my computer to cool the GPU, and when I tried to boot again, I got past the BIOS but when it came to the plymouth boot screen, I get these weird scrambled colours and lines and the system never boots (I have tried many, many times, removing the new fan - so have concluded that it's not that). I am only running Lubuntu, no dual boot (so the grub screen doesn't appear by default) and when I press esc to try and enter recovery mode, nothing seems to happen.

[[IMG]http://img59.imageshack.us/img59/9016/imag0354fi.jpg[/IMG]](http://imageshack.us/photo/my-images/59/imag0354fi.jpg/)

I'm running Lubuntu 11.10 with Nvidia graphics card and proprietary drivers - which were all working until I changed the fan.

Help? :(

---

### Post by Dejavou42 on 2011-11-24
The graphics card isn't configured properly, try to boot into failsafe and start failsafe x. If that works, you can download the needed drivers.

---

### Post by Dejavou42 on 2011-11-24
I believe it's either tab or shift to get grub menu, not esc.

---

### Post by Mike Loubet on 2011-11-24
Sounds a bit noobish, but how do I do that? I keep pressing escape, but doesn't seem to work. I thought that gave you the different boot options, but it doesn't seem to be doing that...

EDIT: Sorry, didn't see that. I'm going to try it now, thanks!

---

### Post by Mike Loubet on 2011-11-24
I did that, and I got the "grub loading..." message to appear, then the scrambled screen appeared again. Looks like it doesn't even want to display the grub bootloader.

Question: I have a spare graphics card, a pretty standard old one which came with this computer. If I boot with that card, can I then reconfigure my other card on there? It's just that LiveCD doesn't seem to be working either...

---

### Post by Dejavou42 on 2011-11-24
hmmm.. definitely sounds like a graphics card issue if you can't even boot a livecd. Does the computer have an onboard graphics card? I would try that first as it uses an intel chipset that is widely supported in linux. If that doesn't work, the other graphics card that you have should be enough to test with.

---

### Post by Mike Loubet on 2011-11-24
OK, switched to integrated graphics on the BIOS, it just kept restarting every time GRUB appeared, or would not load GRUB.

Then when I switched back to PCI, I managed to get GRUB up, but every time I enter recovery mode, or recovery mode for a previous Kernel, the computer would just reboot again.

---

### Post by Dejavou42 on 2011-11-24
when you switched to integrated graphics, did you remove your other video card from the MB? If not do that, see if you can boot.

---

### Post by Mike Loubet on 2011-11-24
OK, I'll try that next, then the other graphics card.

I'm going to have to put this on hold for a while, I'll let you know how I get on! Thanks for the help :)

---

### Post by Mike Loubet on 2011-11-25
Turns out my RAM is corrupted, I enabled the BIOS to do extra checks on start-up and it allowed the RAM to function, but now only 496mb of the 1024mb are in use. I guess that stopped the graphics card from working properly, but I'm not really a hardware person nor is this a hardware forum, so I'm marking this as solved and changing my RAM cards...

---

