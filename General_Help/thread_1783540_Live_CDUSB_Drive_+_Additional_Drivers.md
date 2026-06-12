---
title: "Live CD/USB Drive + Additional Drivers"
date: 2011-06-15
forum: General Help
---

### Post by nair on 2011-06-15
Is it possible to install additional drivers while currently booted into a Live-CD or USB-drive-based Ubuntu environment?

I attempted to do this using both a CD and a thumbdrive, but the "Additional Drivers" application was not able to search and find any drivers.  I know there are some there to obtain, because I can do exactly the same thing on a locally installed Ubuntu environment (installed on my harddrive) and I see them, using the particular machine I'm using.  And I know I can install other applications on a thumbdrive, because I have done it.  I just don't know how drivers work--maybe they don't fall into the same boat.

The only reason I ask is because I might use a thumbdrive environment to boot into Ubuntu, but if I do it on a machine which does not support the graphics driver, for example, or some other driver currently bundled with Ubuntu, I'm screwed.  Right?

---

### Post by Cheesehead on 2011-06-15
If you have a persistent USB-drive, then yes. You should be able to install easily. ('Persistent' meant that changes and saves persist across reboots) Some persistent USB-drives are easier to update than others, depending on the optimizations for maximizing speed and minimizing R/W cycles.

If you don't know if your USB drive is persistent, then it's probably not. You will remembre doing all the extra work to make it persistent.

But LiveCD and non-persistent LiveUSB are much harder becasue they work differently. They load a compressed system image into RAM, and work off that image. So you can either install the drivers each session, or you can modify that big compressed binary blog that gets loaded into RAM by recompiling it.

If you are interested in taking a known system state (including the drivers) and saving it to a non-persistent or persistent USB drive, search for the Debian Live project. It's a good place to begin learning.

---

### Post by 67GTA on 2011-06-15
Graphics drivers should work after setting up your xorg.conf file and logging out and back in. From a terminal run ```
sudo nvidia-xconfig
``` for Nvidia, and ```
sudo ati-config --initial
``` for ATI. Then log out and back in to use the graphics driver. Other drivers work a little different because they need to be initialized at boot. Most wireless drivers can be loaded in a live environment with the modprobe command. For example, my braodcom card used to need the wl driver from the restricted driver manager. Once installed, you would have to run ```
sudo modprobe wl
``` in a terminal to load the driver into the live kernel. To answer your question, yes but with a few caveats. What driver(s) are you wanting to use?

---

### Post by nair on 2011-06-16
Thanks for the replies.  I will have to do more research on the persistent USB drive topic.

With regards to what drivers I am dealing using: I've dealt with a known issue for about a year now since I started using a Dell E6510 laptop.  The problem with the Dell E6510 is that the open source nouveau graphics driver, which Ubuntu automatically wants to use once it detects you've got Nvidia hardware I assume, does not work with the Dell E6510.  This has been a problem for a year, since 10.04, and I have been dealing with it the same way ever since, even during a recent install of 11.04 this week.

I disable the nouveau driver by editing the boot command, and am able to boot up.  Other changes have to be made to permanently disable the nouveau driver.  At that point, I can either run Ubuntu as is at 1024 x 768 resolution (on a 16:9 aspect ratio monitor--equals usable but mildly terrible experience), or I can enable the proprietary Nvidia drivers, which always work, bump up the resolution to something proper (1600 x 900 in my case), and have full 3D graphics acceleration--and supposedly the ability to run Unity (although I cannot confirm this, I have not tried).

This all works fine and dandy by installing Ubuntu on my actual machine--referring to the installation of "Additional Drivers", i.e. the Nvidia proprietary drivers.  But what happens when I want to boot into a Live CD or boot off of a USB drive?  Well, so far I have found that the "Additional Drivers" application does not find anything.  There literally is nothing you can do in the "Additional Drivers" application if you are running off of a Live CD or USB drive (at least in my brief experience).

---

### Post by 67GTA on 2011-06-16
You should be able to use the "nomodeset" option at boot and then install "nvidia-glx-185" once booted. Run "sudo nvidia-xconfig" and log out/in to make it use the nvidia driver. The live USB persistent option mentioned above will work great if you just want to occasionally boot from USB. The persistent option will save all your settings almost like a hard drive install. You can install the nvidia driver in persistent mode, and it should be used every time you boot from USB. Boot from the live CD, plug in your target USB drive, and open the Startup Disk Creator. The "Stored in reserved extra space" slider determines how much space is used for your persistent data.

---

