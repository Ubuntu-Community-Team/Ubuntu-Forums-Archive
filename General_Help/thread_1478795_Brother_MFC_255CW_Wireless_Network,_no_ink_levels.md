---
title: "Brother MFC 255CW Wireless Network, no ink levels"
date: 2010-05-10
forum: General Help
---

### Post by migs73 on 2010-05-10
I have recently installed a wireless Brother MFC-255CW printer onto my network. I followed the instructions on the Brother website for Linux install onto my machine running Lucid. It prints great, but what I seem to be having bother with is Cups reports it cannot get my ink levels. See screen shot.
Has anybody come across this/got it to work??

---

### Post by dino99 on 2010-05-10
just googling around and see that lucid have some issue, might need to report on launchpad.

but try:
sudo update-pciids && update-usbids

then lsusb
and check [COLOR="Blue"]cat /lib/udev/rules.d/40-libsane.rules[/COLOR]
to see if thats match with lsusb info you got

you might search "brother" into synaptic too

---

### Post by migs73 on 2010-05-10
Thanks Dino,
Does what you ask not only work if I'm connected via usb? The connection I have is via wireless network and the cups server. I have already installed the Brother drivers for cups. See below for my synaptic output. Is there any other Cups stuff I may be missing??

PS my printer is an MFC-255CW. I cannot find any help on the Brother website.

---

### Post by migs73 on 2010-05-12
Bump

---

### Post by migs73 on 2010-05-24
another Bump!

---

### Post by migs73 on 2010-06-18
Bumpity Bump!?!

---

### Post by migs73 on 2010-10-29
I will mark this thread as solved, even though the problem still remains. I have found out recently that although I still cannot get an instantaneous reading of the ink level, should one go low I do get a warning.

---

