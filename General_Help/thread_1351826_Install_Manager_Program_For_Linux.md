---
title: "Install Manager Program For Linux?"
date: 2009-12-10
forum: General Help
---

### Post by joelandsonja on 2009-12-10
I was wondering if there was a program for Linux that worked like Install Manager for Windows? I have a lot of trouble installing the .tar files, and was hoping there was an easier alternative available. 

Thanks for the help!

---

### Post by zvacet on 2009-12-10
For most packages you can use synaptic manager witch you can find under system>admin>synaptic.But if you are about to install something that is not available in synaptic read [this.]("http://amitech.50webs.com/installing/index.php.html")

---

### Post by joelandsonja on 2009-12-11
Bah, I still can't get some applications to Install. 

Actually I have yet to install ANYTHING successfully through the terminal. Why is this so complicated? Hasn't anyone developed a program that will install the .tar.gz files automatically? I am trying to install drivers from a cd that will install my Dual Bay harddrive enclosure, and I simply cannot get this thing to work.

Edit - Thanks for the reply though!

---

### Post by Leppie on 2009-12-11
A lot of applications and drivers can be downloaded from the internet as debian packages (.deb files). Most of the times these packages are available for Ubuntu, which is a Debian based distro. Downloading .deb packages allows you to either use synaptic or gdebi (just "launch" it when download has completed), or if you prefer cli use dpkg.
And sometimes there's even binary files (these are like the windows installers) available for download.

---

### Post by joelandsonja on 2009-12-12
Is there a website that has a list of programs available for downloading .deb files? I have used .deb files in the past and love how easy it is, and I would like to download a list of my current programs just as a backup. 

Thanks!

---

### Post by MelDJ on 2009-12-12
i think you might want getdeb [http://www.getdeb.net/](http://www.getdeb.net/)
and you might be interested there is the package alien which can convert tgz's and rpm's to debs in the repo

---

### Post by fancypiper on 2009-12-12
For the easiest use, Synaptic is **the** best software manager I have ever used. Add the medibuntu sources and the partners sources in order to access proprietary software.

[Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683)

```
# Add medibuntu sources latest release
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

[How To Install Software in Linux](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)

[How to install ANYTHING in Ubuntu!](http://amitech.50webs.com/installing/index.php.html)

---

### Post by 3rdalbum on 2009-12-12
> **joelandsonja said:**
> Actually I have yet to install ANYTHING successfully through the terminal. Why is this so complicated? Hasn't anyone developed a program that will install the .tar.gz files automatically?

It's a bit more complicated because you're actually compiling the source code for the programs. It's not like a basic installer where it just copies files - it's actually turning the source code into machine language.

What problems are you having compiling software? Make sure your terminal is in the directory that contains the source code (the "nautilus-open-terminal" package can help with this) and make sure you have the "build-essential" and "linux-headers-generic" packages. The latter is necessary for building drivers.

If the ./configure script complains that you're missing something that it needs, just go to Synaptic and install the package it wants (tip: it will usually want the package that ends in "-dev"; in other words if it tells you that it needs "foobar", then you will probably need to install the "libfoobar" and "libfoobar-dev" packages.

---

### Post by Primefalcon on 2009-12-12
just go to application -> ubuntu software center

---

### Post by joelandsonja on 2009-12-12
Hmm ... all very helpful information, but some of it was a bit over my head. (I am indeed an mega newbie to Linux) I will check out the Get Deb program and report back ...

---

### Post by airtonix on 2009-12-12
obviously most of the replies here are not relevant to your current situation of getting the drivers for your drive bay installed.

it would help if you could tell us : 

1 ) about the tar.gz you are using for the drivers 
2 ) details about the drive bay, assuming the drive bay is plugged in : how does it connect? (usb, pci, etc etc)

---

### Post by joelandsonja on 2009-12-12
I have a Mediasonic Dual Bay Harddrive Enclosure (HUR1-SU2S2) with a 1.5TB Seagate Sata Harddrive installed. It connects through the USB port, but whenever I switch the enclosure on it blinks two green lights on the top and two red lights on the bottom. I'm assuming this means that it is detecting the harddrive in the enclosure, and also detecting that the other side is empty. (Although I managed to install a second harddrive and unfortunately it did the same thing) 

The .tar file I am trying to install is from the installation CD. There is a folder in the installation CD called 'Linux Configuration Manager', which contains the ,tar file. I managed to copy the file on the desktop, so I don't have to use the CD. 

The .tar file is called: "57xxLinuxSteelVineManager_V5_1_24.tar.gz"

This is where I need a lot of help. I followed the instructions from the "Install anything in Ubuntu" guide, and I simply cannot get it to work. If anyone has step by step instructions on how to install the drivers, that would be helpful!

Thanks!

---

