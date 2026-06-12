---
title: "Problems with ndiswrapper"
date: 2006-02-19
forum: General Help
---

### Post by pianoboy3333 on 2006-02-19
Ok, I recently switched from a Dell Wireless 1450 802.11 a/b/g USB 2.0 Adapter to a SMC, I guess PCI 1x, adapter model: SMC2402W. I made the switch because the Dell Wifi was causing my internet to freeze up at some certain sites and just sometimes randomly. I googled it and some others had the same problem with the same adapter. Anyhow, I decided before I'd switch to compile and install ndiswrapper 1.9 figuring it might solve the problem since ubuntu breezy came with 1.1. While doing this I uninstalled the other drivers, ndiswrapper 1.1 the ndisgtk, ndis-utils all that good stuff. I unconfigured it in the System->Admin.->Networking too. While compiling, I had some problems and errors.

First, I unzipped, went to the folder and did 'sudo make'. Then that was all good, I did 'sudo checkinstall'. I set the package name to 'ndiswrapper-1.9' and that turned out fine, when checkinstall tried using 'dpkg -i' to install, I had some problems:

> 
Selecting previously deselected package ndiswrapper-1.9.
(Reading database ... 134354 files and directories currently installed.)
Unpacking ndiswrapper-1.9 (from .../ndiswrapper-1.9_1.9-1_i386.deb) ...
dpkg: error processing /home/alex/Desktop/Downloads/ndiswrapper-1.9/ndiswrapper-1.9_1.9-1_i386.deb (--install):
 trying to overwrite `/lib/modules/2.6.12-10-386/modules.alias', which is also in package linux-image-2.6.12-10-386
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/alex/Desktop/Downloads/ndiswrapper-1.9/ndiswrapper-1.9_1.9-1_i386.deb


So I'm in windoze right now wishing I was in ubuntu...... Any ideas?

---

### Post by Wallakoala on 2006-02-19
I don't know exactly what your problem is, you might want to check out [this]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto") because it tells you how to compile it, and it isn't as easy as what you just did. It might be a better idea just to use the version from the repositories, or download the deb package from the dapper repositories.

---

### Post by pianoboy3333 on 2006-02-19
Walla, If you can't understand it DON'T POST, and obviously if I have no internet, how could I get to the dapper repositories? I'll go check packages.ubuntu.com

---

### Post by Wallakoala on 2006-02-19
[QUOTE=pianoboy3333]Walla, If you can't understand it DON'T POST, and obviously if I have no internet, how could I get to the dapper repositories? I'll go check packages.ubuntu.com[/QUOTE]
well, I meant that if you have it on windows you can transfer it to your ubuntu via usb or cd.

---

