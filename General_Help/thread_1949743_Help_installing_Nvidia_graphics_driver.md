---
title: "Help installing Nvidia graphics driver"
date: 2012-03-30
forum: General Help
---

### Post by KeithLostracco on 2012-03-30
Hi I'm pretty much a newbie to Linux and have just installed Ubuntu. I would like to run the newest Nvidia graphics driver for the two graphics cards installed in my machine. Yesterday I tried with a friend to install a downloaded driver from the Nvidia site and my friend came to the conclusion that I would need to recompile Ubuntu without the Nouveau driver in order to install the Nvidia driver. 

So today I thought I would search the forums and found in a thread that I could type

```
sudo apt-get install nvidia-current
```to install the driver. I did that and it seemed to install something but there are no settings/control panel or changes to the OS.

I hoping someone could point me in the right direction to install the correct driver for the 2 Nvidia Quadro5000 video cards in my machine. 

thanks
Keith

---

### Post by jerome1232 on 2012-03-30
If you click your dash, and search for nvidia, it should pull up the nvidia x server settings, click on that to see your driver version, information about your setup, and make changes to the x server.

Unless your trying to setup dual monitors or something default settings should be fine.

If that gui complains that your not using the right driver try running nvidia-xconfig, then rebooting.

```
sudo nvidia-xconfig
sudo reboot
```

---

### Post by efflandt on 2012-03-31
It is best to install the nvidia drivers using **Additional Drivers** in **Dash**.

One thing to note is that for 11.10, I had to use **nomodeset** kernel boot parameter (I did not need to use that in 10.10).  Try adding that to this line of /etc/default/grub, with **gksu gedit** (or **sudo nano** in a terminal), and afterwards, run **sudo update-grub**

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```If you try to install drivers directly from nvidia, that becomes a maintenance headache because the system does not know you have them, so new kernels would not have proper modules and you may have to reinstall nvidia drivers after kernel updates.

Even using apt-get sometimes does not work properly (not sure if **nvidia-settings** also needs to be installed separately when using that).  Before I was using nomodeset, I tried using apt-get to install nvidia-current along with Additional Drivers to enable or disable them and messed up my system enough that I had to reinstall 11.10 to fix it.

If you need newer nvidia driver version that nvidia-current, add x-swat to your repositories before using Additional Drivers.  Or if drivers are already installed disable them in Additional Drivers, reboot, then enable them after x-swat has been added.  But that might not work if you already used apt-get to install nvidia-current.

To add x-swat:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```

---

### Post by KeithLostracco on 2012-03-31
Thanks guys I'll try your suggestions. 

thanks
Keith

---

### Post by BicyclerBoy on 2012-03-31
Note:
The nVidia driver kernel module will not load if you use "nomodeset".

All the recent X server drivers require kernel mode settings (nVidia AMD intel).

---

