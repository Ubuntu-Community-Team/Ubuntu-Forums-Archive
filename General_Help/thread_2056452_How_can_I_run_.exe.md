---
title: "How can I run .exe?"
date: 2012-09-11
forum: General Help
---

### Post by evelynx0x0 on 2012-09-11
I upgraded to Ubuntu for several reasons. 
It's alright, but I'm experiencing one main issue.

I have this CD it's like a CD that teaches you about driving and whatnot. 
I thought it would be able to run on Ubuntu. But now I realize it doesn't cause it's a .exe file.

Can anybody be very detailed and explain how I can get this CD to run? TY

---

### Post by greatsirkain on 2012-09-11
google 'wine for ubuntu' it might let you run it but you'd be best off trying to find a linux version of a similar program from the ubuntu software center

---

### Post by jerrrys on 2012-09-11
I do not do this, but I can point you here:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=run+.exe+cd&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=run+.exe+cd&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by heminder on 2012-09-11
do a *sudo apt-get install wine* or download Wine from the software center and then run the exe file using that.

---

### Post by Mark Phelps on 2012-09-11
Chances are most likely that it will NOT work in Ubuntu.

You can go to the WineHQ website and check their Application Compatibility database, entering the app name and looking at the results.

If you don't get any results, or if the rating is lower than Gold, you are wasting your time.

---

### Post by oldos2er on 2012-09-11
> **evelynx0x0 said:**
> Can anybody be very detailed and explain how I can get this CD to run? TY

If it's a Windows program, the best thing is to use Windows. Windows programs don't run natively on Linux, but a few of them *may* run using Wine. See [http://ubuntuforums.org/showthread.php?t=885111](http://ubuntuforums.org/showthread.php?t=885111)

---

### Post by heminder on 2012-09-11
It's a driving tutor program. It's mostly likely not doing any low-level computing. It's probably just interfaces and some basic scripts. Doesn't hurt to try to run it with Wine anyway.

---

### Post by spaceshipguy on 2012-09-11
You can also set up a virtual machine with Windows running inside. It's surprisingly simple. I use Virtual Box - it's in the Software Centre.

---

