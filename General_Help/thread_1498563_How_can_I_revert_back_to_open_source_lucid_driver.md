---
title: "How can I revert back to open source lucid driver?"
date: 2010-05-31
forum: General Help
---

### Post by myk02k on 2010-05-31
Hey guys, so I made the error of installing FGLRX on lucid. After the install, Plymouth resolution sucks and my laptop will not come out of suspend/hibernate. When I use jockey-gtk to disable FGLRX, it will not allow me to use compiz for 3d graphics. However, out of the box, I was able to run compiz no problem.

How can I revert lucid back to factory form, where it was able to perform 3d acceleration without the use of FGLRX?

---

### Post by clhsharky on 2010-06-01
myk02k

```
sudo apt-get remove --purge xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
sudo dpkg-reconfigure xserver-xorg
sudo restart gdm
```

Make sure "fglrx" is not listed in /etc/modules file

Sharky

---

### Post by myk02k on 2010-06-01
xorg-driver-fglrx didn't exist. What I did was 'sudo apt-get remove --purge fglrx fglrx-kernel-source fglrx-amdcccle'. Something is still not right on boot, though. I'm getting an error that it cannot find modules glx and fglrx.

---

### Post by myk02k on 2010-06-01
OK, I used the system prompt to restore generic display configuration. However, now I cannot enable desktop effects. :-(

---

