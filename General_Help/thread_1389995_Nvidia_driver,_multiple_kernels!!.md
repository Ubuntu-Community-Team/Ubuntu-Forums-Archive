---
title: "Nvidia driver, multiple kernels!!"
date: 2010-01-25
forum: General Help
---

### Post by scooter1556 on 2010-01-25
I am using the latest Nvidia driver from their website on Ubuntu 9.10. I use 2 kernels, the standard kernel for everyday use and the realtime -rt kernel for my music work. On my desktop i have standard ubuntu and ubuntu studio installed but on my laptop its annoying having to have an external hard drive plugged in when i want to record so i just switch between kernels on a standard install. The problem is i have to reinstall the nvidia driver every time i switch between them or if the kernels get updated (which i don't mind so much). Is there any way i can install the driver so that it configures x.conf to work with both kernels without having to reinstall each time?

---

### Post by m0o on 2010-01-25
Follow [this tutorial]("http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html") and use that method to install NVIDIA drivers from now on in Ubuntu installations, it's less tedious to maintain. It seems to be pretty up to date with the latest drivers also.

---

### Post by Linuxforall on 2010-01-25
Only nvidia drivers compiled in the repository by Ubuntu devs work with the rt kernel, nvidia ncurses based drivers don't work with real time kernel.

---

### Post by pbrane on 2010-01-25
> **Linuxforall said:**
> Only nvidia drivers compiled in the repository by Ubuntu devs work with the rt kernel, nvidia ncurses based drivers don't work with real time kernel.

How so? When I install an nvidia driver from the nvidia site it compiles for the kernel I'm using. It would seem that this would work for any running kernel.

If the nvidia drivers in the repos are compiled for a specific kernel then I can understand, assuming the rt kernel driver is not in the repos. 

In that case I would recommend using this method to install the drivers from nvidia. [http://ubuntuforums.org/showthread.php?t=1125400]("http://ubuntuforums.org/showthread.php?t=1125400")
This is what I do and the nvidia drivers are recompiled for each new kernel and not removed from the previous kernel.

---

