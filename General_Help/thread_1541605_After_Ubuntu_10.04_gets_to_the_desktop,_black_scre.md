---
title: "After Ubuntu 10.04 gets to the desktop, black screen and can't do anything"
date: 2010-07-29
forum: General Help
---

### Post by solarmonk644 on 2010-07-29
Hey,

I have just loaded Ubuntu 10.04 onto a hard drive and then booted using my laptop and it boots all fine and I get to the desktop. After I get to the desktop in around 10-20 seconds the screen suddenly goes black and the mouse disappears and i can't do anything. The fan still goes but thats about it, I have to hard shut down and load up again but it just keeps happening. Not sure what to do next?

Its an old  Toshiba Satelite laptop 
1.6 ghz processor
1gb ram


Cheers,

Solarmonk

---

### Post by alenn on 2010-07-29
what's your graphic card?

---

### Post by solarmonk644 on 2010-07-29
ATI MOBILITY RADEON 9600/9700 Series

---

### Post by apesa on 2010-07-29
I am having the same problem. Runs through the bot process and gets to the Plymouth Ubuntu splash, sits for a couple seconds and then goes blank. Usually this is where the login screen appears. 

The common denominator is the ATI Radeon. In my case it is a desktop Radeon HD4890. I have installed the ATI Catalyst 10.6 drivers.

Any help here would be great.

---

### Post by dino99 on 2010-07-29
boot into recovery mode (hold "shift" key down at end of bios process if grub menu is hidden), then goto:

system admin hardware driver to check driver activation

as your laptop is a toshiba, some specific packages have to be installed: toshset, toshutils, fnfxd (search them into synaptic: system admin synaptic

if issues are still there, try booting by adding on the boot line: nomodeset and/or noacpi, nolapic, noapic, irqpoll

---

### Post by apesa on 2010-07-29
Solarmonk, did you install Catalyst? Version? In my situation I am able to get into the Grub menu. Boot into recovery mode and reinstall Catalyst from the command line. I seem to have to do this every time a large update comes around. 

My bet it is Catalyst and the above pkgs dino99 mentioned are your problem.

---

### Post by solarmonk644 on 2010-07-29
Laptop wont even boot now. I'm going to take the whole thing apart and test each of the components then rebuild it. Re-install XP and see if it even still works sorry about not being able to try out your idea.

Solarmonk

---

### Post by dino99 on 2010-07-29
is it booting on live cd or usb stick ?

---

### Post by solarmonk644 on 2010-07-29
I swapped the hard drive to one which has Windows XP installed on it and this has always worked in this laptop however, it isn't now so I think theres issues with the laptop itself so I'll try fix that first.

---

