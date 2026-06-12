---
title: "Noob needs help"
date: 2009-09-12
forum: General Help
---

### Post by VincentCruise on 2009-09-12
Hello.

can u help me install a linux driver? So far I have extracted a file. Now I have to go to the directory it was extracted to and change make file. I don't know where the file was extracted to so I can't change the file. I did not choose a location so it's somewhere in the default location wherever that is. I have directions but I'm a noob. If you could help me with a few lines of directions you would be of great help.

thanks.

---

### Post by ithinkitschad on 2009-09-12
> **VincentCruise said:**
> Hello.

can u help me install a linux driver? So far I have extracted a file. Now I have to go to the directory it was extracted to and change make file. I don't know where the file was extracted to so I can't change the file. I did not choose a location so it's somewhere in the default location wherever that is. I have directions but I'm a noob. If you could help me with a few lines of directions you would be of great help.

thanks.

have you checked /home/YOURUSERNAME/Desktop?

---

### Post by QIII on 2009-09-12
A better title is more likely to get people with some familiarity to take a look at your post.

Some details needed:

1.  Make, model, full specifications of your machine.

2.  The driver you are trying to install and for which hardware device.

3.  What you have done so far, exactly, by the numbers.

---

### Post by VincentCruise on 2009-09-12
Yes I have I have checked the desktop. extracted the file with the terminal and command:

tar zxvf file location and file

---

### Post by ithinkitschad on 2009-09-12
> **VincentCruise said:**
> Yes I have I have checked the desktop. extracted the file with the terminal and command:

tar zxvf file location and file

So it extracted to that same file location. Now cd into the directory. You need to give us alot more info though to help you.

---

### Post by ckonestroh on 2009-09-12
> **ithinkitschad said:**
> have you checked /home/YOURUSERNAME/Desktop?


You did follow this step....?????

---

### Post by VincentCruise on 2009-09-12
I am installing a driver for a wifi antenna. The driver works for any version of Linux. OK heres the directions that I am following. I don't know what you mean by same place. I checked where the file to be extracted was located but it's not thier. Here' the directions that I am following so to give you better understanding and so you can help:

Step 1: Package Extraction:

tar zxfg ZD1211LnxDrv_xxxx.tar.gz
#where xxxx is the version number, such as 2_0_0_0

The first thing one should do is to uncompress this package by tar. After untaring this package, you can see the source files. One should change directory into this directory for proceeding the next step.

Step 2 Build and install the driver

The package contains drivers for ZD1211 and ZD1211B. If you doesn't have specified request, both of them will be installed. Under the extracted directory, there is a Makefile in it. Because our driver can support for kernel 2.4 and kernel 2.6 there are two sets of rule in the Makefile. One has to modify the Makefile according to the path of "kernel source tree" and the version of  the kernel in your system. In the Makefile, you may see the following statements:

#if the kernel is 2.6.x turn on this
#KERN_26=Y
#kERNEL_SOURCE=/usr/src/linux-2.6.7
#if the kernel is 2.4.x turn on this
KERN_24=Y
KERNEL_SOURCE=/usr/src/linux-2.4.20-8

If you want to build the kernel under the kernel of 2.4.x, one has to set the variable KERN_24=y and comment the KERN_26=y like that as the example above and modify the variable KERNEL_SOURCE to the path which you install the kernel source. After doing these things, one just need to type the "make" and the driver module will be generated and installed.

---

### Post by QIII on 2009-09-12
What is the make and model of the wifi device?

EDIT:  Looked it up.

Can you give us EXACTLY the command you used to extract the tar?  Not "tar zxvf file location and file", but the actual text you used.

There seem to have been issues with this device even if you can get it installed.   What version of Ubuntu are you using and what kernel version?

---

### Post by murderslastcrow on 2009-09-12
It's very rare that you would have to compile your own drivers for this, but it would be much easier to help if we did know the make and model of the device. :) That way we can see what the community resources say about that device.

---

### Post by VincentCruise on 2009-09-12
It is a yagi wifi antenna bought from a guy who makes them himself. It was bought off of Ebay. I am a noob and if you could tell me how to do the instructions posted above you would be of great help. I am using ubuntu 8.10 Intrepid I don't know how to find out what kernel it is. thank you.

The actual command and text I typed are:

tar zxvf Desktop/Linux/ZD1211LnxDrv_2_16_0_0.tar.gz

---

### Post by QIII on 2009-09-12
> **murderslastcrow said:**
> It's very rare that you would have to compile your own drivers for this, but it would be much easier to help if we did know the make and model of the device. :) That way we can see what the community resources say about that device.

The device he is using seems to be supported in kernel version 2.6.28-9.

It should be supported.

---

### Post by ithinkitschad on 2009-09-12
> **VincentCruise said:**
> It is a yagi wifi antenna bought from a guy who makes them himself. It was bought off of Ebay. I am a noob and if you could tell me how to do the instructions posted above you would be of great help. I am using ubuntu 8.10 Intrepid I don't know how to find out what kernel it is. thank you.

The actual command and text I typed are:

tar zxvf Desktop/Linux/ZD1211LnxDrv_2_16_0_0.tar.gz

The extracted files would be at /home/yourusername/Desktop/Linux
There should be the file ZD1211LnxDrv_2_16_0_0.tar.gz and probably a folder named something like ZD1211LnxDrv_2_16_0_0. You would then type cd ZD1211LnxDrv_2_16_0_0 or whatever the folder name is and continue with the instructions.

---

