---
title: "how to use another distro's display drivers?"
date: 2009-07-19
forum: General Help
---

### Post by imtheshade on 2009-07-19
Hi! I am running Ubuntu 9.04 and just can't find any way to make my NVIDIA FX 5200 to work properly on it. I tryed installing another distro, Mepis 8.0 which automatically installed my grafic card's drivers and worked perfectly. Can anyone tell me way to copy the drivers from that distro to this one ? Or is the problem with Ubuntu and I won't ever be able to use my grafic card properly on it ?

---

### Post by pastalavista on 2009-07-19
Check in Mepis to find the kernel version# and also the xserver-xorg version and then try and find a corresponding Ubuntu setup. You may have to revert to an older distro of Ubuntu, probably 8.04 Hardy Heron. It is possible to do. Proprietary drivers can sometimes be used. Have you tried installing envyng? It will search for compiled drivers for Nvidia and ATI cards.

```
sudo apt-get install envyng-core
```

and then run ```
envyng -t
```

---

### Post by imtheshade on 2009-07-19
I tryed envyng. It installed the drivers and the drivers seemed to work, but the highest resolution they let me use was 640x480, whereas now I am typing this reply from a Windows OS with a resolution of 1024x768. What site would u recommend me for downloading hardy ? I remember checking ubuntu's site and not finding it.

---

### Post by pastalavista on 2009-07-19
You can download Hardy here [http://releases.ubuntu.com/hardy/]("http://releases.ubuntu.com/hardy/")

---

### Post by cmost on 2009-07-19
Okay, not to sound arrogant but it's nothing to uninstall Ubuntu's restricted nvidia drivers and then install and compile any version you please directly from nvidia.

Here's where to get the drivers:
32 bit:
[ftp://download.nvidia.com/XFree86/Linux-x86/](ftp://download.nvidia.com/XFree86/Linux-x86/)

64 bit (choose the pkg2 files)
[ftp://download.nvidia.com/XFree86/Linux-x86_64/](ftp://download.nvidia.com/XFree86/Linux-x86_64/)

Download whatever version Mepis is using (that works apparently) otherwise choose the latest version.  Save it in your home directory and remember where!  You'll need it later (e.g., /path/to/downloaded/nvidia/driver)  Note:  For the GeForce 5 series you may need legacy.

Be sure you have the following installed:
linux-headers (for your currently running kernel)
build-essential
...and their dependencies

Now we're ready:
Type the following exactly...
ALT+F1 <to drop to a console>
sudo /etc/init.d/gdm stop <to stop the X server>
cd /path/to/downloaded/nvidia/driver/
sudo sh *.run <begin installation...follow the prompts>
sudo /etc/init.d/gdm start

log in and enjoy Nvidia!

---

### Post by imtheshade on 2009-07-20
I actually solved my graphic card problem by installing ultimate ubuntu. It works great now.

---

