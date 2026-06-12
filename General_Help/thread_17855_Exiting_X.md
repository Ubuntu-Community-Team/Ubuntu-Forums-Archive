---
title: "Exiting X"
date: 2005-03-03
forum: General Help
---

### Post by shrekkie on 2005-03-03
Hi there,
              I am trying to install the Nvidia drivers on ubuntu, but everytime I try to install from the terminal, the installer asks me to quit X and then run the installer again. How do i exactly do this? I am a n00b to ubuntu, so bear with me please :)

---

### Post by my64 on 2005-03-03
[QUOTE=shrekkie]Hi there,
              I am trying to install the Nvidia drivers on ubuntu, but everytime I try to install from the terminal, the installer asks me to quit X and then run the installer again. How do i exactly do this? I am a n00b to ubuntu, so bear with me please :)[/QUOTE]

Reboot your system, type <esc> during boot to get the grub prompt , then choose a kernel in safe mode. After  some setup, the system will ask to continue or type <ctrlD> to enter maintenance mode.
Hit <ctrl D> and when you get the pompt, then you can run the nvidoa installer. 

However, you should preferably  install the debian packages (nvidia-*). It is more clean than the nividia  installation and works fine even on 64 bits systems.

---

### Post by Sgood1971 on 2005-03-03
[QUOTE=shrekkie]Hi there,
              I am trying to install the Nvidia drivers on ubuntu, but everytime I try to install from the terminal, the installer asks me to quit X and then run the installer again. How do i exactly do this? I am a n00b to ubuntu, so bear with me please :)[/QUOTE]

Basically, you need to change your runlevel so you boot to command line. The explanation is kind of lengthy, but the [README](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-6629/README.txt)  at nvidia.com where you downloaded the drivers tells you in pretty good detail how to accomplish this.

---

