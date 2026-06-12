---
title: "dual monitors stopped working after 10.10 kernel update"
date: 2010-11-26
forum: General Help
---

### Post by manubbo on 2010-11-26
Hi guys,

I'm running Ubuntu 10.10 64 bit on a machine with nVidia 8400 GS card installed. before the update to kernel 2.6.35, dual monitors were running correctly (among the Xinerama issue that caused some applications to hang - but I was using separate screens instead). This morning I updated to the new kernel, and it stopped recognizing my second monitor (DVI one). Tried to install all alternative drivers from nVidia, either from synaptic and from their website, but nothing's working. It simply does not detect second monitor.

I may try replacing that card with an ATI one (an old Radeon 9250, it doesn't matter because I'm using it for development - only like visual effects and 1280x1024 resolution, but nothing more!), but I don't know if this is going to improve something.

Anyone could help?

Thanks.

---

### Post by dino99 on 2010-11-26
now kernel directly deal with X, so old xorg.conf often push the mess :(
If you need special settings (like with crt) then rename it to xorg.conf.old

then: sudo rm -f /etc/X11/xorg.conf

into synaptic:
- remove/purge ALL the nvidia installed packages

- install this ppa: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
- update
- install: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

reboot, check driver activation, then use nvidia-settings

---

### Post by Cc7IyImJKz on 2010-11-26
Care to elaborate?

Are we talking about the 2.6.35-22 to 2.6.35-23 upgrade?

I am currently unable start up the X server, after upgrading to 2.6.35-23 kernel.
I use proprietary NVIDIA CUDA enabled drivers for scientific computation purposes, and i can not let go of them.

What is the recommended course of action?

---

### Post by dino99 on 2010-11-26
> **tsunetomo said:**
> Care to elaborate?

Are we talking about the 2.6.35-22 to 2.6.35-23 upgrade?

I am currently unable start up the X server, after upgrading to 2.6.35-23 kernel.
I use proprietary NVIDIA CUDA enabled drivers for scientific computation purposes, and i can not let go of them.

What is the recommended course of action?

it seems to me that your issue is very different to this thread, open yours and dont spam this one.

maybe you can look at: [http://www.nvidia.com/object/cuda_gpus.html](http://www.nvidia.com/object/cuda_gpus.html)

---

### Post by manubbo on 2010-11-26
Thanks dino99, it worked.

Now the only thing that I'd hope to resolve is to getting Xinerama working with using applications such as Skype and Virtualbox. In that case, hovering the mouse to their windows causes a X server reboot. With Xinerama disabled everything works fine. 

Some suggestions even on this?

Thanks.

---

### Post by at165db on 2010-11-29
I'm having this same issue (dual monitors via TwinView, 64-bit Kubuntu, upgraded to 2.6.35-23-generic and nvidia stops working).

I tried the purge/install, and didn't make any progress other than if I boot up without the xorg.conf Kubuntu does boot to X/KDE using the free nvidia drivers.

I'm not sure how I install the ppa, so I'm guessing that is the missing step.  I tried googleing and came up with this:

~$ sudo add-apt-repository ppa:[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
[sudo] password for russlewi: 
Error reading [https://launchpad.net/api/1.0/~https/+archive/ppa:](https://launchpad.net/api/1.0/~https/+archive/ppa:) HTTP Error 404: Not Found

How do I install that ppa you mentioned?

Thanks!

---

### Post by at165db on 2010-11-30
Ah, I assumed that the URL was what I needed to add, but the page was just timing out yesterday.
you just need to run:
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

However, I now get the following problem when doing a sudo apt-get update:
Failed to download [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
404  Not Found

Any ideas?

---

### Post by at165db on 2010-11-30
interesting, it seems there was an update to the same kernel 2.6.35-23-generic, and that has fixed nvidia for me.  I do not have the PPA above installed (I also purged it).

---

### Post by at165db on 2011-01-05
So I come back to work after the holidays, boot up my PC, and do an update to 2.6.35-24.
And once again nvidia stops working with my GeForce 9500 GT.

Why is it a fresh install keeps breaking my drivers?  This is why I left Fedora Core 4 years ago, ubuntu 8.10-10.04 never broke drivers on me.

Does anyone know of a fix for the 2.6.35-24 + nvidia problems?  I'm using the nvidia drivers installed by ubuntu's own packages.

---

