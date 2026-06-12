---
title: "DLINK DWL-G122 Wireless Network Issues"
date: 2010-02-12
forum: General Help
---

### Post by ade234uk on 2010-02-12
Adaptor is detected and I can connect to my wireless network. The adaptor works fine for a couple of mins, and then it stops working. The wireless adaptor is still connected to the network and I am not losing connection.

Any ideas, thoughts would be appreciated.

---

### Post by ade234uk on 2010-02-12
Anyone experienced the same issues?

---

### Post by weirdbeardmt on 2010-02-21
I have a DWL_g122 USB stick... and it's not even recognised on lsusb. Of all the stuff written about this... it seems quite flaky.

---

### Post by Mortesins93 on 2010-07-08
I have the same problem but it only works for 5 seconds. I don't know what to do either

---

### Post by chang47 on 2010-09-17
I experienced the same.  It worked for 10 to 20min, then lose the network.  The device is recognized as DWL-G122 by lsusb, but the network just didn't stay up very long. Still searching for solution...

---

### Post by chang47 on 2010-09-17
I got my DWL-G122 Ver B1 working reliably now on 10.04, I had to use ndiswrapper for it to work.  The basics are in this community document [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Basically you install ndiswrapper and use it to install the Windows driver for DWL-G122. I used the Windows driver that came with my DLink CD. Luckily I still have it.

Then blacklist the original drivers in the file /etc/modprobe.d/blacklist.conf and reboot.

In my case they were:

blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2500usb


use 
lsmod | grep rt
to see what your system is using as the wifi driver.

lsusb show my DWL-G122 was correctly recognized, but did not work reliably so I tried the ndiswrapper route and it seemed working now.

---

### Post by Magic_Spehar on 2010-10-16
You can also try the following solution (already posted here by Tarzan). It worked for me with my G122 adapter when I had Ubuntu 10.04.

Be careful though not to upgrade your system to 10.10 because the default kernel doesn't work with the G122 adapter (you need to change your grub then so the kernel used is the former version and then it also works).

1. Download Linux driver for RT3070USB from [http://www.ralinktech.com/](http://www.ralinktech.com/) (Software -> Linux)

2. Unpack the tar & bz2 source package, be careful to don't leave spaces in the extracted directory name, open a terminal and go to contents' directory

3.
Code:
cp RT2870STACard.dat RT3070STACard.dat
cp RT2870STA.dat RT3070STA.dat
cp common/rt2870.bin common/rt3070.bin
sudo make
sudo make install
4. Add to /etc/modprobe.d/blacklist.conf
Code:
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870sta
5. Make a new dir and copy a RT2870 file in it:
Code:
sudo mkdir /etc/Wireless/RT2870STA
sudo cp /etc/Wireless/RT3070STA/RT3070STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat
6. Add RT3070STA in /etc/modules

7. Restart the system

---

