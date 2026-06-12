---
title: "Desktop freeze with various Ubuntus"
date: 2011-08-02
forum: General Help
---

### Post by blackpit on 2011-08-02
Hello. I have an old desktop pc (AMD sempron 3000+, 1gb RAM, GeForce2 MX200 64MB, Maxtor harddrive 120GB) which I used with Ubuntu 7.10 without any problems. About a year ago the power supply broke down and I didn't bother fixing it until now, so I decided to install a newer version of Ubuntu. I tried Ubuntu 10.04, 10.10, 11.04, Lubuntu 11.04, Linux Mint 11. During installation (both with usb flash drive and CD) at some point the desktop froze. The mouse cursor was moving but everything else was unresponsive. I managed to install using 10.04 alternate installer but again at the installed system after a few minutes it froze again. I also tried pclinuxos lxde, which installed fine, but afterwards it froze in the exact same fashion. I couldn't find anything so far to help me pinpoint the problem. Any input would be appreciated. Thanks.

---

### Post by stmamont on 2011-08-02
it looks like you have your RAM memory broken, try running memory tests

---

### Post by blackpit on 2011-08-02
I ran a memory test using a live-cd and there were no errors.

---

### Post by egalvan on 2011-08-02
I've had this happen due to over-heating because of dust/dirt..
and I've had it happen due to bad caps on the mobo.

First issue is cheap & easy... just chase the dust-bunnies out...

The second will cost money and time...
only you can decide on the benefits/cost ratio.

forgot to mention...
 overheating can also happen due to cpu thermal pasted getting old...
how-to fix??
remove heat-sink,
clean both heat-sink and cpu with paper napkins,
swipe with alcohol,
let dry,
apply fresh paste or tape,
re-install heat-sink.

---

### Post by blackpit on 2011-08-02
Thanks egalvan. I will look into your suggestions. Although I doubt it will be as easy as dusting off since i did that when I replaced the power supply. Also could the new power supply cause the overheating itself (or some other problem) since it's 550W instead of 420W that was the old one? Is there some way to establish that there is overheating (or exclude altogether) because it didn't feel like it when I placed my hand at the side fans of the computer.

---

### Post by blackpit on 2011-08-04
I installed WindowsXP and it runs with no problems. So I guess it's safe to rule out any hardware issues. I may try later to install some other distros as well, maybe some older ones too, and see if the problem persists.

---

### Post by blackpit on 2011-08-06
So i did a few other test installs and here are the results. I tried puppy linux 5.25, Salix OS 13.1.2, Ubuntu 9.04 and 9.10. All of them worked fine. I'm sticking with Ubuntu 9.10 for the time being but I'm open to any suggestions that could help locate the problem. My best guess so far is lack of support for the video card (nvidia geforce2 MX200 64MB) from 10.04 and onwards.

---

