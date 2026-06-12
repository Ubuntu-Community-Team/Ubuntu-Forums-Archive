---
title: "Compile kernel module"
date: 2005-03-06
forum: General Help
---

### Post by Janzert on 2005-03-06
I'm trying to use the warty livecd with an intel d925xcv mb based system. But it doesn't seem to support the network card (neither does any other live cd). Intel has a Linux driver available at [http://support.intel.com/design/motherbd/cv/cv_drive.htm](http://support.intel.com/design/motherbd/cv/cv_drive.htm), but of course it needs to be compiled. The directions for compiling a kernel module start with using apt-get to grab the source and of course I have no network connection.

Is there a way that I could manually grab everything needed and put it on a usb drive or is there somplace (or someone) that I could get the module already compiled for the live cd?

Janzert

*The exact iso I'm using is warty-release-live-i386.iso

---

### Post by GilGalad on 2005-03-07
What kernel version are you using?

By any chance the network card is a Marvel Yukon one? I am going through hell to be able to use it.  My findings:

- Kernel 2.6.8 (from Warty) is able to recognize the card and works so if you are using that version it should work. Just type "sudo modprobe sk98lin" and see the output of "dmesg"
- Kernel 2.6.10 from Hoary does recognize the card but the driver loads with errors and any attempt of network connection makes the computer hard lock.
- The drivers you mention from Intel do not compile in 2.6.10 kernel. If you do some modifications to the driver in order to make it compile, same error as above happens.
- Versions 8.13 & 8.14 from syskonnect web site do compile without errors in kernel 2.6.10. Need the check if they work yet.

As for things you need to compile the driver... compiler (gcc), linux-image, linux-headers. You can grab files from: [http://archive.ubuntu.com/ubuntu/pool/main/](http://archive.ubuntu.com/ubuntu/pool/main/)

---

### Post by Janzert on 2005-03-07
Hmm, well I thought I was using the warty live cd. :?

Here's the output from a couple commands:
warty@ubuntu:~ $ uname -a
Linux ubuntu 2.6.7 #2 Mon Oct 18 00:31:18 CEST 2004 i686 GNU/Linux

Maybe I don't have the final warty release?

warty@ubuntu:~ $ sudo modprobe sk98lin
FATAL: Error inserting sk98lin (/lib/modules/2.6.7/kernel/drivers/net/sk98lin/sk98lin.ko): No such device

Also dmesg has this:

sk98lin: No adapter found.

The relevant line from lspci shows:

0000:04:00.0 Ethernet controller: Marvell: Unknown device 4361 (rev 17)

and lspci -n:

0000:04:00.0 Class 0200: 11ab:4361 (rev 17)

So maybe I've downloaded the wrong ISO?

Janzert

---

### Post by az on 2005-03-07
"I'm trying to use the warty livecd with an intel d925xcv mb based system. But it doesn't seem to support the network card (neither does any other live cd). Intel has a Linux driver available at [http://support.intel.com/design/mot...cv/cv_drive.htm](http://support.intel.com/design/mot...cv/cv_drive.htm), but of course it needs to be compiled"

You are using the live cd.  You do not compitle and add things on to it.  You canoot install packages onto the live cd.  It is read-only.

If you were to install Warty onto your hard drive, then we are talking.  Everything you need to build and install kernel modules is included on the install cd, namely:

build-essential and linux-headers-2.6.8.1-3-386.

---

### Post by Janzert on 2005-03-07
Right, I was hoping to compile off a usb drive, or get it pre-compiled, and then symlink the final module into place. Then a simple modprobe to get the network card working.

The final purpose was to use a live cd, modify the scripts from [http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/) to work under Linux ,and do a full hard drive backup. I did this a couple years ago with another system, but unfortunately it doesn't look like I can get any of the live cd's available to work with this network card.

Janzert

---

