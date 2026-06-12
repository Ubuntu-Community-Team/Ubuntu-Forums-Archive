---
title: "No Internet - Need Driver"
date: 2009-12-08
forum: General Help
---

### Post by rocketninja on 2009-12-08
Alright Guys and Gals, Here's the situation.

I've got a fresh install 9.1 x64, on my win7 side I have wifi setup and running (clearly. I'm using my neighbors wifi) However, with the new install from the automated windows installation process I don't have access to restricted drivers or any apt-get. What can I do or where can I go to get the broadcom 802.11g generic driver for linux or an alternative that is possible to get through windows to my hdd and back into linux, and the installation process?

---

### Post by gordintoronto on 2009-12-08
Open Accessories/Terminal and type the command 
           lspci 

This should give you a list of your PCI devices.  If the WiFi is a USB dongle, the command is lsusb

The point of this is to get the exact model number so you can search the forums for answers that are sitting there waiting for you.

Hmmm.  In most cases, Wifi "just works," without having to mess around with drivers.  Have you tried to connect from the network manager icon, which is near the time, in the upper right?  I think you right-click and select "edit connections."

---

### Post by NFblaze on 2009-12-08
> **rocketninja said:**
> Alright Guys and Gals, Here's the situation.

I've got a fresh install 9.1 x64, on my win7 side I have wifi setup and running (clearly. I'm using my neighbors wifi) However, with the new install from the automated windows installation process I don't have access to restricted drivers or any apt-get. What can I do or where can I go to get the broadcom 802.11g generic driver for linux or an alternative that is possible to get through windows to my hdd and back into linux, and the installation process?


[http://packages.ubuntu.com](http://packages.ubuntu.com)

Do a search for the broadcom deb files. 
You may need to download some of the dependencies like fakeroot dkms...etc... Basically when you boot back into ubuntu and try to run the deb installer it will let you know which dependency it needs. It may be trial an error tho, before you finally get all the dependent .debs

---

### Post by naatiq on 2009-12-08
> **rocketninja said:**
> Alright Guys and Gals, Here's the situation.

I've got a fresh install 9.1 x64, on my win7 side I have wifi setup and running (clearly. I'm using my neighbors wifi) However, with the new install from the automated windows installation process I don't have access to restricted drivers or any apt-get. What can I do or where can I go to get the broadcom 802.11g generic driver for linux or an alternative that is possible to get through windows to my hdd and back into linux, and the installation process?

If nothing works try NDISWRAPPER , with windows wifi drivers , it always works..

google how to use ndiswrapper

happy wifi-ing

---

