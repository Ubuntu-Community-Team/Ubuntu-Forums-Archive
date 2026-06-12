---
title: "fixed channel mon0 : -1"
date: 2011-08-19
forum: General Help
---

### Post by sonna22 on 2011-08-19
i'm using ubuntu 11.04 when i focus the attack on a spesific channel it gives fixed channel mon0 : -1 error off course you can't go on with subseqwent steps and yes i already tried alot to fix it and followed many tutorial including aircrack-ng site but no luck and by the way i have ALFA wireless adapter RTL8187 and i'm not a beginner i'm familiar with linux.
any help will be appretiated...

---

### Post by sonna22 on 2011-08-20
please help

---

### Post by spiky001 on 2011-08-20
Hi I found these they might help
[http://ubuntuforums.org/showpost.php?p=10586643&postcount=5](http://ubuntuforums.org/showpost.php?p=10586643&postcount=5)
[http://ubuntuforums.org/showthread.php?t=1598930](http://ubuntuforums.org/showthread.php?t=1598930)
The last 1 has a few pages, Sorry if you have seen these already

[http://www.janoweb.net/tutorials/install-drivers-rtl8187-r8187-rt2800usb-on-ubuntu-lucid-maverick.html](http://www.janoweb.net/tutorials/install-drivers-rtl8187-r8187-rt2800usb-on-ubuntu-lucid-maverick.html)
Have a look  about half way down

---

### Post by sonna22 on 2011-08-20
thank you so much spiky001 for your reply

---

### Post by sonna22 on 2011-08-20
Finally I've got it sorted out the problem solved for good
i have followed those links BUT i have modified 3 steps of the guide and thats it  you'r good to go.
              
*if you notice i have changed the date to the latest version which is the KEY to solve the problem

[PHP]wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2011-08-06.tar.bz2
tar -jxf compat-wireless-2011-08-06.tar.bz2
cd compat-wireless-2011-08-06
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot[/PHP]if any extraction error just download latest compat-wireless-2.6 Manually and put it in Home folder
[http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)

And that's the bottom line because i said so.

---

### Post by basry on 2011-08-22
> **sonna22 said:**
> Finally I've got it sorted out the problem solved for good
i have followed those links BUT i have modified 3 steps of the guide and thats it  you'r good to go.
              
*if you notice i have changed the date to the latest version which is the KEY to solve the problem

[PHP]wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2011-08-06.tar.bz2
tar -jxf compat-wireless-2011-08-06.tar.bz2
cd compat-wireless-2011-08-06
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot[/PHP]if any extraction error just download latest compat-wireless-2.6 Manually and put it in Home folder
[http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)

And that's the bottom line because i said so.

i did exactly as you said but the problem still not solved , it just turned to [fixed channel mon0 : "random numbers" ]
so can anybody help me with that.

---

### Post by Basher101 on 2011-08-22
Try these:
```
airmon-ng stop wlan0
```
```
ifconfig wlan0 down
```
```
iwconfig wlan0 mode managed
```
```
ifconfig wlan0 up
```
```
iwconfig wlan0 channel (your channel here)
```
```
ifconfig wlan0 down
```
```
iwconfig wlan0 mode monitor
```
```
ifconfig wlan0 up
```

you must repeat this if you want to change the channel for sniffing another network

---

### Post by basry on 2011-08-23
thanks it worked .

---

### Post by dashadowfire on 2011-12-05
Hi, im kinda new in linux. Im trying this solution, and when i get to the: gedit scripts/update-initramfs   part, i get this message:



(gedit:3776): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported


** (gedit:3776): WARNING **: Could not connect to session bus



what should i do about this?

---

### Post by aesthetic.crazy on 2012-01-15
> **sonna22 said:**
> Finally I've got it sorted out the problem solved for good
i have followed those links BUT i have modified 3 steps of the guide and thats it  you'r good to go.
              
*if you notice i have changed the date to the latest version which is the KEY to solve the problem

[PHP]wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2011-08-06.tar.bz2
tar -jxf compat-wireless-2011-08-06.tar.bz2
cd compat-wireless-2011-08-06
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo reboot[/PHP]if any extraction error just download latest compat-wireless-2.6 Manually and put it in Home folder
[http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/)

And that's the bottom line because i said so.


I got this error, plz guide me further

ubuntu:~/compat-wireless-2012-01-14$ make
make -C /lib/modules/3.0.0-12-generic/build M=/home/d3o4/compat-wireless-2012-01-14 modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
  CC [M]  /home/d3o4/compat-wireless-2012-01-14/drivers/net/wireless/iwlwifi/iwl-trans-pcie.o
/home/d3o4/compat-wireless-2012-01-14/drivers/net/wireless/iwlwifi/iwl-trans-pcie.c: In function ‘iwl_trans_rx_alloc’:
/home/d3o4/compat-wireless-2012-01-14/drivers/net/wireless/iwlwifi/iwl-trans-pcie.c:91:2: error: implicit declaration of function ‘dma_zalloc_coherent’ [-Werror=implicit-function-declaration]
/home/d3o4/compat-wireless-2012-01-14/drivers/net/wireless/iwlwifi/iwl-trans-pcie.c:91:10: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/d3o4/compat-wireless-2012-01-14/drivers/net/wireless/iwlwifi/iwl-trans-pcie.c:97:15: warning: assignment makes pointer from integer without a cast [enabled by default]
cc1: some warnings being treated as errors

make[4]: *** [/home/d3o4/compat-wireless-2012-01-14/drivers/net/wireless/iwlwifi/iwl-trans-pcie.o] Error 1
make[3]: *** [/home/d3o4/compat-wireless-2012-01-14/drivers/net/wireless/iwlwifi] Error 2
make[2]: *** [/home/d3o4/compat-wireless-2012-01-14/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/d3o4/compat-wireless-2012-01-14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [modules] Error 2

---

### Post by joelstitch on 2012-03-08
> **Basher101 said:**
> Try these:
```
airmon-ng stop wlan0
```
```
ifconfig wlan0 down
```
```
iwconfig wlan0 mode managed
```
```
ifconfig wlan0 up
```
```
iwconfig wlan0 channel (your channel here)
```
```
ifconfig wlan0 down
```
```
iwconfig wlan0 mode monitor
```
```
ifconfig wlan0 up
```

you must repeat this if you want to change the channel for sniffing another network

Finally! this worked for me also!

---

