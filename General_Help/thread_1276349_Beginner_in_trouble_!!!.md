---
title: "Beginner in trouble !!!"
date: 2009-09-26
forum: General Help
---

### Post by samrat96 on 2009-09-26
I have a USB modem which supports only windows. Other type of connection is not possible for me. So every time I need something for my Ubuntu I open windows and complete the download.

 I need to download the mp3 codec and other codecs for ubuntu but I don't where to get it.
Remember that I cannot directly update from Ubuntu as there is no internet connection while running ubuntu. So what I need to know is 

1) Where do I find support for mp3 format?
2) How do I update my Ubuntu using these?
3) Is it possible to download all the software for Ubuntu like I plan to do?

I would prefer that answer be given in procedural format with pointers to websites and also would appreciate if technical information related to my post (eg: Ubuntu and usb internet) would be supplied in concise from with pointers.

---

### Post by akakingess on 2009-09-27
> **samrat96 said:**
> I have a USB modem which supports only windows. Other type of connection is not possible for me. So every time I need something for my Ubuntu I open windows and complete the download.

 I need to download the mp3 codec and other codecs for ubuntu but I don't where to get it.
Remember that I cannot directly update from Ubuntu as there is no internet connection while running ubuntu. So what I need to know is 

1) Where do I find support for mp3 format?
2) How do I update my Ubuntu using these?
3) Is it possible to download all the software for Ubuntu like I plan to do?

I would prefer that answer be given in procedural format with pointers to websites and also would appreciate if technical information related to my post (eg: Ubuntu and usb internet) would be supplied in concise from with pointers.

I'm not quite sure I understand your questions, mp3 is supported, I believe VLC will play them, and what do you need to update in Ubuntu for mp3s? Yes, it is possible to download the RPMs or tar's, whichever way you are going to go for software to be installed and then just unpack them within Ubuntu and install, Does this answer the questions, or am I misunderstanding?

---

### Post by fragos on 2009-09-27
The package you want is ubuntu-restricted-extras which I believe is in the multiverse repository. You will be able to locate the URL at [http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras](http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras).

---

### Post by 3rdalbum on 2009-09-27
> **fragos said:**
> The package you want is ubuntu-restricted-extras which I believe is in the multiverse repository. You will be able to locate the URL at [http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras](http://packages.ubuntu.com/jaunty/ubuntu-restricted-extras).

Ubuntu Restricted Extras is a metapackage; it merely tells the package manager to "download these other packages" which is not going to be of any use if you don't have an internet connection on Ubuntu.

Go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and do a search for "gstreamer0.10-fluendo-mp3" for Jaunty; this package will add MP3 support. You might need to download addition packages from that website in order to install it; if this is the case, Ubuntu will tell you which packages and say "Dependency not satisfiable".

The best solution is to buy an ADSL modem/router that plugs into your Ethernet port; these work perfectly with Ubuntu.

---

### Post by zman58 on 2009-09-27
You need to get hardware that can provide network connection to your Ubuntu system. You are wasting your time without that. Get a WAN router attached to your ISP, so you can then attach any PC system to that using Ethernet TCP/IP. It will be very much worth the cost and will save you incredible time and energy than the course you are trying to take.

Are you on Cable or Dialup?

Most cable modems, besides USB also have an Ethernet RJ45 plug connection available with them. Perhaps all you need is a Ethernet cable.

---

### Post by Shujah on 2009-09-27
Easy option is to download relevant .deb files, try get-deb & gnome-files websites. These .deb files can be executed on Ubuntu. But you will run into dependency problems sooner or later. Better option is to download Ubuntu DVD which comes with all the packages add it to Ubuntu repos and add packages from there. Best option is to try to configure your usb modem on Ubuntu, Google for wvdial and search the threads on this forum.

---

