---
title: "Crash (Linux kernel) after installing additional drivers"
date: 2012-04-15
forum: General Help
---

### Post by Hannie on 2012-04-15
I use Oneiric in a dual boot system (Windows7 + Oneiric in wubi). WhenI installed the recommended additional drivers for my nVidia GeForce GT 530 I was no longer able to log in using the latest Linux kernel (recover did not work either). I could only log in using a previous Linux kernel. Every kernel update gives me a blank screen (no login screen). I tried restoring login screen with:  Control Alt F1 > sudo cd /etc/x11 > mv ./xorg.conf ./xorg.conf_old > service gdm stop X >  -configure mv ./xorg.conf.new ./xorg.conf > reboot now. But that did not work.
I really would like my GeForce card to be recognized, as I cannot use Unity-3D at the moment.
My 1 TB hard disk has 4 primary partitions, installed by the manufacturer, so I have to use wubi.

---

### Post by Hannie on 2012-04-20
Perhaps the problem lies in the latest nvidia driver (it's a regression in nvidia-drivers 295.40). See:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/980298](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/980298)

---

