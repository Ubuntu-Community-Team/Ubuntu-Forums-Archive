---
title: "Will WinXP 64 bit run faster on Ubuntu 64 bit?"
date: 2010-04-26
forum: General Help
---

### Post by sgsawant on 2010-04-26
I currently have the Ubuntu 32 bit 9.10 installed on my laptop. I wanted to install WinXP 64 bit using VirtualBox. My question is: will WinXP 64 bit run faster on Ubuntu 64 bit than it will run on Ubuntu 32 bit (my current OS)? Is the upgrade from Ubuntu 32 bit to Ubuntu 64 bit worth it for running a virtual Windows XP 64 bit?

Regards,

-sgsawant

---

### Post by WinterRain on 2010-04-26
In my opinion, going to ubuntu 64 is worth it, but running xp 64 in virtualbox, will yield little to no noticable results. I run xp 32 in virtualbox, and it absolutely flies. A defrag only took 8 seconds, and it was fairly fragmented. So no, I don't think it's worth it.

---

### Post by sgsawant on 2010-04-26
From your reply I am guessing that 64 bit WinXP in 32 bit Ubuntu will perform almost as well as it will in 64 bit Ubuntu.
Is it because it's actually not running in 64 bit mode and just virtually running in a simulation mode?


I am just curious. By the way thanks for the answer!

---

### Post by 3rdalbum on 2010-04-26
Note: Your CPU needs to have hardware support for virtualisation in order to run a 64-bit guest. Not all Core 2s have this support.

Also, I hear that 64-bit Windows XP is a frustrating experience even when you're running it on real hardware.

And I don't know if you can run a 64-bit guest with a 32-bit host OS in Virtualbox.

**I think ideally you'd use 64-bit Ubuntu as the host and 32-bit Windows XP as the guest.**

---

