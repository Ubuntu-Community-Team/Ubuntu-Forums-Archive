---
title: "xorg driver"
date: 2010-06-01
forum: General Help
---

### Post by beradero on 2010-06-01
Hi all,
I started using 10.04 today and it seems that the xorg.conf file disappeared.. 
It's the first time that the default xorg dirver works for my nvidia card, and I want to know what drive is this..
How can I know what xorg driver the system is using? Is there a command for that?

---

### Post by dino99 on 2010-06-01
with lucid the kernel directly deal with X, so no need xorg.conf by default.

with a nvidia card: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings have to be installed (check into synaptic), and activated (look at: "system admin hardware driver")

---

### Post by beradero on 2010-06-01
synaptic shows that a myriad of drivers are installed.. 'system admin hardware driver' shows three proprietary drivers I can install.. I still don't know what driver the system is using..

---

### Post by dino99 on 2010-06-01
> **beradero said:**
> synaptic shows that a myriad of drivers are installed.. 'system admin hardware driver' shows three proprietary drivers I can install.. I still don't know what driver the system is using..

that is shown by a "light green radio box" if its activated. You need to select nvidia-current and validate your choice by pressing the button on the bottom right

---

### Post by beradero on 2010-06-01
Almost all the xserver-xorg-video drivers are marked as installed (with a green box).. Synaptic is not the place to look what video drive I'm using..
And I don't want to activate other driver with  'system admin hardware driver'..

---

### Post by beradero on 2010-06-02
I found it in /var/log/Xorg.0.log.. I'm using nouveau..

---

