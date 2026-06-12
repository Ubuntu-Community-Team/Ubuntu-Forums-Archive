---
title: "Laggy Ubuntu"
date: 2011-05-15
forum: General Help
---

### Post by CypressX on 2011-05-15
Specs
I am running on an AMD Athlon x64 4400+ x2 dual core processor running at an over clocked 2.4 GHz with an ATI XFX Radeon HD 4650 graphics card, I have an 160 gig hard drive and it runs fine with Ubuntu, and my motherboard is a rare RS480-M motherboard that only supports socket 939 CPU's (which AMD no longer makes.) And 2 gigs of RAM. keyboard and mouse are USB devices.

Problem: My Ubuntu is running SO slow that whenever I type it lags, whenever I move my mouse it lags, whenever I open terminal it lags, and pretty much the entire thing lags like hell... I would love to know what the problem with my system and Ubuntu is, I am Running Ubuntu (Latest Version) 32-bit OS, but the thing is that theres so many things that could be causing the problem for the lag. It could be that my CPU is only using 1 of its cores in Ubuntu (which I don't know how to fix), or that I installed the wrong Ubuntu on my machine (I installed intel 32-bit because the amd athlon's only had 64 bit compatible installations which my computer is only 32-bit), or just because my keyboard and mouse are USB and Ubuntu hates it.

If someone could give me an answer why my Linux system is lagging so badly and give me step by step directions (cuz im a noob) I would very much appreciate it. (I do not know if both of my CPU's Cores are being used or not.)

Please Help!

---

### Post by mörgæs on 2011-05-15
Hi, welcome to the fora.

This machine should have plenty of horsepower for Ubuntu. As a beginning, you could install Gkrellm and watch the system load while you are working.

---

### Post by ianmillington on 2011-05-16
Launch a terminal and type 

top

Then hit return

That will list the processes that are running and, importantly, show you what resources they are using. 

From the list is there anything that looks like it's grabbing more than its fair share. The most likely candidate is xorg which handles not only graphics but has an influence in the keyboard and mouse.

On the question of your graphics card, are you using the supplied driver or the one from AMD/ATI? If the former, it may be that there is a manufacturer-supplied driver for your card. If so, I'm not sure whether you have to download it or whether it's available via ubuntu's proprietory driver installer. I'm at a Win box right now :( so can't be 100% sure but if you go to system/ hardware (I think) you should be advised whether any special drivers are available for your hardware.

HTH

---

### Post by coffeecat on 2011-05-16
> **CypressX said:**
> It could be that my CPU is only using 1 of its cores in Ubuntu (which I don't know how to fix),



Open up System Monitor and look in the Resources tab. That will tell you how many cores your system is using. If you are using the Unity desktop, click on the shutdown button top right and choose 'System Settings'. System Monitor is under the System heading. If you are using classic gnome desktop, System Monitor is in the System > Administration menu.

> **CypressX said:**
>  or that I installed the wrong Ubuntu on my machine (I installed intel 32-bit because the amd athlon's only had 64 bit compatible installations which my computer is only 32-bit)

Are you sure? You say your CPU is the  AMD Athlon x64 4400+ which is definitely 64-bit. However with only 2GB RAM, the advantages of running a 64-bit system are marginal or non-existent. A 32-bit system *should* run just fine on a 64-bit system.

---

### Post by Throne777 on 2011-05-16
> **CypressX said:**
> Specs
I am running on an AMD Athlon x64 4400+ x2 dual core processor running at an over clocked 2.4 GHz with an ATI XFX Radeon HD 4650 graphics card, I have an 160 gig hard drive and it runs fine with Ubuntu, and my motherboard is a rare RS480-M motherboard that only supports socket 939 CPU's (which AMD no longer makes.) And 2 gigs of RAM. keyboard and mouse are USB devices.

Problem: My Ubuntu is running SO slow that whenever I type it lags, whenever I move my mouse it lags, whenever I open terminal it lags, and pretty much the entire thing lags like hell... I would love to know what the problem with my system and Ubuntu is, I am Running Ubuntu (Latest Version) 32-bit OS, but the thing is that theres so many things that could be causing the problem for the lag. It could be that my CPU is only using 1 of its cores in Ubuntu (which I don't know how to fix), or that I installed the wrong Ubuntu on my machine (I installed intel 32-bit because the amd athlon's only had 64 bit compatible installations which my computer is only 32-bit), or just because my keyboard and mouse are USB and Ubuntu hates it.

If someone could give me an answer why my Linux system is lagging so badly and give me step by step directions (cuz im a noob) I would very much appreciate it. (I do not know if both of my CPU's Cores are being used or not.)

Please Help!

Did you upgrade to 11.04 or was it a fresh install?

---

