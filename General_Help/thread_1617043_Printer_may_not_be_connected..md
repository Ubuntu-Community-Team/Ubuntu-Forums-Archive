---
title: "Printer may not be connected."
date: 2010-11-08
forum: General Help
---

### Post by d5xtgr on 2010-11-08
Hi all
I have a LaserJet 6MP that I have successfully used since switching to Ubuntu in July, and since upgrading to 10.10 a month ago.  Unfortunately, I got a message while trying to print yesterday to the effect of "This printer may not be connected".  After spending several hours over the past two days trying to fix the problem, things only seem to have gotten worse; I uninstalled and attempted to reinstall the printer as per one set of instructions I read, but it doesn't seem to be recognized at all now.

The printer is connected via a usb-to-parallel converter cable.
lsusb outputs the following:
[code]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[\code]
Can someone walk me through how to install this thing and get it working?  I'd rather not buy a new printer; this thing's quite a workhorse and I still have spare cartridges for it.

I've had no success using parallel:/dev/usb/lp0 for the URI, as is suggested in a number of places.

Many thanks
d5xtgr

---

