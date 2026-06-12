---
title: "Please help me get my Nvidia drivers installed"
date: 2010-06-30
forum: General Help
---

### Post by joebob213 on 2010-06-30
Ok, I have had this problem before, searched, found the answer, and fixed it.  I can't find the answer this time :(  

Simply put, Linux and my video card hate each other.  It's a GeForce 6800.  On regular linux distros I can choose safe graphics mode, download the restricted drivers, and all is well.  

Ubuntu Studio, which is what I'm trying to install, doesn't have this safe graphics mode so that's not an option.  

After an install I get a distorted mess of a picture with "Input signal out of range" in the middle.

All guides start with, "Download the latest driver from nVidia.com".  Can't do that without a screen!  

I had a trusty guide printed out that told me how to download and install nVidia drivers for linux using only terminal.  This is what I need, I lost it :(

Can anybody point me in the right direction?

Thanks

---

### Post by mikewhatever on 2010-06-30
How about the recovery mode (usually the second boot option)? The card is by no means new, so I think the driver from the repositories should do. Anyway, if you download and install from nvidia.com, be sure to remove nvidia related stuff from the repositories.

---

### Post by joebob213 on 2010-06-30
> **mikewhatever said:**
> How about the recovery mode (usually the second boot option)? The card is by no means new, so I think the driver from the repositories should do. Anyway, if you download and install from nvidia.com, be sure to remove nvidia related stuff from the repositories.

I have no problem getting to terminal, it's a matter of what commands to use once I get there.

---

### Post by mikewhatever on 2010-06-30
to remove nvidia related stuff
sudo apt-get remove nvidia*

to download the latest driver from nvidia.com:
wget [http://us.download.nvidia.com/XFree86/Linux-x86/256.35/NVIDIA-Linux-x86-256.35.run](http://us.download.nvidia.com/XFree86/Linux-x86/256.35/NVIDIA-Linux-x86-256.35.run)

to run the installer:
sudo ./Linux-x86/256.35/NVIDIA-Linux-x86-256.35.run

---

### Post by dabl on 2010-06-30
> **joebob213 said:**
>  

I had a trusty guide printed out that told me how to download and install nVidia drivers for linux using only terminal.  This is what I need, I lost it :(

Can anybody point me in the right direction?



Here's how I do it:  [http://kubuntuforums.net/forums/index.php?topic=3107406.0](http://kubuntuforums.net/forums/index.php?topic=3107406.0)

mikewhatever has given you the console command to "wget" the driver.

---

