---
title: "DLink DW-140 (Rev. B2) Wireless Pen driver  problem"
date: 2010-03-22
forum: General Help
---

### Post by Peter Alien on 2010-03-22
i tried lots of ways to install DLink DW-140 (Rev. B2) Wireless Pen driver in Ubuntu 9.10 but with no luck :( ... it simply doesn't work.
I even tried to compile one or two drivers and install them (rt2870, rt3070), but no luck.

Can someone give me another way to do it or i have to give up Ubuntu Karmic Koala :( i don't have internet, so i can't update or download anything.

I have Kernel 2.6.31.14. I noticed that this version brings rt2870, but it doesn´t work too.
I only have an wireless internet connection, no cable one.

Thank you very much.

---

### Post by Peter Alien on 2010-03-29
anyone?!

---

### Post by gordintoronto on 2010-03-29
According to this:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#USB)

The 140 works "out of the box".

Do you know how to connect with a working wireless adapter?

---

### Post by Peter Alien on 2010-03-30
My pen is DLink DW-140 (Rev. B2), in the table doesn´t say that "works out of the box".

I tried with kernel 2.6.31.14 and 2.6.31.16, with no luck :(

i compiled the latest driver that i found, the complitation went well but the instalation of it gave me errors!!!

I don't know if anyone has this pen and if had luck to put it to work?!

---

### Post by Peter Alien on 2010-04-01
I found out an older driver in a Forum for my DLink DW-140/Rev.B2, and finally my wireless pen has the led flashing :D and i put my credentials in the network-manager, and i saw that the connection was established... but there's still one problem... when i open Firefox it doesn´t let me see any webpages :( 
Can anyone tell me why?

I was running Ubuntu 9.10 (Kernel 2.6.31.14)  from the CD.

Here is the method i used:
--------------------------

Driver: 2009_1110_RT3070_Linux_STA_v2.1.2.0


Open terminal

Code:
sudo gedit /etc/modprobe.d/blacklist.conf
And add...

Code:
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
blacklist ndiswrapper
Save and exit.

Compiling a New Kernel Module (Driver)

You'll need a compiler and Linux headers installed

Code:
sudo apt-get install build-essential linux-headers-generic
Config and Install Driver

note: The "build-essential linux-headers-generic" is in the CD, no need to download it.


Extract these files (rt3070USB driver) then move to the dir. in terminal:

Code:
cd Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0
Next, we have to make a few adjustments to the config...

Start with config.mk in /os/linux/:

Code:
gedit /os/linux/config.mk
Then find:

Code:
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

and change to:

Code:
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
Save and close


Then open usb_main_dev.c in /os/linux/:

Code:
gedit /os/linux/usb_main_dev.c
Then add the following before the #endif (in the "USB Devices" area)

Code:
{USB_DEVICE(0x1737,0x0078)}, /* Linksys WUSB100v2 */

Important note: In this file i had to edit the value to my device D-Link DW 140 -> from 3072 to 3070.

Compile



Now run:

Code:
make
make install
Now you have to delete the rt2870sta that came with the install and load the new module

Code:
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/staging/rt2870
modprobe rt3070sta
insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt3070sta.ko
Now if you run iwconfig you should see an ra0 interface but if you run ifconfig its not there. So here is the fix:

Code:
mv /etc/Wireless/RT3070STA /etc/Wireless/RT2870STA

Now restart network-manager:

Code:
/etc/init.d/networking restart
restart network-manager
Now you should see wireless connections available in network manager (This may require a restart)


After many drivers tested and compiled, finally i got my pen led flashing and could connect to my wireless router, but still can´t open any webpages in Firefox :( Why?!

Is because i was running Ubuntu from CD?!


Can someone help me?

Many thanks in advanced.

Pedro

---

