---
title: "Not loading into desktop environment, get error"
date: 2011-02-04
forum: General Help
---

### Post by Rikeshar on 2011-02-04
Hello all, I've got Ubuntu 10.04 LTS installed dual-boot on my pc alongside Windows 7. When choose Linux in the grub menu, it loads to a black, dos like screen with:

[17.642524] tpm_tis 00:0b: tpm_transmit: tpm_send: error -62

And then asking for my user name and password. If I enter my user name and password it comes up to the command prompt, and I can type in startx to get into the desktop. If I just leave it on the prompt asking for my user name and password, then between 30 seconds and 2 minutes, it will automatically load into the desktop. Any ideas?

I'm still pretty new to Ubuntu so I'm not entirely sure where to get the system specs from, to post those.

---

### Post by Rikeshar on 2011-03-30
Solving out this old thread. Issue was that the display driver. Activing the restricted ones was screwing things up.

---

