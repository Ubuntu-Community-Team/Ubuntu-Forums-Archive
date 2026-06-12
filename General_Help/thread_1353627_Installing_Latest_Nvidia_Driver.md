---
title: "Installing Latest Nvidia Driver"
date: 2009-12-13
forum: General Help
---

### Post by Tyrionn on 2009-12-13
Cheers All!!

I am new to Ubuntu and Linux, but like a good little nerd, I tinker till by ankles bleed....

I know how to use the Hardware Drivers for Nvidia, but how do I go about installing the brand-spanking new 195.22 drivers?

Thanks for any information you can toss my way!

---

### Post by staf0048 on 2009-12-13
I'd list the steps, but it's much easier to just give you a link to someone who's already done the work.  

[http://forums.nvidia.com/index.php?showtopic=99513](http://forums.nvidia.com/index.php?showtopic=99513)

By the by, if you're using 9.10, you might not want to use this....

---

### Post by 3Miro on 2009-12-13
People with drivers not from the repos often have to reinstall the thing when a newer version of the kernel comes by. I am sure there is an easy way to do this, but I don't know it.

---

### Post by staf0048 on 2009-12-13
> **3Miro said:**
> People with drivers not from the repos often have to reinstall the thing when a newer version of the kernel comes by. I am sure there is an easy way to do this, but I don't know it.

Simple.  Don't install the new kernels.

---

### Post by Linuxforall on 2009-12-13
sudo apt-get install build essential

Place nvidia driver in home folder.

ctrl+alt+F2
login
sudo service gdm stop
sudo sh NVIDIA and hit tab
say yes to all and after that do a sudo reboot

every time there is a new kernel, do the same, ctrl+alt+F2
login
sudo nvidia-uninstall and then after reboot install the new driver.

---

