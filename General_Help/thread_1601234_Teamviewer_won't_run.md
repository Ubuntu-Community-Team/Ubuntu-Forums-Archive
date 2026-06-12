---
title: "Teamviewer won't run"
date: 2010-10-20
forum: General Help
---

### Post by Lord35 on 2010-10-20
Hi there, I just installed Xubuntu 10.10 and Teamviewer 5. When I try to launch it i get an error message. 

"X11 Bit Depth Mismatch" It says i need to change the color bit depth to 24bpp.

It used to work fine on this same pc with another installation.

I tried to change the xorg.conf file, but there is none. I created one but now of course it is an empty file, and i'm stuck.

any help ?? thanks a lot.

---

### Post by P4man on 2010-10-20
What videocard do you have? If you have to do it through xorg.conf, then create one with this command:

sudo Xorg -configure

This doesnt work when X is running, so stop X first or boot into recovery mode. More details here:
[http://ubuntuforums.org/showpost.php?p=9431354&postcount=8](http://ubuntuforums.org/showpost.php?p=9431354&postcount=8)

---

### Post by Lord35 on 2010-10-22
Thank u for your answer. My video card is a Voodoo 3 3000, AGP 16mb.

I rebooted on fail safe mode and Teamviewer worked, but not on normal mode.

Can i install proprietary drivers for this card ?? To set up the color depth to 24bpp ??

thanks

---

### Post by P4man on 2010-10-22
A voodoo 3000? Wow. Im impressed that even works at all. That card is like 12 years old and from a company that went bankrupt ages ago. No proprietary drivers for that, and if I read wiki correctly:
[http://en.wikipedia.org/wiki/Voodoo3#Architecture_and_performance](http://en.wikipedia.org/wiki/Voodoo3#Architecture_and_performance)
Then this card doesnt even support 24 bit colour.

Maybe its time to buy something new?

---

