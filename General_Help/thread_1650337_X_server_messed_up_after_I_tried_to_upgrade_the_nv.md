---
title: "X server messed up after I tried to upgrade the nvidia driver."
date: 2010-12-21
forum: General Help
---

### Post by colobix on 2010-12-21
Hey. I can't get the graphic to work now. when I start the pc I get this "low graphic" error message.
I have tried 100 guides on the net but nothing seam to work for me.
Idk what nVidia card I have (if that's important).
Under Additional Drivers it tells me that a driver is active but not in use (whatever that's suppose to mean).
Please help me out here. Thanks in advance :)

---

### Post by DarkAmbient on 2010-12-21
lspci | grep VGA

tells you what graphic-card you have. I had the same problem as you 2 days ago, think it's something with the latest kernel upgrade.

There's alot of threads about it allready. :)

heres one, you might find something useful.
[http://ubuntuforums.org/showthread.php?t=1648076](http://ubuntuforums.org/showthread.php?t=1648076)

and the stupid thread I made about it..
[http://ubuntuforums.org/showthread.php?t=1648044](http://ubuntuforums.org/showthread.php?t=1648044)
I managed to fix it after tried lots of different method. But nothing I'd recommend...

---

### Post by colobix on 2010-12-21
Well, I got rid of the error message but this method doesn't actually solve anything. It resets X. If I run nvidia-xconfig to enable the driver, it gets back to low-fraphic mode. Here's the method:

> **sikander3786 said:**
> Try,

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo shutdown -r now
```

Does it get rid of safe graphics now?

So will this be fixed soon? I must say, that I am sick and tired of being your damn beta tester all the time, Ubuntu. As an everyday user I have more than enough things to do with my pc.
People shouldn't feel the need to visit a forum for help and support almost everyday, huh? 

But ok, back to the topic. Can anyone help me with this please?

EDIT: Here's my nVidia card info: 
03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)

So what does this tell you? THat I have the coolest nVidia card? Yea, I know :D

---

### Post by Hippytaff on 2010-12-21
If it's a Kernel issue just boot the previous Kernel.

---

### Post by colobix on 2010-12-21
> **Hippytaff said:**
> If it's a Kernel issue just boot the previous Kernel.
I know, and that's why I don't think this is a karnel issue.
How can I solve this or give you guys the info u need in order to help me here?

---

### Post by Hippytaff on 2010-12-21
You could try highlighting ubuntu at the grub screen (the bit where you choose kernels/OS's) press e then change 'quiet splash' to 'nomodeset' press CTRL+X to boot.

If you boot successfully uninstall and reinstall the driver from addidtional drivers.

---

### Post by colobix on 2010-12-21
nah nothing happened.

---

### Post by Hippytaff on 2010-12-21
Can you boot into low graphics mode? if so have you tried uninstalling and reinstalling the driver?

alternatively you could uninstall and reinstall X.org

edit -> might this be a hardware issue?

---

### Post by colobix on 2010-12-21
**Problem solved!**
After too much crying and bitching on Linux, it finally works:)

OK so here's the guide:

1) Removi all NVIDIA drivers from synaptic (173, current etc)
2) Open up your blacklist.conf file with gedit from root (sudo gedit /etc/modprobe.d/blacklist.conf), and paste in these lines at the end of the file:
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
3) Installing nvidia-settings and nvidia-common (from Synaptic)
4) Reboot
5) Go to Additional Drivers (System>admin), and there you will see 2 new driver choices. Enable the recommended one.
6) Reboot and everything works like a charm.

---

### Post by Hippytaff on 2010-12-22
Glad you got it sorted - job well done sir ;-)

---

