---
title: "Brother MFC-440CN Drivers"
date: 2011-10-10
forum: General Help
---

### Post by Icedrake99 on 2011-10-10
Hey guys! I'm a new Ubuntu user, currently using 11.04, and I've been trying to get my Brother MFC-440CN printer to work. I've gone to the Brother Linux drivers website, and downloaded the LPRS and CUPS .deb files. When I go to install them in Ubuntu Software Center, I get a warning saying that they are unsafe and can cause problems in my system. 

What should I do? I really need to get my printer working; so should I just continue to install it? All the guides I've read/seen just say to install and don't mention the warning message.

Also, I made another thread a while back about the same thing, and I was told then that Ubuntu will most likely automatically find the drivers (which in my case it didn't), and if not, to go to the Linux drivers website which is where I am now.

---

### Post by plucky on 2011-10-11
> **Icedrake99 said:**
> Hey guys! I'm a new Ubuntu user, currently using 11.04, and I've been trying to get my Brother MFC-440CN printer to work. I've gone to the Brother Linux drivers website, and downloaded the LPRS and CUPS .deb files. When I go to install them in Ubuntu Software Center, I get a warning saying that they are unsafe and can cause problems in my system. 

What should I do? I really need to get my printer working; so should I just continue to install it? All the guides I've read/seen just say to install and don't mention the warning message.

Also, I made another thread a while back about the same thing, and I was told then that Ubuntu will most likely automatically find the drivers (which in my case it didn't), and if not, to go to the Linux drivers website which is where I am now.

Open **Synaptic Package Manager** and search for **mfc-440cn** and it should find ```
brother-cups-wrapper-bh7
brother-lpr-drivers-bh7
```
Install them both and the when you **Add a New Printer** you will find the driver for your printer is now installed.

I would advise connecting up the printer using a USB cable just to make sure the printer works.and then you can try getting it to work as a network printer.

If your printer has a scanner,you will still have to go to the Brother Website and download and install the .deb file for your scanner.

Good Luck

---

### Post by Icedrake99 on 2011-10-11
Worked brilliantly, thanks!

---

