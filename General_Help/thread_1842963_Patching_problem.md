---
title: "Patching problem"
date: 2011-09-12
forum: General Help
---

### Post by astro123 on 2011-09-12
Hi I am new to Ubuntu and know very little of Linux distros as till date I have used windows only.
I am willing to learn Linux too.

So I have been reading alot and couldn't find solution.It may be minor problem for regular Linux users but it's new to me.

I am trying to apply compat wireless patch to my rtl8187 device but dont know if it's done successfully?
Also how does Patching works in Linux?
Is it same as upgrading s/w in Windows or may be modifying?

I did following steps as mentioned on this forum by someone
```
sudo apt-get install linux-headers-$(uname -r) wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/2010/12/compat-wireless-2010-12-20.tar.bz2 tar -jxf compat-wireless-2010-12-20.tar.bz2 cd compat-wireless-2010-12-20 wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch sudo apt-get install patch patch ./net/wireless/chan.c channel-negative-one-maxim.patch  make sudo make install sudo make unload sudo reboot      
    
```

Here's Process


It's too big so will attach a Process.txt file

Here's error

```
                   lo        no wireless extensions.  eth0      no wireless extensions.  wlan0     IEEE 802.11bg  ESSID:off/any           Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm           Retry  long limit:7   RTS thr:off   Fragment thr:off           Encryption key:off           Power Management:off  root@bt:~# airmon-ng stop wlan0   Interface       Chipset         Driver  wlan0           RTL8187         rtl8187 - [phy0]                                 (monitor mode disabled)  root@bt:~# iwconfig lo        no wireless extensions.  eth0      no wireless extensions.  wlan0     IEEE 802.11bg  ESSID:off/any           Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm           Retry  long limit:7   RTS thr:off   Fragment thr:off           Encryption key:off           Power Management:off  root@bt:~# airmon-ng start wlan0 1   Found 2 processes that could cause trouble. If airodump-ng, aireplay-ng or airtun-ng stops working after a short period of time, you may want to kill (some of) them!  PID     Name 4781    dhclient 4803    dhclient   Interface       Chipset         Driver  wlan0           RTL8187         rtl8187 - [phy0]                                 (monitor mode enabled on mon0)  root@bt:~# aireplay-ng -9 -e aaaa -a 80:A1:D7:18:54:B0 wlan0 12:28:22  Waiting for beacon frame (BSSID: 80:A1:D7:18:54:B0) on channel -1 12:28:22  wlan0 is on channel -1, but the AP uses channel 1      
    
```

---

