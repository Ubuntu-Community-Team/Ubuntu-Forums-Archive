---
title: "[nvidia] Can someone explain me this ?"
date: 2009-07-22
forum: General Help
---

### Post by kpkeerthi on 2009-07-22
I have two kernels installed - the stock 2.6.28.x and the latest 2.6.30.2 that I compiled from source.

My GPU is nvidia and I have the binary driver, downloaded off nvidia's website, installed. I'm not using the driver from Ubuntu's repository.

After installing the new kernel, I uninstalled the nvidia driver (using **sudo sh ./NVIDIA-Linux-x86-185.18.14.pkg1.run --uninstall**). Then, booted up the new kernel. X complained of no driver module 'nvidia'. Perfectly fine upto now: the driver has been completely wiped from the old 2.6.28.x and I am yet to install it under 2.6.30.2. So I went ahead and installed the driver (using **sudo sh ./NVIDIA-Linux-x86-185.18.14.pkg1.run**). Rebooted into 2.6.30.2 and X came up now. 

What surprised me was that when I booted into 2.6.28.x, X continued to work. I'm wondering how could this possibly work as the nvidia kernel modules are available for 2.6.30.2 only?

---

