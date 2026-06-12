---
title: "Linux Will Not Detect My Hard Drives"
date: 2011-02-25
forum: General Help
---

### Post by Ferret* on 2011-02-25
Ok so before i begin i want to thank all of you for you're time and i also want to say that i am a COMPLETE noob when it comes to linux so i am going to need things explained to me in a way that would be easy for a child to understand. For about 5 months now i have been trying off and on to get linux working on my computer, i have tried 7 different distros ranging from Elive,Opengeu,MoonOS,ManhattanOS,Linux Mint,Kubuntu,Ubuntu and each one brings me the same results. (all the distros give me the same results but since we are on the ubuntu forums ill just talk about ubuntu) Ill boot into ubuntu 10.10 using the live cd, it brings me to the menu where it asks me if i want to install or try, i will click install and then it will show a grey X next to "Has atleast 2.6gb of available drive space" a green check for  "is plugged into a power source" and a green check next to "is connected to the internet". i have tried switching my HDD settings from enhanced to compatable, switching to IDE mode, i have tried unplugging just one of my satas and using an old sata (which HAS had linux on it before), switching the sata ports,using a usb dvd drive instead of my sata dvd drive,have checked to make sure all connections are secure 3 times over, and nomatter what i do it just will not let me install linux.

Btw my mobo is a Asus p6x58d

my HD's are a Western Digital Caviar Green WD10EARS 1TB SATA 3.0Gb/s 3.5 and a WD500aaks 500gb

---

### Post by zenwalker on 2011-02-25
Mines to western digital, but a different model. But alas Linux should support it. 

Any ways, when your on live cd, just posts here whats the out put of 

lspic
lsusb 

commands in terminal as root.

---

### Post by Ferret* on 2011-02-25
O also, i dont know if this helps but in my bios at the main part it says sata 1-6 and all of them say not detected, so it is not detecting either of my hard drives, but if i goto boot order it DOES see my WD10ears hard drive but not my WD500aaks HD

---

