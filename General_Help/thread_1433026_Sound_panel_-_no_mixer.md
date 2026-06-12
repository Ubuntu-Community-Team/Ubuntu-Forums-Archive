---
title: "Sound panel - no mixer??"
date: 2010-03-18
forum: General Help
---

### Post by dd1linux on 2010-03-18
Hi all, minor poblem to solve here.  When I click on the sound icon in the panel (next to the date), I dont get a mixer to change the volume of the line-in, mic, etc.  As a temporary fix, i downloaded aumix from synaptic, and it works perfectly fine.  But I would like to add a link directly into the sound icon in the panel for ease of use (I don't understand why this wouldnt be designed in.)  Any ideas on how to do that?  

I'm running 9.10 on a 64-bit if it helps at all

Please let me know if you need more info

---

### Post by mastermindg on 2010-03-18
Two options:

1) Add a shortcut to aumix on the panel
2) Find/program a panel applet

---

### Post by dd1linux on 2010-03-18
lol, wow, that was easy.  thanks bro.  dont know why i didnt think of that ... must be lack of sleep, lol.  But what I was really looking to do was when i right click on the original icon i was talkin about to get an option to launch aumix from there (just one less icon up there), thats probably pretty complicated tho.

---

### Post by ajgreeny on 2010-03-18
Add a custom application launcer for **alsamixer** run in terminal is possibly the best way to go, and/or install **pavucontrol** if you don't already have it and add a launcher for pulseaudio-volume-control to your panel.

Pavucontrol is a bit different to the old mixer gui, so you may prefer alsamixer.

---

