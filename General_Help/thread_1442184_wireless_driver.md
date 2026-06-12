---
title: "wireless driver"
date: 2010-03-29
forum: General Help
---

### Post by achtneun on 2010-03-29
So my problem is, my Ubuntu cant find wireless driver while liveCD can. How can i fix it? I used Ubuntu 9.10 . Pls help me!!! im a newbie =.="
Some ppl say i should use wicd to set wireless.. but when i try to install that deb file, it says "wireless manager" is still there so it cant run. So wat should i gonna do? i mean how can i "uninstall" a program on Ubuntu 9.10?
Thx first

---

### Post by cryptotheslow on 2010-03-30
What wireless adapter is it? And is it an internal PCI / onboard device or connected by USB?

A good start would be to boot up with the LiveCD and copy/paste back here the output from these commands (run in a Terminal):

lsmod
lspci
lsusb
nm-tool
lshw -C network


That will give us the relevant information about the interface and driver being used by the LiveCD - then we should be able to help you get it working under the installed version.

---

### Post by 3rdalbum on 2010-03-30
System > Administration > Hardware Drivers.

If it doesn't list anything there, and it did when you were running from the live CD, then you need to refresh your package list. Of course, this requires an internet connection, so plug your computer into your router via the Ethernet port, and go to System > Administration > Synaptic and click the Reload button.

Then quit Synaptic and you'll be able to download your wireless driver through the Hardware Drivers program.

---

### Post by achtneun on 2010-03-30
Wow thx 3rdalbum much :D my Ubuntu work perfect after i do that, my  wireless card, my monitor works more smoothy than b4. Pls help me more  next time,cryptotheslow you too.
Thanks again ^^

---

### Post by cryptotheslow on 2010-03-30
No problem, glad you got it sorted. :)

I'm always too quick to jump into a Terminal to try to figure things out I think - but that's where I am most familiar.

Please can you update your post subject to mark it as Solved.

---

