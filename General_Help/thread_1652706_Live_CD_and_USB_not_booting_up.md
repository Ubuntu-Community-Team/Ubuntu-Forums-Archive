---
title: "Live CD and USB not booting up?"
date: 2010-12-25
forum: General Help
---

### Post by Cheetah1933 on 2010-12-25
I am on my new HP envy 14, and I have both a USB drive and a Live CD with the latest version of 64 bit ubuntu.

When I run the Live CD, it takes me to a purple screen with a keyboard and person symbol at the bottom, and after a minute it opens up a black window that looks like a command prompt, and then the screen goes black.

When I try to run the USB, either selecting the "install" option or the "run from USB option", it goes through the boot processes like everything is working, and then the screen goes black.

The same thing happened on my main computer with a 32 bit live CD. Any suggestions?

---

### Post by Rubi1200 on 2010-12-25
Hi and welcome to the forums :)

Please post the _full_ specifications for the machine in question.

Thanks.

---

### Post by wojox on 2010-12-25
Latest version being 

10.04 LTS

10.10

11.04 Daily build

---

### Post by Cheetah1933 on 2010-12-25
Intel Core i5 M460 2.53ghz
4gb ram
570GB hard drive with a speed of 7200rpm
1 GB ATI Mobility _Radeon_ HD 5650 dedicated graphics card with switchable graphics (I can't find the specs for the other card anywhere.)

EDIT: The version is 10.10 64 bit

---

### Post by Rubi1200 on 2010-12-25
Try some of the boot parameters to get things going. You do this when you see>  a purple screen with a keyboard and person symbol at the bottom , hit F6 and a menu should appear.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Also try the nomodeset option.

---

### Post by Cheetah1933 on 2010-12-25
Ill try that really quick, thank you.

---

### Post by ctparmenter on 2011-11-02
Did that work? I'm having the exact same problem. Same computer except: Intel Core i5-2410M 2.3 GHz, 6 GB ram, same video card.

---

### Post by techvish81 on 2011-11-02
why not use 11.10 when u r not using LTS, 
it is great and may be the reason behind your problem is some of your newer hardware is not recognized by older version of Ubuntu.

i've got an i3 which works flawlessly with natty and oneiric but not with older versions.

---

