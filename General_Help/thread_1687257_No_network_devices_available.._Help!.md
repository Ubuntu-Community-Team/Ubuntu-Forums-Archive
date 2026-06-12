---
title: "No network devices available.. Help!"
date: 2011-02-13
forum: General Help
---

### Post by leon.vitanos on 2011-02-13
I am using Ubuntu 10.10 ... 
From the connection manager->wireless i edited my network and checked the checkbox "Allow to all users"

After restarting i am seeing this notification that no network devices are available.. ( See screenshot )

What can i do?

---

### Post by An Sanct on 2011-02-13
Right click on the connection applet, disable wifi and then re-enable it after a few seconds, this should help. If the problem persists, search for a network management other then the OS default, I've heard it is not the best option out there.

---

### Post by leon.vitanos on 2011-02-13
> **An Sanct said:**
> Right click on the connection applet, disable wifi and then re-enable it after a few seconds, this should help. If the problem persists, search for a network management other then the OS default, I've heard it is not the best option out there.

By right clicking i do not have any option to disable wifi... ( Screenshot 1 )

The output of lspci -nn | grep Network is
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

The output of airodump-ng start wlan0 is

Found 3 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
926    avahi-daemon
927    avahi-daemon
978    wpa_supplicant


Interface    Chipset        Driver

wlan0        Intel 3945ABG    iwl3945 - [phy0]
                (monitor mode enabled on mon1)
mon0        Intel 3945ABG    iwl3945 - [phy0]



I recently have installed some dhcp-client and dns packages.. i complete removed now, and now i see this message ( Screenshot 2 )
After removing them the The output of airodump-ng start wlan0 doesn;t find any processes that could cause trouble

I can't install another network management because i can't connect to the internet with ubuntu right now... 

:(

---

### Post by hakermania on 2011-02-13
Download this and insert it via USB into ubuntu [http://launchpadlibrarian.net/15738261/wifi-radar_1.9.9-1.1_all.deb](http://launchpadlibrarian.net/15738261/wifi-radar_1.9.9-1.1_all.deb)

---

### Post by leon.vitanos on 2011-02-14
Every deb in ubuntu needs internet connection to download packages.. So i cannot install something.. Guys any ideas? Should i format ubuntu...? ](*,)

---

