---
title: "Can't connect to internet via wireless"
date: 2011-01-23
forum: General Help
---

### Post by rctaets on 2011-01-23
I have an HP Mini 311 laptop with Windows XP. I would like to run Ubuntu on it but I can't get the wireless network to work. The laptop uses a Broadcom 802.11b/g WLAN that works with Windows XP.  I can bring the laptop up on Ubuntu 10.10 netbook using a USB flash drive. Before I try to install it on the hard drive I am using the "Try UBUNTU first". Everything seems to work except the wireless. I can only connect to the internet through an ethernet cable.  How do I go about getting the wireless to work?

---

### Post by CrusaderAD on 2011-01-23
Is the wireless option greyed out when you right lick the network icon in the tray?

---

### Post by rctaets on 2011-01-23
Yes it is greyed out.

---

### Post by CrusaderAD on 2011-01-23
Well you're using the live cd version. I had this happen before. I did an install, then when you boot the first time, it won't work. Do a system update and then it should install the right drivers.

---

### Post by rctaets on 2011-01-23
I tried that but it says I don't have enough space for the updates. Do I have to install Ubuntu on the hard drive first?

---

### Post by Bucky Ball on 2011-01-23
That card will work 'out of the box' with a full install. You need to get online with a cable to download firmware etc. It is a two click process that takes half a minute. 

Installing the correct wireless drivers while trying Ubuntu from the LiveCD (or in your case USB) is not really possible as there is nowhere to install them to if you follow me. If the OS is resident on the hard drive there will spaces and places to write them to.

---

### Post by rctaets on 2011-01-23
I will try to install Ubuntu on the hard drive tomorrow. I will let you know how it goes.  Thanks for your help.

---

### Post by rctaets on 2011-01-24
I installed Ubuntu 10.10 on my hard drive. Wireless still does not work. Right click on network icon shows Enable Wireless is checked. If I left click the icon the Wireless Networks is greyed out and underneath it says "device not ready(firmware missing).  Any ideas on how to get the firmware?

---

### Post by Bucky Ball on 2011-01-24
Plug in an ethernet cable if you haven't already. Get online then:

System>Admin>Update Manager, and get updates.

Then:

System>Admin>Additional Drivers

See anything? You might not even need to do the last step depending on your wireless card. Do you know what it is? Open a terminal (don't be afraid!) by doing Applications>Accessories>Terminal, and paste this in then press enter. Post the result back here:

```
sudo lshw -C network
```

;)

---

### Post by rctaets on 2011-01-24
Well I must have done something right because the wireless is now working.  Thanks for all your help.

---

### Post by Bucky Ball on 2011-01-24
Great news. Welcome and enjoy. ;)

---

