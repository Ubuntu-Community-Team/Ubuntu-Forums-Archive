---
title: "New Kernel Boots to Console"
date: 2006-02-20
forum: General Help
---

### Post by Progressive on 2006-02-20
I would like the new kernel I compiled to boot to KDM rather than the console. How do I do this?

Sorry, I am a newbie

---

### Post by codejunkie on 2006-02-20
[QUOTE=Progressive]I would like the new kernel I compiled to boot to KDM rather than the console. How do I do this?

Sorry, I am a newbie[/QUOTE]
will the xserver start if you type ```
startx
``` if not what kind of videocard do you have?

---

### Post by Progressive on 2006-02-20
I have a nvidia geforce Go 6200

... I will try startx

---

### Post by codejunkie on 2006-02-20
[QUOTE=Progressive]I have a nvidia geforce Go 6200

... I will try startx[/QUOTE]
if you installed the nvidia driver and your new kernel through synaptic you just need to install the linux-restricted-modules for your new kernel you can do that with 
```
sudo apt-get install linux-restricted-modules-`uname -r`
```if you compiled the new kernel yourself you'll have to download and install the nvidia driver from [www.nvidia.com](www.nvidia.com)

---

### Post by juanhm on 2006-02-20
I´ve got a similar problem after updating to the new kernel. By now I don´t know how to fix this, but at least I think I can add some details.

My problem is caused by the Nvidia kernel module, assumed that "nvidia-glx" and "linux-restricted-modules" both are installed. Everything was Ok till I upgraded the kernel to "linux-image-2.6.10-12-k7".

I suggest you have a look at "/var/log/Xorg.0.log" and check the error message at the end of the file. If it´s related to Nvidia module too, I quick fix is edit /etc/X11/xorg.conf, look for the entry "Device nvidia" and change it to "Device nv". 

Anyway, this solution implies you loose the 3D hardware acceleration provided by the Nvidia official module.

For anybody that can help with the real problem, this is my situation: as I said, everything was OK before upgrading the kernel. After that, the kernel installed is "linux-image-2.6.12-10-k7" and I´ve also installed "linux-restricted-modules-2.6.12-10-k7". If I try to load the Nvidia module with "modprobe" there´s a problem and it says that "there is no such device" or something like this.

I´ve also tried installing the official binary module form Nvidia web site but nothing changes.

---

### Post by dcstar on 2006-02-20
[QUOTE=juanhm]
........
For anybody that can help with the real problem, this is my situation: as I said, everything was OK before upgrading the kernel. After that, the kernel installed is "linux-image-2.6.12-10-k7" and I´ve also installed "linux-restricted-modules-2.6.12-10-k7". If I try to load the Nvidia module with "modprobe" there´s a problem and it says that "there is no such device" or something like this.

I´ve also tried installing the official binary module form Nvidia web site but nothing changes.[/QUOTE]
The latest kernel update "broke" the Via module I had previously used to give me hardware acceleration.

It seem this kernel already has DRM built into it, do I did a "modprobe -r via" and now I have it all working again.

You may want to experiment with something similar.

---

### Post by codejunkie on 2006-02-20
[QUOTE=juanhm]I´ve got a similar problem after updating to the new kernel. By now I don´t know how to fix this, but at least I think I can add some details.

My problem is caused by the Nvidia kernel module, assumed that "nvidia-glx" and "linux-restricted-modules" both are installed. Everything was Ok till I upgraded the kernel to "linux-image-2.6.10-12-k7".

I suggest you have a look at "/var/log/Xorg.0.log" and check the error message at the end of the file. If it´s related to Nvidia module too, I quick fix is edit /etc/X11/xorg.conf, look for the entry "Device nvidia" and change it to "Device nv". 

Anyway, this solution implies you loose the 3D hardware acceleration provided by the Nvidia official module.

For anybody that can help with the real problem, this is my situation: as I said, everything was OK before upgrading the kernel. After that, the kernel installed is "linux-image-2.6.12-10-k7" and I´ve also installed "linux-restricted-modules-2.6.12-10-k7". If I try to load the Nvidia module with "modprobe" there´s a problem and it says that "there is no such device" or something like this.

I´ve also tried installing the official binary module form Nvidia web site but nothing changes.[/QUOTE]

in order to use the official nvidia driver from [www.nvidia.com](www.nvidia.com) you have to remove all nvidia packages in synaptic first because they conflict with the offical nvidia driver you can do that by running 
```
sudo apt-get remove --purge nvidia*
```
in a terminal then reinstall the nvidia binary driver.

if you wan't to revert to the driver in synaptic after you've installed the nvidia binary driver you have to remove anything that it installed you can do that with 
```
sudo nvidia-installer --uninstall
```
then reinstall the nvidia driver with 
```
sudo apt-get install nvidia-glx nvidia-settings linux-restricted-modules-`uname -r`
```

---

### Post by Progressive on 2006-02-20
startx doesnt work

I changed the device driver and now the new kernel makes some weird color pattern when I startx

X doesn't work at all in the old kernel anymore now that I changed the driver

---

### Post by juanhm on 2006-02-20
For my all the problem was related to the moduel "nvidiafb" loaded by the new kernel. In runlevel 3 I tried "modprobe -r nvidiafb" and then "modprobe nvidia" and it worked.

So if this is your case, just look for a way to disable "nvidiafb" loading by default.

---

