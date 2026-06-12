---
title: "Driver for GEForce 6200"
date: 2009-11-06
forum: General Help
---

### Post by rktompsett on 2009-11-06
Is there any driver upgrades for Ubuntu running a Navidia GEForce 6200 graphics card at 512mb?

---

### Post by wrgb2 on 2009-11-06
There are NVIDIA proprietary drivers available.  Have you run System > Administration > Hardware Drivers?  This will do an automatic search for any available third-party drivers.

---

### Post by rktompsett on 2009-11-06
Randy,

Thanks for the info.

Rob

---

### Post by orengolan on 2010-06-12
thank you wrgb2 but I don't use gnome/kde/xfce.
is there another way to find what drivers will fit my 6200?

can someone on this thread run dpkg -l |grep nvidia
and let me know what packages are installed so I'll install them as well.

thank you!

---

### Post by altonbr on 2010-09-12
Did that work for you? Because I've had nothing but problems with Ubuntu and my nVidia GeForce 6200... 9.10 Karmic and 10.04 Lucid. Thinking of trying Maverick just cause.

---

### Post by orengolan on 2010-09-12
I got it working on my HP desktop with the following packages:

[LIST]
[*]nvidia-current                       
[*]nvidia-glx-185                        
[*]nvidia-settings
[/LIST]

I hope it helps.

---

### Post by bobo747 on 2010-09-12
I got graphic problem. My Card is Nvidia Geforce 6200 128MB. I update the driver but Internet Connection is slow and sometime, connection is drop. Update was stop in middle. And I try again when connection is good. But I got Error Message. I can't activate driver.
Driver is also disable.Please help me. I am ubuntu new user. ubuntu is 10.04. (By the way, I am from myanmar and sorry for my English)

---

### Post by altonbr on 2010-09-12
> **bobo747 said:**
> I got graphic problem. My Card is Nvidia Geforce 6200 128MB. I update the driver but Internet Connection is slow and sometime, connection is drop. Update was stop in middle. And I try again when connection is good. But I got Error Message. I can't activate driver.
Driver is also disable.Please help me. I am ubuntu new user. ubuntu is 10.04. (By the way, I am from myanmar and sorry for my English)
My question to you would be 'do you need it?' The open source drivers (the one that are installed by default) work for most and are useful for most purposes (except graphic-heavy applications like games). Other than that, it just sounds like your connection is timing out.

---

### Post by ellgor on 2010-09-13
Hi,

I read somewhere that the Nvidia drivers for some reason don't get loaded in correctly, giving problems all round, I found a guide that gets them in and running properly:

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

Note: When I ran this I got an error message "Unable to find kernel source tree", so I ran:
$ sudo apt-get install linux-headers -`uname -r'

then ran the installer again

8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

Regards, Ellgor.

---

