---
title: "xbox 360 streaming  - how!?"
date: 2010-01-14
forum: General Help
---

### Post by mcclunyboy on 2010-01-14
Hi,

I am trying to stream to my xbox 360,,,

I have a wireless belkin adapter attached by USB and attempted to use ushare but it didnt work. does anyone know anywhere with detailed instructures for tversity and wine (im a noob) or any other way to stream to xbox for free?!

---

### Post by Fire_Chief on 2010-01-14
Here's a good guide that's fairly up to date for configuring uShare on Ubuntu.
[http://nexus172.wordpress.com/2009/04/26/how-to-stream-video-to-your-xbox360-using-ubuntu-ushare/]("http://nexus172.wordpress.com/2009/04/26/how-to-stream-video-to-your-xbox360-using-ubuntu-ushare/")

HTH!

---

### Post by mcclunyboy on 2010-01-15
I have tried this and I am getting an error in regard to me using "wlan0".

Do i need to specify a port or something in the conf file?

Is it a problem to do with my belkin adapter?

---

### Post by Fire_Chief on 2010-01-15
I got the same error when starting ushare from the command line however it still started up and was listening on the wireless interface IP address. This is confirmed in the startup info and I see the port listening in netstat.```
**Interface wlan0 is down**.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Initializing UPnP subsystem ...
Starting in XboX 360 compliant profile ...
Starting in DLNA compliant profile ...
**UPnP MediaServer listening on 192.168.1.58:49152**

``````
tcp        0      0 0.0.0.0:49152           0.0.0.0:*               LISTEN      13620/ushare
```

Do you see this result as well? Also, you may want to check if the 360 just sees the media shares anyway once ushare is running.

Cheers!

---

