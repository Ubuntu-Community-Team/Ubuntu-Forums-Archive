---
title: "Help! Unable to connect to Wired/Wireless Networks"
date: 2010-08-29
forum: General Help
---

### Post by soundofbread on 2010-08-29
I've been working on getting connected to the internet.. and it is just not happening..

when I type sudo iwconfig

   lo       no wireless extentions.
 eth0       no wireless extentions.
 eth1       no wireless extentions.
wlan0       IEEE 802.11abgn   ESSID: "Sealab 2021"
            Mode:Managed Frequency:2.457 GHz Access point: 00:14:51:and so on
            Bit Rate=18 Mb/s    Tx-Power=6 dBm                                                                 Retry  long limit: 7    Rts thr:off Fragment thr:off 
            Encryption key:off
            Power Management : on
            Link Quality=70/70 Signal level=39 dBm
           Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
            Tx Excessive retries:0 Invalid misc:0 Missed beacon:0

Here, and in WICD it tells me I am connected to one of my routers (sealab 2021), but I also have it wired in.. 

I can not get an IP address when I try to connect with the wire.

AND even though it shows me I am connected to a network that has internet, I can't use the internet.. 

(Its really strange, it will load like half of the [www.google.com](www.google.com) page) (and it will preform searches on the google page, but I cannot go to any other websites at all, and it will not load any of the links from the google searches)


when I type this code:

cat /etc/resolv.conf

I get

nameserver 10.0.1.1

I really have no idea what to do to try and get either the wired connection or wireless going... preferably both

Any help is GREATLY appreciated
-soundofbread

---

### Post by meditatingfrog on 2010-08-29
> **soundofbread said:**
> I've been working on getting connected to the internet.. and it is just not happening..

when I type sudo iwconfig

   lo       no wireless extentions.
 eth0       no wireless extentions.
 eth1       no wireless extentions.
wlan0       IEEE 802.11abgn   ESSID: "Sealab 2021"
            Mode:Managed Frequency:2.457 GHz Access point: 00:14:51:and so on
            Bit Rate=18 Mb/s    Tx-Power=6 dBm                                                                 Retry  long limit: 7    Rts thr:off Fragment thr:off 
            Encryption key:off
            Power Management : on
            Link Quality=70/70 Signal level=39 dBm
           Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
            Tx Excessive retries:0 Invalid misc:0 Missed beacon:0

Here, and in WICD it tells me I am connected to one of my routers (sealab 2021), but I also have it wired in.. 

I can not get an IP address when I try to connect with the wire.

AND even though it shows me I am connected to a network that has internet, I can't use the internet.. 

(Its really strange, it will load like half of the [www.google.com](www.google.com) page) (and it will preform searches on the google page, but I cannot go to any other websites at all, and it will not load any of the links from the google searches)


when I type this code:

cat /etc/resolv.conf

I get

nameserver 10.0.1.1

I really have no idea what to do to try and get either the wired connection or wireless going... preferably both

Any help is GREATLY appreciated
-soundofbread

The only thing I can think of is try using a different kernel, and see if that changes anything.  You can select a different kernel in the grub menu, i think.  if that doesn't work, run lspci to get info for the ethernet adapter on your system, and search the forum for that particular device. 

i would try that, see if you can get your wired connection working.  once you get wired working, then move to wireless.  the reason i say this is because my wired connection always worked, even though wireless was a trickier situation (had to use ndiswrapper until a linux driver was written for my atheros chip).

---

