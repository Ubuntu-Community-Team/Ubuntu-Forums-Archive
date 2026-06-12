---
title: "X windows auto-detected configuration"
date: 2010-12-10
forum: General Help
---

### Post by robsonr on 2010-12-10
Hi everybody,

I run at home Ubuntu 9.10 with Asterisk PBX on it. I have a VGA switch box I would like to use to with this server and other PCs I have. When I tried to connect this Ubuntu server to this VGA/keyboard/mouse switch box within one day server crashes. I test it couple time. As soon as I get it off the switcher it runs no problem for months. 
I tried to make modifications to X windows configuration, but I had not much success. 
I contribute crashing to auto-detection feature of X windows, where some X windows parameter is set differently when connected to switch box. When connected to switch, max resolution is limited to 1024x768, but I'm enforcing it to 1600x1200. I also tried not to keep this low resolution, but it didn't help. The server still crashed.

What I would like to do if possible, to connect my ubuntu directly to monitor and capture at that point running X windows configuration. At the next step I would enforce same configuration for X window but using VGA switch box. If there a way to do it?

Do you have any other suggestions I could do? 

I cannot afford this box crash, because it takes down whole home phone system.

Thank you in advance for your help and suggestions.

---

### Post by Wtower on 2010-12-10
I had a similar issue once, until I decided to completely remove that pc from the screen switch and login remotely with x11vnc. Of course this is not recommended if you use that pc a lot.

Regards

---

