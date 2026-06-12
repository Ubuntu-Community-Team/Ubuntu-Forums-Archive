---
title: "installing nvidia drivers"
date: 2012-04-27
forum: General Help
---

### Post by famebu on 2012-04-27
Hello!

I am new to linux and am trying to install nvidia drivers on kubuntu 10.04.

I need a easy explanation on how to do this.I am trying to follow these instructions:[http://us.download.nvidia.com/XFree86/Linux-x86_64/295.40/README/installdriver.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/295.40/README/installdriver.html) but don't really understand them.(like i said am total noob lol) 

Any help will be very appreciated. 
 

[]("http://us.download.nvidia.com/XFree86/Linux-x86_64/295.40/README/installdriver.html")

---

### Post by papibe on 2012-04-27
Hi famebu.

I would let the option of installing the driver from the Nvidia site as a last resort.

First I would try the driver provided by Ubuntu. Check [this]("http://www.psychocats.net/ubuntu/nvidia") tutorial.

I hope that helps, and let us know how it goes.
Regards.

---

### Post by eco2geek on 2012-04-27
Why are you trying to use Nvidia's binary installer? Does your graphic card work with Nvidia's current drivers? (295.40) Right now there is a [serious issue](http://www.nvnews.net/vbulletin/showthread.php?t=178460) with that version of the driver and some Nvidia chipsets (including mine, an onboard 6150SE).

But if your graphics card isn't one of them, let *buntu install the driver for you! Besides being much easier than a manual install, it uses DKMS, and what means for you is that it reinstalls the driver automatically every time there's a kernel upgrade -- otherwise, you'd have to re-run the Nvidia installer manually.

Look for a menu item with a circuit board icon with the caption "Additional Drivers" somewhere in your menus (I'm running Xubuntu, not Kubuntu, sorry) and run it. Let the system do the hard work for you.

---

### Post by SeijiSensei on 2012-04-28
From the main launcher 

Applications > System > Additional Drivers 

Let it do its magic.

---

### Post by famebu on 2012-04-28
Hello, Thank you all for the answers.

I have tried getting the drivers provided by kubuntu but there are no drivers to install.

I have a inch wide black bar all around my screen so I was thinking this could be because i have two different graphics, I have an hp pavilion p6774y, which has a amd graphics built in, but I have a nvidia geforce 560ti also. So I thought getting the nvidia driver from the website would fix this since there was no drivers provided by kubuntu.

That is why i was trying to get it off the website because there was no other way. I just mostly want to get rid of this black bar, so is it caused by the drivers or something else? Is there another way to get the drivers without the website or kubuntu supplying them?

---

### Post by SeijiSensei on 2012-04-28
> **famebu said:**
> I have a inch wide black bar all around my screen so I was thinking this could be because i have two different graphics, I have an hp pavilion p6774y, which has a amd graphics built in, but I have a nvidia geforce 560ti also. So I thought getting the nvidia driver from the website would fix this since there was no drivers provided by kubuntu.

This is the result of so-called "hybrid graphics" which have become all the rage on recent laptops.  Unfortunately the hardware developers didn't see fit to figure out a way to use this technology with Linux before loosing it upon the world.  

The "Bumblebee" project has worked to resolve this problem.  You can give the solution described here a try: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by famebu on 2012-04-28
> This is the result of so-called "hybrid graphics" which have become all  the rage on recent laptops.  Unfortunately the hardware developers  didn't see fit to figure out a way to use this technology with Linux  before loosing it upon the world.  

The "Bumblebee" project has worked to resolve this problem.  You can give the solution described here a try: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

That fixed it completely, was able to download the nvidia driver and it is now full screen.

Thank yall very much for the help in fixing this!

---

