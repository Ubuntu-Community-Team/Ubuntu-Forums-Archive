---
title: "Ubuntu 11.10 64bit NVIDIA Driver Installation"
date: 2011-12-10
forum: General Help
---

### Post by stressed on 2011-12-10
Hello everyone.  This is my first post and first time use of Ubuntu.  

I'm trying to install the latest NVIDIA graphics driver on Ubuntu 11.10 64bit.  I'm installing the Linux x64 290.1 display driver for my PNY GeForce 560 Ti graphics card.  When installing the driver, it stated that I was running an X server and that I had to exit X before installing.  Doing  some research, I found that if I selected CTRL-ALT-F1, I could login and exit X from there.  However, when I select CTRL-ALT-F1, the monitor stops getting any video at all and I have to do a hard restart of the computer.  Any ideas on how I can exit X so I can get my graphics display driver installed?  Any ideas would be helpful and I thank you in advance.

---

### Post by pqwoerituytrueiwoq on 2011-12-10
```
sudo apt-get install nvidia-current
```
if you don't have the version you want add this ppa
**ppa:ubuntu-x-swat/x-updates**

---

### Post by Perfect Storm on 2011-12-10
Have you tried installing the driver via 'Additional drivers' instead? It makes it easy to install Nvidia restricted drivers.

---

### Post by gennatolls on 2011-12-10
> **stressed said:**
> Hello everyone.  This is my first post and first time use of Ubuntu.  

I'm trying to install the latest NVIDIA graphics driver on Ubuntu 11.10 64bit.  I'm installing the Linux x64 290.1 display driver for my PNY GeForce 560 Ti graphics card.  When installing the driver, it stated that I was running an X server and that I had to exit X before installing.  Doing  some research, I found that if I selected CTRL-ALT-F1, I could login and exit X from there.  However, when I select CTRL-ALT-F1, the monitor stops getting any video at all and I have to do a hard restart of the computer.  Any ideas on how I can exit X so I can get my graphics display driver installed?  Any ideas would be helpful and I thank you in advance.

This just worked for me assuming your running lightdm (You should be gdm was the old dm)
```
sudo /etc/init.d/lightdm stop
```

Then I pressed: CTRL+ALT F1
That pulled up a terminal and I logged in.

Then navigate to where you downloaded the Nvidia binary and make it executable if needed. Then run it by:
```
./yourBINhere
```

After setup reboot and it should work.

I had to do this in an Arch Linux setup, you can't have X running to do this because the Nvidia X server needs to blacklist the Noveau Driver (I believe that is the name). As others have mentioned it will be way easier to just use the additional drivers under system settings. Then you won't have to manually update. I strongly recommend using the driver from "Additional Drivers". Nvidia even recommends using the driver distributed by your Linux Distro on the driver page. That how I setup my GeForce 560. It works great for me. Good luck.

---

### Post by pqwoerituytrueiwoq on 2011-12-10
if yuo do what gennatolls said you will have to reinstall the driver after every kernal update

---

### Post by stressed on 2011-12-10
sudo apt-get install nvidia-current 
This command line option did install version 280.13.

I'm wondering how I might be able to update the driver to version 290.1 which is the version that is listed on NVIDIA's driver page at the time of this post.  Does Ubuntu have a way of updating the NVIDIA display driver using a command line as above?

---

### Post by gennatolls on 2011-12-10
You have to wait until Ubuntu releases the driver update. Im running 280.13, I do alot of 3D graphics in Matlab and it works great also watch Blu rays quite a bit. I don't think you will see much if any improvement between the two drivers.

---

### Post by stressed on 2011-12-10
When Ubuntu does release the driver update, will the driver be updated automatically such as a system update or would I have to update the driver manually?  If I have to update the driver manually, is there command line syntax for that?

---

### Post by oldos2er on 2011-12-11
The Nvidia 290.x drivers are available from this PPA: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

