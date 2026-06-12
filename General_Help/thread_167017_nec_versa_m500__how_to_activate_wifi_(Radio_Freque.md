---
title: "nec versa m500 : how to activate wifi (Radio Frequency Kill Switch is On) ?"
date: 2006-04-27
forum: General Help
---

### Post by manubreizh on 2006-04-27
hi,
it might have be discussed allready (but i haven't find answers...), but i have a problem with wifi activation on nec versa m500 (with centrino inside) : the kill switch radio is on, and i can't configure it as "off", so my wifi doesn't work ; i have never tried with windows, and i don't have double boot (only breezy on this machine).
iwconfig says : 
 eth0      radio off  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power=off
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dmesg says :
[4294698.510000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4294698.510000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4294698.513000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[4294699.432000] ipw2200: Radio Frequency Kill Switch is On:
[4294699.432000] Kill switch must be turned off for wireless networking to work.

/etc/network/interface :
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0
#auto eth1
iface eth1 inet static
address ***********
netmask ***********
gateway ***********
broadcast ************
network ***********

#iface eth0 inet


when i use system settings, and try to activate, it appears green one second and red after, no matter what i try.

to finish, it seems that the keyboard special keys (Fn + F1) doesn't work (and no led to see if it does anything on the wifi card !).
i hope i've given enough informations, just ask if you want some more.
the problem is not important so much (i have speedtouch modem usb to connect) but i'd like to use wifi at work, so...
thanx in advance

---

