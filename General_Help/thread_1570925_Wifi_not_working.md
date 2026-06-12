---
title: "Wifi not working"
date: 2010-09-08
forum: General Help
---

### Post by rsodee on 2010-09-08
I'm having problems connecting to a network over wifi on my netbook. Wired connection works fine. I'm not sure what the problem is. Can someone show me how to fix this?

---

### Post by croivzeba on 2010-09-08
You need to install the wifi drivers; check if you have proprietary drivers available by going to system -> Administration -> Hardware Drivers. 

Remember to be connected to the internet using a wired connection as it might have to download the drivers.

If there are none available, provide us with your card name and model and I'm sure someone will find you the required driver and help you compile it.

---

### Post by rsodee on 2010-09-09
How can I find out what the card model number is?

---

### Post by croivzeba on 2010-09-09
open a terminal and type

lspci -v

It should be listed under network controllers.

---

### Post by rsodee on 2010-09-09
I guess I don't have any proprietary drivers. It says "No proprietary drivers are in use on this system." My card is a  Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by croivzeba on 2010-09-09
Try installing the backports modules by opening a terminal and typing:

sudo apt-get install linux-backports-modules-wireless-lucid-generic

then reboot.

---

### Post by rsodee on 2010-09-10
I tried that and I also tried installing Wicd. I'm not sure what fixed it but the WiFi is working now.

---

### Post by bedelsten on 2010-09-10
If your network adapater has windows drivers, you could try this:
Applications - Add Software - Windows Wireless Drivers
Find the (CD or download) windows drivers (use Windows 2000/XP)
System - Admin - Wireless Network Drivers
Install New Driver
(search for the location of the .inf file)
Select the .inf file
Open
Install
(you should get a message "Hardware Present - Yes"
Close
Open the Network tool at the top of the screen to connect to the wireless network.

---

### Post by rsodee on 2010-09-10
I tried it and it seems to be working ok.

---

### Post by NDIS Wrapper on 2010-09-13
> **croivzeba said:**
> You need to install the wifi drivers; check if you have proprietary drivers available by going to system -> Administration -> Hardware Drivers. 

Remember to be connected to the internet using a wired connection as it might have to download the drivers.

If there are none available, provide us with your card name and model and I'm sure someone will find you the required driver and help you compile it.

Hello,

I have recently installed Lucid Lynx on my 64 bit Dell laptop. When I  ran the Live CD before installing (just to try Ubuntu for some time) it  asked me whenever I was in wifi network if I wanted to install the  proprietary drivers for wifi device. But the  same did not happen after I installed Ubuntu on HDD. So now I cannot  access internet from Ubuntu interface.
  
I read about the ndisgtk and tried to install it, but i could not find  it in package manager !!
What could be done ? If any pre- packages are to be downloaded can u plz  post the links here ?

Thanks

---

