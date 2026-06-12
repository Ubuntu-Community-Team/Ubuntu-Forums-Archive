---
title: "Create a one-time windows boot script to use on vnc."
date: 2011-07-30
forum: General Help
---

### Post by snoopo71 on 2011-07-30
Hi, I'd like to be able to choose the OS to be booted on the next start, remotely. I explain, I've a dual boot win7/Kubuntu and I regularly use VNC connections to remotely control my PC but I've a problem, if I remotely edit my grub to start on Windows(I change the default option,save and reboot), I can't start again on Kubuntu, at least without being physically in front of the PC... . Any idea on how to edit the grub for only one time?

Thanks for all

---

### Post by gordintoronto on 2011-07-30
You can edit grub to reboot to "the same OS as last time." That's the way my machine is set up, but I forget how. Google....

---

### Post by snoopo71 on 2011-07-31
Thx gordintoronto but this is not what I need. I'll try to explain it a better way, imagine that:
My default OS in the grub is kubuntu, I start my PC and obviously go to kubuntu, then I access it remotely through a VNC connection and I want to reboot it to windows, so I remotely edit my grub conf to start on windows chanching my grub's default OS to win7, I save and reboot. My pc starts on win7, I access it again with a VNC comnection, do my work on win and want to go to kubuntu again, but if I restart the computer my Grub is still with win7 as default OS, so I won't be able to go to kubuntu until I get to my home and restart my computer physically and choose kubuntu in the grub menu.. I don't know if I've explained myself, what I want is to be able to boot one time to win7 and ho again to kubuntu without need to be in front of my pc. Thx to all and sorry for my english.

---

### Post by gordintoronto on 2011-07-31
Your description was very clear, but I don't have a solution.

---

### Post by snoopo71 on 2011-08-04
Thank you gordintoronto!!

---

