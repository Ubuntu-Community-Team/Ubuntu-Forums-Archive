---
title: "Wine doesnt like my videocard drivers. Please help!"
date: 2009-08-30
forum: General Help
---

### Post by mac666 on 2009-08-30
Hola,
Im running wine 1.01 and i have Nvidia GeForce 9800GT with Nvidia driver version 185.18.36
When i try to run games thru wine, i often get messeges about my videocard having to low memory or that i dont have direct3d, hardware 3d acceleration etc etc...
I have installed many things thru winetricks such as DriectX 9, .NET, VB etc etc

Still Wine doesnt think get my videocard drivers...
I even tried to install windows drivers from nvidia into wine, just for the sake of it. It didnt work :)

Im new to linux and my ubuntu installation is not very old, max 1-2 weeks.
Am i missing something here?
Games like Warcraft III, Fable, Half-Life 2 works allmost... Exept some bad graphics...
But they cant influence the screen resulotion. If Half-Life runs in 800x600 resolution. It will be in a centered window on my desktop with that resulotion, Not full screen...

Warcraft III makes everything around its actual size just black, it doesnt fit the window since it cant affect the desktop resolution.

Please? What am i missing... Some vitual part of my videocard drivers..

I have triedout other versions of the drivers, but this version i have now ( the latest from nvidias website) works most well with ubuntu. But Wine cant get into it :(


Please help me out!!

---

### Post by mac666 on 2009-08-31
Come on! Please... Anyone must know what im missing?

---

### Post by mac666 on 2009-08-31
Anyone?

---

### Post by XCan on 2009-08-31
It doesn't work either with the drivers Ubuntu installs for you in "Hardware Drivers"?

---

### Post by mac666 on 2009-08-31
System > Administration > Hardware Drivers is empety... It says i have no *** drives in use in this system...
Any clues?
Thanks for the reply...

---

### Post by XCan on 2009-08-31
Hmm, that's very strange. I have the exact same video card on my workstation and I can install a driver from Ubuntu's Hardware Drivers menu. I haven't tried running games on it through Wine, but I know that, CUDA calculations work fine, as well as quakelive.

---

### Post by mac666 on 2009-08-31
quakelive for linux???!!!
Im on it... I will try it out and get back with results,
Thanks

---

### Post by mac666 on 2009-09-03
> **XCan said:**
> Hmm, that's very strange. I have the exact same video card on my workstation and I can install a driver from Ubuntu's Hardware Drivers menu. I haven't tried running games on it through Wine, but I know that, CUDA calculations work fine, as well as quakelive.

Ok it worked good with Quake live with ubuntu...
What can it be then?

---

### Post by P4man on 2009-09-03
What you're missing is that you're running ubuntu, and not windows. If your main goal is playing windows games, stick to windows, or dual boot.

If you want to try and fight wine to perhaps get some of your games working, then check wineHQ for tips. for instance for warcraft, see this:

[http://appdb.winehq.org/appview.php?iVersionId=1177](http://appdb.winehq.org/appview.php?iVersionId=1177)

---

