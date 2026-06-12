---
title: "nvidia module has to be reloaded constantly"
date: 2006-04-26
forum: General Help
---

### Post by Efwis on 2006-04-26
ok here is my problem.

I compiled my own Kernel for breezy to get my mouse working and to remove modules I don't use. I then installed the latest Nvidia driver so that my OpenGL and 3d graphics work since the kernels drivers don't work properly for me.

now everytime I reboot my computer I have to reinstall the Nvidia driver to have the graphics card work correctly. How can I fix this so I don't have to keep reinstalling the driver?

---

### Post by hw-tph on 2006-04-26
Is the nvidia module listed in /etc/modules? This will make it load on boot.

Here is the /etc/modules config file from my laptop:```

rtc
lp
evdev
tsdev
mousedev
psmouse
sbp2
sr_mod
nvidia
ndiswrapper
realtime
```

Håkan

---

### Post by Efwis on 2006-04-26
[QUOTE=hw-tph]Is the nvidia module listed in /etc/modules? This will make it load on boot.

Here is the /etc/modules config file from my laptop:```

rtc
lp
evdev
tsdev
mousedev
psmouse
sbp2
sr_mod
nvidia
ndiswrapper
realtime
```

Håkan[/QUOTE]
well the nvidia wasn't listed, I added it and I still have to reinstall the Driver module. When I do reinstall I get the following message from the Nvidia driver

> Your driver installation has been altered since it was initially installed. This may happen, for example, if you have since installe dthe driver through a mechanism other then teh NVIDIA-Installer (such as a rpm or with the NVIDIA tarballs.) The NVIDIA-Installer will attempt to uninstall as best as it can. Please see the file `/var/log/NVIDIA-Installer.log for details.
I looked at the log and found one warning issued there about a missing Nvidia.so module.

---

### Post by hw-tph on 2006-04-26
Did you properly uninstall all nvidia related packages before you installed the drivers manually (using nvidia's own installer)?


Håkan

---

### Post by Efwis on 2006-04-26
[QUOTE=hw-tph]Did you properly uninstall all nvidia related packages before you installed the drivers manually (using nvidia's own installer)?


Håkan[/QUOTE]
yes, as a mtter of fact when I went to install it originally I had to recompile my Kernel because I had the Nvidia framebuffer support on.

---

