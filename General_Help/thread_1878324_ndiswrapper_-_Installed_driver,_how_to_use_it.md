---
title: "ndiswrapper - Installed driver, how to use it?"
date: 2011-11-09
forum: General Help
---

### Post by Charkel on 2011-11-09
Hello. I installed ndiswrapper and followed this tutorial to install the correct driver for my dwa-140: [http://blog.greweb.fr/2011/01/how-to-make-dlink-dwa-140-perfectly-work-on-linux/](http://blog.greweb.fr/2011/01/how-to-make-dlink-dwa-140-perfectly-work-on-linux/)

And now:
```
# ndiswrapper -l
drt2870 : driver installed
```

But I cannot use the wpa command:
```
# wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.
```

How do I use this correct? My speed is still limited to about 1,5-2 M/s and I wanna be able to use my full 100Mbps internet :(

Thank you in advance.

---

### Post by gandaran on 2011-11-09
cant you just use network manager?
and did you try with linux drivers first,  the dwa-140 is supposed to work out of the box on ubuntu or maybe it's just needs a fix to load the right ralink linux driver, theres no need to use windows drivers with ndiswrapper.
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)

---

### Post by Charkel on 2011-11-09
With network manager, do you mean the one that comes with ubuntu or something I have to download?

I got B2 parhaps thats why :(

---

### Post by gandaran on 2011-11-09
> **Charkel said:**
> With network manager, do you mean the one that comes with ubuntu or something I have to download?

I got B2 parhaps thats why :(
okay, I see the B2 doesn't work on linux but only with windows drivers.

---

### Post by Charkel on 2011-11-10
BUMP because of page 20+

---

### Post by Charkel on 2011-11-11
Please someone help me get this working :(

---

