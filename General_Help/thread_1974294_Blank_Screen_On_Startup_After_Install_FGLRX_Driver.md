---
title: "Blank Screen On Startup After Install FGLRX Driver"
date: 2012-05-05
forum: General Help
---

### Post by Silvertongue00 on 2012-05-05
Hello there, I'm total noob at ubuntu. I've tried my best to google my problem but I haven't found solution, so I make thread to ask someone to help me.

I have problem with FGLRX driver installation, I have tried several method to install it but none worked. When I installed FGLRX, I always got blank screen after startup. I've tried to install from **System Settings > Additional Drivers** then I tried post release update and normal one, but neither of them are working. I also tried to install from terminal and full console but neither of them are working as well. I use this command to install and uninstall FGLRX driver.

```
sudo apt-get --purge remove fglrx*

sudo apt-get install fglrx-updates fglrx-amdcccle-updates
```

from my local forums, I got information that I need to update my kernel to PAE version using this command, obviously this is not working too.

```
sudo apt-get update
sudo apt-get install linux-image-3.2.0-24-generic-pae linux-headers-3.2.0-24-generic-pae
```

I use Radeon HD 6790 and this is result **lspci | grep VGA**

```
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Barts LE [AMD Radeon HD 6700 Series]
```

I really appreciate every single bit help you give me, thanks :)

---

### Post by brainwash on 2012-05-05
After installing the driver and before rebooting you have to run this command to create a new Xorg configuration file (/etc/X11/xorg.conf):
```
sudo aticonfig --initial
```

---

