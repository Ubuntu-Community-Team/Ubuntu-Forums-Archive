---
title: "nVidia Drivers"
date: 2006-02-10
forum: General Help
---

### Post by kdxrider9262 on 2006-02-10
Hello,
I am running breezy 64 and I have a GeForce 5500 installed that I want to load the video drivers for. Is there a special proceedure that I need to follow or anything special that I have to do? I am running the ubuntu desktop.

Thanks,
Steve

---

### Post by Perfect Storm on 2006-02-10
```
sudo apt-get install nvidia-glx nvidia-settings
sudo nvidia-glx-config enable
smeg
```

click **system tools** and then **New Entry**

Name: Nvidia Settings
Command: nvidia-settings

exit the application and reboot

---

### Post by kdxrider9262 on 2006-02-16
Thanks alot!. now does it matter that im running on a 64 bit version of Ubuntu and that I want the 64 bit driver???

---

### Post by SWAT on 2006-02-17
Uhm, I guess the packages from the repository will work. I myself prefer the drivers from the Nvidia site (in my opinion they are better), and that's why I wrote [this howto](http://www.zwhlug.nl/content/nvidia_nvidia_driver_1_0_8178_installation_on_ubuntu_breezy_5_10)

---

