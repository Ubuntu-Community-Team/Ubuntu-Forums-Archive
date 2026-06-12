---
title: "noob needs help"
date: 2009-09-12
forum: General Help
---

### Post by VincentCruise on 2009-09-12
**Noob needs basic help** 			
 			 			 		   		 		 		I am a noob and I can't follow some basic directions for installing a driver. Can you help? I don't know much about terminal commands and so forth.

Step 1: Package Extraction:

tar zxfg ZD1211LnxDrv_xxxx.tar.gz
#where xxxx is the version number, such as 2_0_0_0

The first thing one should do is to uncompress this package by tar. After untaring this package, you can see the source files. One should change directory into this directory for proceeding the next step.

Step 2 Build and install the driver

The package contains drivers for ZD1211 and ZD1211B. If you doesn't have specified request, both of them will be installed. Under the extracted directory, there is a Makefile in it. Because our driver can support for kernel 2.4 and kernel 2.6 there are two sets of rule in the Makefile. One has to modify the Makefile according to the path of "kernel source tree" and the version of the kernel in your system. In the Makefile, you may see the following statements:

#if the kernel is 2.6.x turn on this
#KERN_26=Y
#kERNEL_SOURCE=/usr/src/linux-2.6.7
#if the kernel is 2.4.x turn on this
KERN_24=Y
KERNEL_SOURCE=/usr/src/linux-2.4.20-8

If you want to build the kernel under the kernel of 2.4.x, one has to set the variable KERN_24=y and comment the KERN_26=y like that as the example above and modify the variable KERNEL_SOURCE to the path which you install the kernel source. After doing these things, one just need to type the "make" and the driver module will be generated and installed.

---

### Post by snakepit # on 2009-09-12
Do what it says and untar it.

$ tar -zxvf  (Hint: Just type the first letter of the file and then hit your TAB key, it will autocomplete)

$ ls  (to see what the name of the new dir is)

$ cd (Again, first letter of dir, hit your TAB.  You might have to type a new letter then TAB again as dir name will be similiar to the .tgz)

$ ls  (This is the same as 'dir' in MSDOS)

(Look for a README, or INSTALL, or somethine along those lines, if you find one)

$ less README

(Read it. Your up/down arrows and spacebar scrolls. Press Q when you are done.)

Dont worry about your kernel, you have a 2.6
$ uname -a  (will tell you that you have a 2.6.x.y)

Most likely, the build and install will be done by (but make sure first)

$ ./configure

$ make
(Don't worry about all that stuff flying by now, unless it ends in 'error'.  That just means its compiling.)

$ make install

Edit: You'll probably have to be root to install it, so, in Ubuntu you'll do a:  $ sudo make install

---

### Post by VincentCruise on 2009-09-12
tell ya what I'll do it myself. This forum has a bunch of losers I  have been here for too long on this simple thing. And it's still not answered. Geek. What a forum for gaining new insight into linux.........?

---

### Post by pastalavista on 2009-09-12
> **VincentCruise said:**
> tell ya what I'll do it myself. This forum has a bunch of losers I  have been here for too long on this simple thing. And it's still not answered. Geek. What a forum for gaining new insight into linux.........?
It was answered but it was expected for you to know those were ($) terminal commands. noobs who call their helpers losers are morons. who's the one who needs the help?

---

### Post by cariboo on 2009-09-12
You don't need to compile a driver for your wireles device as the driver is already included with the kernel. To make sure the device is detected and the driver loaded could you open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network > network.txt
```

the above command will list your network devices and whether the driver has been loaded. THe command also outputs a text file called network.txt. Can you paste the output in your next post. 

I have a wireless device with the same chipset, it worked out of the box. I find it also works better in Ubuntu thatn it does with Windows.

---

### Post by akakingess on 2009-09-12
Also, you shouldn't have to edit the Makefile, when you run ./configure, it should take into account your system parameters and adjust the Makefile accordingly.

---

### Post by katoiam on 2009-09-12
VincentCruise you are incredibly ungreatful, you had a very quick reply, people want to help you and you tell them theyre loosers, sorry mate but your the looserand ungreatful to boot. I  have never found these forums to be anything but a great help and full of very kind people who atke there time out of there daily lives to help other people

---

