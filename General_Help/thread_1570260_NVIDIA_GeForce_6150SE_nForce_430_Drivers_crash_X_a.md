---
title: "NVIDIA GeForce 6150SE nForce 430 Drivers crash X and (by extension) GDM."
date: 2010-09-07
forum: General Help
---

### Post by Tng222 on 2010-09-07
I have a non-OEM built desktop, which I recently installed Ubuntu 10.04.1 on, it has a NVIDIA GeForce 6150SE nForce 430 on the motherboard, and i can't get it to work properly. In past versions of Ubuntu on this computer, I could install the driver, easily, when prompted if I chose to enable desktop effects; then it would reboot and work smoothly. But, for some reason, when I try this on 10.04.1, it reboots, and X and GDM seem to just crash, it flashes green on the screen, then drops to a command line. 

Well, I didn't know what to do, so I reinstalled Ubuntu, installed the driver when prompted, but then, before I rebooted, I searched in Synaptic for anything "nvidia" and I got a list of the nvidia packages installed:

nvidia-173
nvidia-173-modaliases
nvidia-96-modaliases
nvidia-common
nvidia-current-modaliases
nvidia-settings

So I rebooted to, again, find X and GDM crashed and at a command line. Then, I logged in  and did, sudo apt-get remove nvidia-173. I rebooted to find that it gave me the choice of reconfiguring X, going to command line, restarting X, loading GDM in low-graphics mode, or troubleshooting it. As it didn't really fix anything, I went to the command line, logged in, and did, sudo apt-get purge nvidia-*, to remove it all, and then install the driver I got from [http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html](http://www.nvidia.com/object/linux-display-ia32-256.53-driver.html)

It didn't work. Instead of letting me go into the low-graphics mode, it just dropped right to a command line after tons of junk flashed on the screen. Now, I don't know what  to do, or how to uninstall this driver. What can I do to get this working?

Well, that's my Tuesday night story :D

Help is extremely appreciated! If I can't solve this, then I'll abandon the idea of Ubuntu on this computer, then maybe try OSx86, and as a last resort, Windows 7.

Thanks!!!!

---

### Post by ellgor on 2010-09-08
Hi,

I found this guide that should help you out:

1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have, be precise as errors will result in "no such file"
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Regards, Ellgor.

---

### Post by Tng222 on 2010-09-08
Thanks for your input, but it still doesn't work; tried your steps from the command line (considering that I can't get a GUI to run) and I reinstalled the official driver, and GDM still can't load.

---

### Post by TuxGirl on 2010-10-14
Not very helpful, but for what it's worth, I am having the same problem.  I was able to get back in by removing the driver, but I'm very frustrated with not being able to use the driver.

---

