---
title: "Virtual Box Messed things up"
date: 2011-09-23
forum: General Help
---

### Post by yungballla6 on 2011-09-23
Hi, i was trying to intall Virtual Box following this guide [http://www.ubuntugeek.com/how-to-install-virtualbox-4-x-on-ubuntu-11-04natty.html]("http://www.ubuntugeek.com/how-to-install-virtualbox-4-x-on-ubuntu-11-04natty.html")

After i entered all of the commands i instantly lost internet connection and could not get it back. When i went to restart my computer it showed a black screen with commands but it would stay on that screen forever, no new commanmds were being processed it just froze. When i booted back up into ubuntu I still could not connect to the internet, and again when i booted down it froze with a bunch of commands. I have no idea what the hell happened but i would appreciate if someone knows how to help my situation. thank you.

---

### Post by yungballla6 on 2011-09-23
windows works fine though

---

### Post by seawolf167 on 2011-09-23
What are the "bunch of commands" being shown? Are you able to type anything? You said you were able to boot to the desktop? Please provide us with more details so we can help.

---

### Post by yungballla6 on 2011-09-23
> **seawolf167 said:**
> What are the "bunch of commands" being shown? Are you able to type anything? You said you were able to boot to the desktop? Please provide us with more details so we can help.

When i boot up into ubuntu before i get to the log in screen after the grub menu i see the picture with commands with a black background (attatchment #2), i can move the mouse cursor around and still sign in by hitting enter then typing in my password while being blind of the log in screen. When i try to power down i get stuck on (attachment #1) so i have to hold down the power button on my laptop until it powers down.

Also at these screens i am unable to type anything or give commands.

---

### Post by yungballla6 on 2011-09-23
bump

---

### Post by jmate24 on 2011-09-23
In order to help you we need more information:

did you install dkms before you installed virtualbox?
what version of ubuntu are you running?
what kernel are you running (i.e. linux-image-2.6.38-11-generic)?

who was your laptop manufacturer (i.e. Acer, Dell, IBM (Lenovo), Asus, Alien Ware, etc., etc.)

what is connected to your laptop when this first occurred?

what are your laptop specs (i.e. Processor speed, Hard drive size, amount of RAM, Ethernet Card (type and manufacturer), Modem Card (type and manufacturer), Wi-fi Card (type and manufacturer)?

have you tried filing a bug on virtualbox.org's website?

---

### Post by yungballla6 on 2011-09-23
> **jmate24 said:**
> In order to help you we need more information:

did you install dkms before you installed virtualbox?
what version of ubuntu are you running?
what kernel are you running (i.e. linux-image-2.6.38-11-generic)?

who was your laptop manufacturer (i.e. Acer, Dell, IBM (Lenovo), Asus, Alien Ware, etc., etc.)

what is connected to your laptop when this first occurred?

what are your laptop specs (i.e. Processor speed, Hard drive size, amount of RAM, Ethernet Card (type and manufacturer), Modem Card (type and manufacturer), Wi-fi Card (type and manufacturer)?

have you tried filing a bug on virtualbox.org's website?

I have a HP G62 with a intel pentium 2x processor, realtek wifi, 4gb ram, i am running ubuntu 11.04 with kernel version 3x.xx (newest version), nothing was plugged into my laptop (charger, mouse etc.) i followed the guide i posted above to the T, step by step.

---

### Post by yungballla6 on 2011-09-24
bump

---

### Post by davidvandoren on 2011-09-24
Did you try booting into an older kernel?

At start up hit the arrow key down and choose an older kernel to boot.

---

### Post by yungballla6 on 2011-09-24
> **davidvandoren said:**
> Did you try booting into an older kernel?

At start up hit the arrow key down and choose an older kernel to boot.

there is no other kernels for me at boot up. just kernel 3 then kernel 3 safe mode

---

### Post by yungballla6 on 2011-09-24
bump

---

### Post by yungballla6 on 2011-09-24
Someone please help.

---

### Post by yungballla6 on 2011-09-24
Bump

---

