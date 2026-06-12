---
title: "xserver won't start - 9.10"
date: 2009-11-08
forum: General Help
---

### Post by schmidtbag on 2009-11-08
so ever since i found the latest version of gnome to be a disaster, i decided to move to kde and i think its amazing.  everything was working fine and then suddenly today i turn on my computer and my graphical interface doesn't work anymore.  i'm taken straight to the CLI login screen on TTY1 and typing "startx" doesn't work.  it leaves me with the error message:
```
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found
```

I have searched for hours on how to fix this.  and yes, i do have nvidia for video, i did reinstall all nvidia drivers (even reverted to older ones), reinstalled the kernel, used depmod -a, used modprobe nvidia, used dpkg-reconfigure xserver-xorg, used nvidia-xconfig, reinstalled grub (i had to remove grub2 because i don't know how to configure it) and now i feel that theres no other option but to reinstall but i REALLY don't feel like doing that after how much time i put into my current setup.

is there any solution?

---

### Post by schmidtbag on 2009-11-08
i managed to fix this problem on my own.  for those of you who have searched for hours like i have, the problem is the nvidia_drv.so file is missing in /usr/lib/xorg/modules/drivers.  in the command line of the defective computer, run:
```
cd /usr/lib/xorg/modules/drivers
sudo cp nv_drv.so nvidia_drv.so
sudo nvidia-xconfig
sudo nano /etc/X11/xorg.conf

```
find the "Device" section that includes 'VendorName       "NVIDIA Corporation"' and under Driver type "nv".
This of course may not turn out to be what you want and could mess with your screen resolution, but it will work.  When (K)ubuntu boots up and the resolution is off, open up synaptic, purge (completely remove) nvidia-185-kernel-source, nvidia-settings, and nvidia-glx-185 (replace the number with your current version), apply, and then reinstall those 3 packages.  reboot, and there you go

---

