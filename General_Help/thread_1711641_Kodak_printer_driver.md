---
title: "Kodak printer driver"
date: 2011-03-21
forum: General Help
---

### Post by Spyderkid on 2011-03-21
I recently upgraded to 64bit but i found out that the driver i used to work my Kodak Esp5210 printer was the wrong architecture being i368. Does anyone know where I can get a driver for the 64bit ubuntu 10.10?

[post by me to where I was getting my old driver]("http://ubuntuforums.org/showthread.php?t=1682181")

---

### Post by scouser73 on 2011-03-21
I also have x64 pc with a Kodak ESP 3xxx printer but the driver **c2esp_15-1_i386.deb** is the one that needs to be installed, I have it on my system and I know it works without any problems.

The driver can be downloaded from this link;  [[COLOR="Red"]**Kodak ESP 5xxx Series Driver**[/COLOR]]("http://sourceforge.net/projects/cupsdriverkodak/files/c2esp_15-1_i386.deb/download")

---

### Post by Spyderkid on 2011-03-22
But that file you gave me is the one I was using and it was the wrong architecture for 64 bit

---

### Post by scouser73 on 2011-03-22
It's exactly the same one I have installed and it does work, trust me.

Okay so you're saying it's the wrong architecture for x64, and you're right it is but I know it works for my on my x64 pc on my Kodak ESP.

---

### Post by Spyderkid on 2011-03-23
How do i install it if the software centre won't install it because it says its the wrong architecture though??

---

### Post by Spyderkid on 2011-03-25
Anyone?

---

### Post by Spyderkid on 2011-03-25
[Solved]

I installed all of the packages under Cups and installed an old version of that package you and i posted the version 8 and did a make, sudo make install, thing.

---

