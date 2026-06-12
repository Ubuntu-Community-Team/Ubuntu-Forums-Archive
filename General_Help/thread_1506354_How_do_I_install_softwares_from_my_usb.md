---
title: "How do I install softwares from my usb?"
date: 2010-06-10
forum: General Help
---

### Post by pranj on 2010-06-10
:confused::confused:I am completely new to ubuntu...
 
I have not been able to set up an internet connection on my pc yet and I have Ubuntu 9.10 ...
I want to downlad some sofwares and I have the package.tar.gz files on my usb so the question is how do I INSTALL and RUN them on the pc?

---

### Post by Peter09 on 2010-06-10
Initially - just to check, have you asked about your internet problems on the forum. Its worth going that way first if it will resolve your problems.

---

### Post by 3rdalbum on 2010-06-10
> **pranj said:**
> :confused::confused:I am completely new to ubuntu...
 
I have not been able to set up an internet connection on my pc yet and I have Ubuntu 9.10 ...
I want to downlad some sofwares and I have the package.tar.gz files on my usb so the question is how do I INSTALL and RUN them on the pc?

No; you need .deb packages, and you'll also find that you need the dependencies for those packages too. This will become clearer if you look at [http://packages.ubuntu.com](http://packages.ubuntu.com) - download the packages for your version of Ubuntu, and you'll also see a part where it lists the "dependencies" for the package. If your system doesn't already have those dependencies installed (you can check through Synaptic Package Manager), then you'll need them as well.

Then double-click on the dependencies first, and then the main program, to install them.

If you can get an internet connection, even just mobile broadband, that will make things MUCH simpler. Then the computer can download and install the software and all its dependencies with one click. Ubuntu is not really meant for computers without an internet connection.

---

