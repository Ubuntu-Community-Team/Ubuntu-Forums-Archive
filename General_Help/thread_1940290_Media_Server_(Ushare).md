---
title: "Media Server (Ushare)"
date: 2012-03-13
forum: General Help
---

### Post by bOgNeR17 on 2012-03-13
I am trying to install UShare so that I can stream media from my computer to my Xbox 360. I am following the tutorial here: [http://nexus172.wordpress.com/2009/04/26/how-to-stream-video-to-your-xbox360-using-ubuntu-ushare/](http://nexus172.wordpress.com/2009/04/26/how-to-stream-video-to-your-xbox360-using-ubuntu-ushare/)

Only problem so far is I'm not sure about the configuration file where it says:

```
USHARE_IFACE=eth0 *(the name of which ethernet adapter you’ll send the data over)*
```

I am using a wireless USB adapter to connect to my router what would I put in there instead of eth0?

Thanks

---

### Post by bOgNeR17 on 2012-03-13
bump

---

### Post by raja.genupula on 2012-03-13
in the output of ```
ifconfig -a
``` look whats your device

---

### Post by bOgNeR17 on 2012-03-13
Okay I found out that its wlan0 not the only problem is that it wont let me save the configuration file it says "Can't open file to write", anyone know how to work around this??

---

### Post by raja.genupula on 2012-03-13
you have to open that file with sudo .
```
sudo gedit /path/to/file
```

---

