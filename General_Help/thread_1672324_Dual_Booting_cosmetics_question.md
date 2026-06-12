---
title: "Dual Booting cosmetics question"
date: 2011-01-20
forum: General Help
---

### Post by helios16v on 2011-01-20
I have an HP and the whole boot process is pretty clean and "pretty" as the whole bios boot process is hidden behind the HP splash and then by the time its all loaded it just goes straight into the Ubuntu splash but since I dual booted Windows 7 in there, it brings me to that text screen where I choose between all the different ubuntu environments or windows 7.

Is there anyway to run a graphic boot loader so I can just pick between a Ubuntu logo and Windows logo?

-Ben

---

### Post by garvinrick4 on 2011-01-20
> **helios16v said:**
> I have an HP and the whole boot process is pretty clean and "pretty" as the whole bios boot process is hidden behind the HP splash and then by the time its all loaded it just goes straight into the Ubuntu splash but since I dual booted Windows 7 in there, it brings me to that text screen where I choose between all the different ubuntu environments or windows 7.

Is there anyway to run a graphic boot loader so I can just pick between a Ubuntu logo and Windows logo?
  
-Ben No you are running grub2 and it shows the menu entries in the config file
to choose to boot into. When you only have one menu entry it will by default go straight into that install. 
But with 2 or more you have to have somewhere to select from then a nice splash screen.

---

### Post by helios16v on 2011-01-20
I'm just wondering if there is different boot loaders I can use to select which os to start in. I found lots of stuff about graphical boot loaders when I was looking into making this a hackbook (osx86) for triple booting windows 7, ubuntu, and osx. those screens simpled showed three logo's to choose from with the left and right keys on the keyboard.

I'm just wondering if theres anything like that for only windows 7 and ubuntu without all the osx86 bootloader stuff.

-Ben

---

### Post by garvinrick4 on 2011-01-20
Do not know but if you keep looking report back to this thread and tell us what you have found out there. A graphical boot menu entry with I nice little collection of icon's would make new users not freak out as much as when they see actual text on there monitor. grub2 has not been used that long and only on debian that I have used. Seems the other major players down the line from Ubuntu all still use grub legacy so I would not be surprised in time if it is an option in grub2.

---

### Post by Quackers on 2011-01-20
It may be worth looking at BURG

[https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

---

