---
title: "display issues with new install"
date: 2011-02-16
forum: General Help
---

### Post by gee013 on 2011-02-16
i have recently installed ubuntu 10.10 onto a older PC and everything installed perfectly. my problem is that the display has these annoying vertical lines all the way across.

its an older intel mini atx motherboard with just the onboard vga 

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter (rev 04)

thanks!

---

### Post by jerrrys on 2011-02-17
have you tried changing your refresh rate ?

---

### Post by gee013 on 2011-02-18
yes, i did try different refresh rates and different resolution settings. 
also, it just sees it as a "unknown" monitor.

---

### Post by jerrrys on 2011-02-18
another simple thing to try is go to system>admin>hardware drivers and see if any updated drivers are out there.

if no drivers exist then i would suggest looking here for an answer

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=[SiS]+661%2F741%2F760+PCI%2FAGP+or+662%2F761Gx+PCIE+VGA+Display+Adapter&as_qdr=all&sa=Google+Search&lang=en#881]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=")

for some reason i cannot properly post this link so please to enter in the search enging:

[SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by redmoonskylight on 2011-03-13
Hi gee013.

I have the same chipset that you do, and it appears that we are out of luck when it comes to the display and graphics department.  The problem is that instead of having their own memory, our cards share memory with the rest of the system, creating all sorts of buggy problems.
You can read more about it here:
[http://www.winischhofer.net/linuxsispart1.shtml#13](http://www.winischhofer.net/linuxsispart1.shtml#13)

Basically, from what I understand, we are just out of luck.  There probably won't be a driver made for linux users, and even with a driver the card is still technically useless because of the memory issue.
I had all current drivers installed when my system was Window$, and display was always funky.

---

