---
title: "installing the latest nvidia drivers"
date: 2009-07-25
forum: General Help
---

### Post by diggedy on 2009-07-25
According to nvidia and many other sites Ive visited, the latest drivers for my card are 185.18.14.

Im running ubuntu 64 bit and my card is a 8800gts. According to any google searches I should be able to update the drivers via the system update or using EnvyNG, however both of these tell me the latest driver is 180.

Ive downloaded the pkg2 file from nvidia but have no idea how to install it. Can nayone give me any pointers?

---

### Post by abhi90 on 2009-07-25
for that you have to download packages of Nvidia 185.18.14.
just go to the pakages.ubuntu.com  and search for Nvidia

---

### Post by DeMus on 2009-07-25
> **diggedy said:**
> According to nvidia and many other sites Ive visited, the latest drivers for my card are 185.18.14.

Im running ubuntu 64 bit and my card is a 8800gts. According to any google searches I should be able to update the drivers via the system update or using EnvyNG, however both of these tell me the latest driver is 180.

Ive downloaded the pkg2 file from nvidia but have no idea how to install it. Can nayone give me any pointers?

The latest version I found on ppa.launchpad.net/main is 190.18. Have a look there.

---

### Post by Soul-Sing on 2009-07-25
yep via this: [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates) your pretty "safe". X updates are a bit tricky, if done
outside the regular Ubuntu updates, because X could break after a kernel update/upgrade.

---

### Post by kpkeerthi on 2009-07-25
> **diggedy said:**
> According to nvidia and many other sites Ive visited, the latest drivers for my card are 185.18.14.

Im running ubuntu 64 bit and my card is a 8800gts. According to any google searches I should be able to update the drivers via the system update or using EnvyNG, however both of these tell me the latest driver is 180.

Ive downloaded the pkg2 file from nvidia but have no idea how to install it. Can nayone give me any pointers?

There are many guides in the Tutorials & Tips section.

---

### Post by diggedy on 2009-07-25
> **DeMus said:**
> The latest version I found on ppa.launchpad.net/main is 190.18. Have a look there.


thanks for the help everyone. I can still only see the 180 drivers looking on here though

---

### Post by DeMus on 2009-07-25
> **diggedy said:**
> thanks for the help everyone. I can still only see the 180 drivers looking on here though

Found the website. It is:

[http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-190/]("http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/pool/main/n/nvidia-graphics-drivers-190/")

Here you find all kind of nVidia drivers for different systems.

---

### Post by 3rdalbum on 2009-07-25
Do you absolutely need the latest drivers? Are you having problems with your setup?

The reason I ask is because the greatest degree of testing has been done with Ubuntu running your existing video card driver. If you install a later version of the Nvidia driver, it could open up graphics problems or affect the stability of your computer. Also, unless you set up the Nvidia driver to rebuild automatically, it will require reinstalling whenever you update the kernel, and after some Xorg updates.

If you really want to install the graphics card driver, there are HOWTOs here that must be followed to the letter; it requires removing the old driver fully and installing the new driver. Alternatively there are instructions on the download page at Nvidia.com, that don't mention about using Synaptic to remove the "nvidia-glx-180*" packages.

---

### Post by DeMus on 2009-07-25
> **3rdalbum said:**
> Do you absolutely need the latest drivers? Are you having problems with your setup?

The reason I ask is because the greatest degree of testing has been done with Ubuntu running your existing video card driver. If you install a later version of the Nvidia driver, it could open up graphics problems or affect the stability of your computer. Also, unless you set up the Nvidia driver to rebuild automatically, it will require reinstalling whenever you update the kernel, and after some Xorg updates.

If you really want to install the graphics card driver, there are HOWTOs here that must be followed to the letter; it requires removing the old driver fully and installing the new driver. Alternatively there are instructions on the download page at Nvidia.com, that don't mention about using Synaptic to remove the "nvidia-glx-180*" packages.

I agree with you: there is no absolute need to use the latest driver, BUT the one I use now (190.18) is faster than the 180.44. For me it runs stable, I have no issues with it. (tested or not tested by Ubuntu)
With the right repos installing them, and un-installing the previous ones, is simple enough using Synaptic so that should not be a problem.

If the improvement of the new driver is not really necessary and you have a stable installation at the moment, stick with the one you have now. Especially if you are still new to Linux and Ubuntu. Installing it could damage your installation, ending up in a command line interface screen, from which you have to try restoring the old driver with the correct resolution.

I must say this: why is it so hard to update a video-driver in Linux? When I do this in Windows it's a piece of cake. Why can't it be like that in Ubuntu? Why is the chance something goes wrong so gigantic, leaving us with a command line, fooling around with text files and complicated instructions?
Is it Ubuntu, is it Linux in general or is it caused by the manufacturers of the graphical cards and their drivers?

---

### Post by diggedy on 2009-07-25
I am having some graphic instabilities, im unsure if it was the driver but I figured it was something to check. If theres a chance its going to destroy my system then ill leave it for now and come back to it as a last resort.

thanks for the help

---

### Post by jmszr on 2009-07-25
diggidy,

I noticed this thread in the Community Cafe: [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978). It is rather long, but you may find it of some interest.

---

