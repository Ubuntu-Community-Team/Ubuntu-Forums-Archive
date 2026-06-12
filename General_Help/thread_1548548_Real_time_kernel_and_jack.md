---
title: "Real time kernel and jack"
date: 2010-08-08
forum: General Help
---

### Post by oleink on 2010-08-08
hey I just installed a real time kernel but jack won't let me start with "realtime" checked in qjackctl. (Yes I booted to the real time kernel and am not on the generic)

As a side question:
Before I did a fresh install of 10.04 I had a menu come up that allowed me to select my kernel while booting and I cannot do that now...?  I use startupmanager in the terminal to select when changing kernels on boot but I'd like that menu

---

### Post by jbrown96 on 2010-08-08
Realtime Jack has nothing to do with the kernel. It's an enhanced mode for pulseaudio. 

Start [here.]("http://ubuntuforums.org/showthread.php?t=453486")

---

### Post by oleink on 2010-08-08
> **jbrown96 said:**
> Realtime Jack has nothing to do with the kernel. It's an enhanced mode for pulseaudio. 

Start [here.]("http://ubuntuforums.org/showthread.php?t=453486")

ok thanks.  I read somewhere you didn't have to change limits.conf with the newest release but idk musta been a lie

---

