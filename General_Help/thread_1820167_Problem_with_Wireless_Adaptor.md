---
title: "Problem with Wireless Adaptor"
date: 2011-08-07
forum: General Help
---

### Post by n0nex on 2011-08-07
Hello Dear

I am using Ubuntu 11.04 with Live CD. I need to install TP-LINK WN7200ND (RT2870) driver.

Some details>

- lsusb

```

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 045e:074f Microsoft Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:c117 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

- lsmod | grep rt2

```


rt2870sta             410104  0 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  4 rt2800lib,ath9k,rt2x00usb,rt2x00lib
cfg80211              156212  4 ath9k,rt2x00lib,mac80211,ath

```

- dmesg | grep rt2

```

[   85.368784] Registered led device: rt2800usb-phy1::radio
[   85.368807] Registered led device: rt2800usb-phy1::assoc
[   85.368829] Registered led device: rt2800usb-phy1::quality
[   85.369066] usbcore: registered new interface driver rt2800usb
[   85.928517] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   85.944400] usbcore: registered new interface driver rt2870

```

*************************************
*************************************

Before this post i tried these methods to install drivers>

1.

# in /etc/modprobe.d/blacklist.conf > added blacklist rt2800
# in /etc/modules > added rt2870sta

***

2.

I downloaded Ralink RT2870 driver from its own website. Than>

# In Makefile i set the "MODE = STA" in Makefile and chosed the TARGET to Linux by set "TARGET = LINUX"
# In os/linux/config.mk i set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
# $make

and when i type `sudo make install` to the terminal there is an error like that|

```

make -C /home/ubuntu/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/ubuntu/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/ubuntu/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/
install: cannot stat `rt2870sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/ubuntu/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
make: *** [install] Error 2


```

So how can i install and connect with my wireless adaptor?

NOTE > I am using my Ubuntu with my Live CD. So I cannot restart my machine <CD is read only>
NOTE > I read most of subjects on the forum but couldnt solve my problem.

Thank you.

---

### Post by Topsiho on 2011-08-07
I am afraid that you'll have to do the install (of the WiFi drivers and so) again and again, every time you start up the live CD. The CD is read only, so cannot be written to, and as the harddisk is untouched, this means that any install you do is written into RAM, and gets lost when Ubuntu on the Live CD is exited.

Topsiho

---

### Post by n0nex on 2011-08-07
Thank you for you response.

I am ready to install every time when i start Ubuntu but there is one problem about installation.

I could not install driver however i tried lots of methods. I want to learn if there is any other way to install drivers.

Thank you.

---

### Post by gandaran on 2011-08-07
hi,
I think your adapter should work out of the box but maybe there is some kind of conflict with RT2870 and RT3070 driver, read some of these threads by users with the same ralink chipset problem 
[http://ubuntuforums.org/search.php?searchid=82375962](http://ubuntuforums.org/search.php?searchid=82375962)

---

### Post by n0nex on 2011-08-07
Thanks for response.

So I will buy a new adapter, is there any adapter which is compatable (plug and play) with Ubuntu (11.04)? Which adapter do you suggest? Please help about this.

Thank you.

---

### Post by gandaran on 2011-08-08
> **n0nex said:**
> Thanks for response.

So I will buy a new adapter, is there any adapter which is compatable (plug and play) with Ubuntu (11.04)? Which adapter do you suggest? Please help about this.

Thank you.
look, I'm sure you can get your adapter working easily, try a search for ralink RT2870 and RT3070  chipset on the wireless and networking forum section, there are plenty of threads and fixes for the same problem.
if you still prefer a new one then I recommend either atheros or realtek chipsets, realtek is probably the best but don't buy exactly a recent new one as it may not be supported yet (I got two of them rtl8188su and rtl8191su working very well on 11.04 but they don't work on previous Ubuntu releases) 
ralink chipsets should also work out of the box but sometimes there is a driver conflict and all you have to do is blacklist some drivers so yours can work.
and don't buy any broadcom chipsets.

---

