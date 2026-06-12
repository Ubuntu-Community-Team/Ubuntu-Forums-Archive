---
title: "Constantly getting &quot;E:Unable to correct problems, you have held broken package&quot;"
date: 2010-10-23
forum: General Help
---

### Post by robot85 on 2010-10-23
...on many things I try to install. I am running 64-bit Lucid; would running 64 bit be the problem? Anyway, A few of the packages I've been trying to install include Wine 1.3 and a proprietary ATI FGLRX graphics driver for my Laptop's Radeon 4250 graphics card. Many other things I try to install from the Synaptics Package Manager (or anywhere, including the Ubuntu Software Centre) come up with the "E:Unable to correct problems, you have held broken package" as well. It is very frustrating and it is a very vague error. Is it my 64 bit Ubuntu or is it already installed packages that are broken...? :confused:

---

### Post by physic.dude on 2010-10-23
I had that same problem, I just Re-installed Ubuntu 64 Bit, and after that I first installed the graphics driver (Then reboot) and then run the update manager (Then reboot). 

IDK what the problem was, it might be a random thing.

---

### Post by robot85 on 2010-10-23
Reinstalling most likely will not help, as this is a new installation. It was doing this from the moment I installed it.

---

### Post by BigCityCat on 2010-10-23
Restart and login using recovery. Then fix broken packages. See if that works.

---

### Post by drs305 on 2010-10-23
From Synaptic, you can select "Custom Filters" in the left pane, then Broken Packages to see if it's one package or multiples. 

There is also the option in the Synaptic to fix broken packages via the Edit menu.

---

### Post by robot85 on 2010-10-23
I have no broken packages. I don't understand this. :(

---

### Post by drs305 on 2010-10-23
You might be able to find out what packages, if any, are being held with this command:
```
grep -B1 "Status: hold" /var/lib/dpkg/status
```

There is an "apt-get install" option to ignore held packages ( --ignore-hold ) . Not knowing what packages may be held and why I can't tell you what it will do to your installation if you run it.

---

