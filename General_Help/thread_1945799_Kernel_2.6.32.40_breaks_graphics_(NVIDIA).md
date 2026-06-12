---
title: "Kernel 2.6.32.40 breaks graphics (NVIDIA)"
date: 2012-03-23
forum: General Help
---

### Post by max1e6 on 2012-03-23
10.04 (64)

Hi,

Update manager presented 2.6.32.40 today. I upgraded as suggested.

Restart drops to low graphics mode: (EE) NVIDIA: Failed tp load NVIDIA kernel module (no drivers available).

Selecting 2.6.32.39 at boot starts desktop properly.

My card: NVIDIA 500 series 

The driver which I have installed and working in 32.39 was installed using NVIDIA driver run file (from NVIDIA). This was required for proper OpenGL/GLX on my system.

Can't afford to break and follow smoke on this system.

Is the fix simply to run the "NVIDIA-Linux-x86_XX.run" again on the new kernel?

---

### Post by beanhead on 2012-03-23
If you have need to install the new driver in the kernel and have the nvidia binary driver.
sudo sh nvidiadriverfile. then cp your new xorg.conf to /etc/X11/xorg.conf

---

### Post by Bobhuber on 2012-03-23
You need to reinstall the nvidia.run file every time you update the kernel.

---

### Post by max1e6 on 2012-03-24
Yup, that works. Also had to reinstall the RTL8111/8168B PCI Express Gigabit Ethernet controller. 

Thanks

---

