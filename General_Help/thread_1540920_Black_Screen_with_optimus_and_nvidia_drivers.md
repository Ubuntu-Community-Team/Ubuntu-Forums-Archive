---
title: "Black Screen with optimus and nvidia drivers"
date: 2010-07-28
forum: General Help
---

### Post by neven on 2010-07-28
Hello,
I have Asus N61jv laptop with optimus, and i use ubuntu 5-6 months, i know that i can't use my nvidia graphic card, today ubuntu offered to install nvidia drivers and I accidentally clicked, after restart i see only black screen, can someone explain me how to get back to a previous state, i found some topic with this solution "...except booting to a live cd and disabling gdm.". How can i fix this problem, i have important data on ubuntu?

Tnx

---

### Post by dino99 on 2010-07-28
when you boot, select the boot line into the grub menu (if hidden, hold "shift" key down at end of bios process) and:

- edit it: "E"
- remove : quiet splash, so see comments when booting
- add: video=vesa
- boot: "X"

hope it will boot, then modify xorg.conf by removing "nvidia" and replace by "nouveau" (should be that previously i guess)

( sudo gedit /etc/X11/xorg.conf)

---

### Post by neven on 2010-07-28
I don't think this is important but i have dual boot on laptop ubuntu and windows 7, i installed before some program on ubuntu that after choosing ubuntu next thing to show is loading and login, so now when i try any command including hold shift it doesn't do anything.

---

### Post by neven on 2010-07-28
I have live cd with me is there some way i can fix this from live cd?

---

