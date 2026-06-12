---
title: "Newb needs help please"
date: 2009-09-12
forum: General Help
---

### Post by VincentCruise on 2009-09-12
Hello. I am a noob and I am having trouble with some directions for installing a driver. I have been working through this. I have ubuntu Intrepid 8.10. Previously I followed this line of directions 

2.2 Build and install the driver

The package contains drivers for ZD1211 and ZD1211B. If you doesn't have specified request, both of them will be installed. Under the extracted directory, there is a Makefile in it. 
Bbbecause our driver can support for kernel 2.4 and kernel 2.6, there are two sets of rule in the Makefile. One has to modify the Makefile according to the path of "kernel source tree" and the version of the kernel in your system. In the Makefile, you may see the following statements,

#if the kernel is 2.6.x, turn on this
#KERN_26=y
#KERNEL_SOURCE=/usr/src/linux-2.6.7
#if the kernel is 2.4.x turn on this
KERN_24=y
KERNEL_SOURCE=/usr/src/linux-2.4.20-8

This is what i put in my makefile

KERN_26=y
KERNEL_SOURCE=/usr/src/linux-headers-2.6.27-7

is this correct? I am not sure I have the kernel source tree?


The current thing that I am working on is:

2.4 Build the debugging tool

There are two debuging tools in this package, "apdbg" and "menudbg". Run "make debug" to compile them both. If you don't have the ncurse library, you may get some error messages while compiling menudbg. You can ignore it and get apdbg only.

I dont know how to "Run make debug". Can you tell how to do it? I am used to a windows environment where I would just double click a file. I don't know what they mean.

---

### Post by P4man on 2009-09-12
Are you *sure* you need to all of this?
Most wifi sticks work out of the box without doing anything.

What USB stick do you have ? Can you post the output of

```
lsusb
``` ?

edit: and if its an internal card, run

```
lspci
```

If you are unlucky enough to have a stick that is not supported, I would consider trying ubuntu 9.04 which supports even more, or using the windows drivers with ndiswrapper.

---

### Post by suavecu on 2009-09-12
> **VincentCruise said:**
> Hello. I am a noob and I am having trouble with some directions for installing a driver. I have been working through this. I have ubuntu Intrepid 8.10. Previously I followed this line of directions 

2.2 Build and install the driver

The package contains drivers for ZD1211 and ZD1211B. If you doesn't have specified request, both of them will be installed. Under the extracted directory, there is a Makefile in it. 
Bbbecause our driver can support for kernel 2.4 and kernel 2.6, there are two sets of rule in the Makefile. One has to modify the Makefile according to the path of "kernel source tree" and the version of the kernel in your system. In the Makefile, you may see the following statements,

#if the kernel is 2.6.x, turn on this
#KERN_26=y
#KERNEL_SOURCE=/usr/src/linux-2.6.7
#if the kernel is 2.4.x turn on this
KERN_24=y
KERNEL_SOURCE=/usr/src/linux-2.4.20-8

This is what i put in my makefile

KERN_26=y
KERNEL_SOURCE=/usr/src/linux-headers-2.6.27-7

is this correct? I am not sure I have the kernel source tree?


The current thing that I am working on is:

2.4 Build the debugging tool

There are two debuging tools in this package, "apdbg" and "menudbg". Run "make debug" to compile them both. If you don't have the ncurse library, you may get some error messages while compiling menudbg. You can ignore it and get apdbg only.

I dont know how to "Run make debug". Can you tell how to do it? I am used to a windows environment where I would just double click a file. I don't know what they mean.

you just type 

> make --debug [target]

in the terminal

But ya, I can't imagine having to install a driver for a thumb drive.

---

### Post by P4man on 2009-09-12
> **suavecu said:**
> 
But ya, I can't imagine having to install a driver for a thumb drive.

I think its for a wifi card or stick.

---

### Post by suavecu on 2009-09-12
Ah, when you said usb stick I assumed thumb drive.

---

### Post by VincentCruise on 2009-09-12
It's a very rare wifi antenna it was built by a guy on ebay. Hey do I have the kernel source tree correct. And why I have your attention. I have never used wireless with a linux os. I want to try this out on a free wifi hotspot to see if it works. In a windows environment little pop up boxes will ask you if you want to connect. How does it work in linux.

---

### Post by NoaHall on 2009-09-12
There's a little applet in the "system tray". 

Anyway, a custom built antenna? Can I have a link :) Sounds interesting. 

Are you building the driver yourself?

---

### Post by P4man on 2009-09-12
> **VincentCruise said:**
> It's a very rare wifi antenna it was built by a guy on ebay. Hey do I have the kernel source tree correct. And why I have your attention. I have never used wireless with a linux os. I want to try this out on a free wifi hotspot to see if it works. In a windows environment little pop up boxes will ask you if you want to connect. How does it work in linux.

If you can compile your own kernel drivers, Im sure you'll figure out how to click the network icon and select a wifi network from the list LOL.

Can't help with the other question, ive only been using linux for 3 years :D

BTW, while compiling and all can be fun, if this is a wifi network card with windows drivers, you *can* use those. Much easier. install ndiswrapper, then in system > adminstration there is a new item called "windows drivers" or "ndiswrapper" not too sure, start it, point it to the windows drivers (the .inf file) and thats it.

---

### Post by VincentCruise on 2009-09-12
This is a link to the guy's website:
[http://www.innovativedevice.com/asp/InformationYagi.asp](http://www.innovativedevice.com/asp/InformationYagi.asp)

No I'm not building the driver.

Oh and also I suspect it must've been correct but do I have the path to the kernel source tree right?

Thanks

---

### Post by NoaHall on 2009-09-12
That's seriously cool! :D

Right, well, you've run "make" and so on? Click on the little signal icon in the top right hand corner and see if it's picking up your wifi.

---

### Post by VincentCruise on 2009-09-12
I ran make debug on the whole folder but It returned an error. When i went back to the folder thier was a new file. It was called apdbg and it was blue and had gears on it. It is a executable. I tried using the antenna but the applet isn't doing anything different then when it wasn't plugged in.

---

