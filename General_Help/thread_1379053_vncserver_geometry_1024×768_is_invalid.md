---
title: "vncserver: geometry 1024×768 is invalid"
date: 2010-01-12
forum: General Help
---

### Post by placrsaeed on 2010-01-12
Hi All,

I am trying to get a GUI connection with my Linux VPS, it is running Ubuntu Karmic Koala.

I am following this tutorial ([http://markus.revti.com/2009/08/installing-vnc-remote-desktop-on-ubuntu-linux-vps/](http://markus.revti.com/2009/08/installing-vnc-remote-desktop-on-ubuntu-linux-vps/)). However at step 4,  I am getting this error;

'vncserver: geometry 1024×768 is invalid'

Please help.

Thanks,

Saeed.

---

### Post by upbeat.linux on 2010-01-12
In step 4 it says:

```
vncserver :1 -geometry 1024×768 -depth 16 -pixelformat rgb565
```

Make sure the 1024x768 is an x (letter x lower case). You might even want to try:

```
sudo vncserver :1 -geometry 1024×768 -depth 16 -pixelformat rgb565
```

---

### Post by placrsaeed on 2010-01-13
Yes, that solved the problem. Thank you very much.

Saeed

---

