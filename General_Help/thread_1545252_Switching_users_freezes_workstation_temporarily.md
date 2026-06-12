---
title: "Switching users freezes workstation temporarily"
date: 2010-08-03
forum: General Help
---

### Post by RayDeCampo on 2010-08-03
I have been experiencing issues when switching users since my last update; I filed a bug, but I was interested if anybody else was having the same problem:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/612829]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/612829")

In a nutshell the computer freezes temporarily during the switch user process.  The longer it is running, the longer the freeze lasts.  When frozen the screen is black except for a mouse pointer; but the mouse and keyboard are not responsive including the usual X command keys (Ctrl-Alt-Del, Ctrl-Alt-Bksp, Ctrl-Alt-F1, etc.).

When I get the chance I am going to rollback gdm to see if that makes a difference.  If anybody has any other suggestions, let me know.

---

### Post by SentientFluid on 2010-10-12
I don't know if you solved this or not but if you are using the nvidia drivers on 10.04 here's what fixed it on my system:
```
cd /tmp
wget http://mirrors.kernel.org/ubuntu/pool/restricted/n/nvidia-graphics-drivers-173/nvidia-173-kernel-source_173.14.28-0ubuntu1_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/restricted/n/nvidia-graphics-drivers-173/nvidia-173_173.14.28-0ubuntu1_i386.deb
wget http://mirrors.kernel.org/ubuntu/pool/main/n/nvidia-graphics-drivers-173/nvidia-173-modaliases_173.14.28-0ubuntu1_i386.deb
dpkg -i nvidia*deb

```

That will download and then install the nvidia 173 drivers used with 10.10 which do not have this bug.

Of course another option would be to upgrade to 10.10. :)

---

