---
title: "new Asus UL30VT-A1 installing ubuntu"
date: 2010-04-21
forum: General Help
---

### Post by supershin on 2010-04-21
Hi, I've been reading some threads about this model and hybrid-graphic models in general having issues with nvidia drivers. What I don't know is all the side-effects when I install ubuntu, read something about needing to run a script. 

I'm planning on installing ubuntu and other distros, namely fedora, opensuse and backtrack. I'm still keeping windows 7 though.

So can I just install ubuntu like how I installed it on my desktop? Also, since some/all of the other distros are debian-based, hm not sure, anyway would they all suffer the same problem and can be fix with the same 'patch'/script?

Please explain this clearly to me. :confused:


Links:
[http://ubuntuforums.org/showthread.php?t=1432109&highlight=asus+ul30vt-a1](http://ubuntuforums.org/showthread.php?t=1432109&highlight=asus+ul30vt-a1)
[http://ubuntuforums.org/showthread.php?t=1366605&highlight=ul30vt](http://ubuntuforums.org/showthread.php?t=1366605&highlight=ul30vt)

Btw its 64bit.

---

### Post by supershin on 2010-04-22
Can I install fedora, opnsuse and backtrack and not experience this graphics problem? 

For U/UL Asus owners, 
[https://launchpad.net/~asus-ul30]("https://launchpad.net/~asus-ul30")
This team is a group of ASUS U/UL Series owners and/or developers interested in getting it to work 100% under Linux (e.g. ASUS UL30A-A2, ASUS UL30A-X5, ASUS UL30A-A3B, ASUS UL30Vt-A1, ASUS UL30Vt-X1, ASUS UL80Ag-A2B, ASUS UL80Ag-A1, ASUS UL30JT, ASUS UL80JT, ASUS UL30Jt, ASUS U30Jc, etc)

EDIT:
[https://wiki.ubuntu.com/LaptopTestingTeam/Old/AsusUL30A]("https://wiki.ubuntu.com/LaptopTestingTeam/Old/AsusUL30A")
Hardware details, shows what works and some fixes.

---

### Post by avilella on 2010-04-23
I think the differences between Ubuntu and Fedora, Opensuse or other distros will be minimal. Please feel free to subscribe to the launchpad team even if you haven't got the laptop yet, and ask if someone has successfully installed other distros in the mailing list. There are ~140 users subscribed, I am sure someone must have tried :-p

> **supershin said:**
> Can I install fedora, opnsuse and backtrack and not experience this graphics problem? 

For U/UL Asus owners, 
[https://launchpad.net/~asus-ul30]("https://launchpad.net/~asus-ul30")
This team is a group of ASUS U/UL Series owners and/or developers interested in getting it to work 100% under Linux (e.g. ASUS UL30A-A2, ASUS UL30A-X5, ASUS UL30A-A3B, ASUS UL30Vt-A1, ASUS UL30Vt-X1, ASUS UL80Ag-A2B, ASUS UL80Ag-A1, ASUS UL30JT, ASUS UL80JT, ASUS UL30Jt, ASUS U30Jc, etc)

EDIT:
[https://wiki.ubuntu.com/LaptopTestingTeam/Old/AsusUL30A]("https://wiki.ubuntu.com/LaptopTestingTeam/Old/AsusUL30A")
Hardware details, shows what works and some fixes.

---

### Post by supershin on 2010-04-23
Thanks for the help. Guess I'll have to get myself an openID for that lauchpad thing. When I get those distros on I'll post back.

---

### Post by nl4m on 2010-04-23
If you want you can download wubi. Install Ubuntu from within windows, reboot, log in to Ubuntu, click on "System" - "Administration" - "Hardware drivers" and see if you can update the drivers to Nvidia. I, too, had some problems with my video card until I install those drivers. Now I can use some special effects.

---

### Post by nokbar on 2010-04-24
Hi,
I had posted a call for support for my install issues with the Asus U30JC-A1 in this [thread]("http://ubuntuforums.org/showthread.php?t=1460557").

---

### Post by supershin on 2010-04-24
I forgot to ask, I was going to install 8.10 but seeing as how 10.04 is coming out in a few days I may wait it out. If I install 8.10 will i face the same issues? and if i wait for 10.04 will it work out of the box?


[I]For U/UL Asus owners,
[https://launchpad.net/~asus-ul30](https://launchpad.net/~asus-ul30)
This team is a group of ASUS U/UL Series owners and/or developers interested in getting it to work 100% under Linux (e.g. ASUS UL30A-A2, ASUS UL30A-X5, ASUS UL30A-A3B, ASUS UL30Vt-A1, ASUS UL30Vt-X1, ASUS UL80Ag-A2B, ASUS UL80Ag-A1, ASUS UL30JT, ASUS UL80JT, ASUS UL30Jt, ASUS U30Jc, etc)[/I]

Your model is last in the list above "ASUS U30Jc, etc". 
However the link to turn off the nvidia card states just Asus UL30Vt, or Asus UL50Vt or Asus UL80Vt. Anyone know if that fix would apply to U30JC?

---

### Post by nokbar on 2010-04-24
> **supershin said:**
> 
[I]For U/UL Asus owners,
[https://launchpad.net/~asus-ul30](https://launchpad.net/~asus-ul30)
This team is a group of ASUS U/UL Series owners and/or developers interested in getting it to work 100% under Linux (e.g. ASUS UL30A-A2, ASUS UL30A-X5, ASUS UL30A-A3B, ASUS UL30Vt-A1, ASUS UL30Vt-X1, ASUS UL80Ag-A2B, ASUS UL80Ag-A1, ASUS UL30JT, ASUS UL80JT, ASUS UL30Jt, ASUS U30Jc, etc)[/I]

Your model is last in the list above "ASUS U30Jc, etc". 
However the link to turn off the nvidia card states just Asus UL30Vt, or Asus UL50Vt or Asus UL80Vt. Anyone know if that fix would apply to U30JC?

Well, on the U30JC, the screen goes blank when I try to install/run the liveCD, so I don't know how I would even work with the command line, or if it would even help.

---

### Post by supershin on 2010-04-29
hmm...I was able to install backtrack without any problems. I can dual boot without any problems

**UPDATE: Installed backtrack, lucid lynx without any problems.** No graphic issues though i didn't check to see it i was running off integrated graphics or nvidia card. 

I installed fedora but it has a boot problem not related to graphic issue, my post on it here [http://ubuntuforums.org/showthread.php?p=9242390#post9242390](http://ubuntuforums.org/showthread.php?p=9242390#post9242390)

---

