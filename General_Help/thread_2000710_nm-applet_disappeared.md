---
title: "nm-applet disappeared"
date: 2012-06-10
forum: General Help
---

### Post by johanmattsson on 2012-06-10
I upgraded a few packages and network-manager disapeared from the unity panel.

Running nm-applet in a terminal gives me this:

```

johan@floden:~$ nm-applet 
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon

(nm-applet:1849): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

```

What should I do about it?

---

### Post by drpjkurian on 2012-06-10
Try this [link ]("http://www.google.com/url?sa=t&rct=j&q=restore%20nm%20applet%20in%20unity&source=web&cd=7&ved=0CGoQFjAG&url=http%3A%2F%2Fmikebeach.org%2F2011%2F02%2F06%2Frestoring-the-network-manager-applet-in-ubuntu%2F&ei=ojLUT7DeKYLNrQfUw_T7Dw&usg=AFQjCNFpE_3NRqGOmO-mbh-rrEFY9aRAfQ&cad=rja")

---

### Post by codemaniac on 2012-06-10
You may find the below thread useful .

[http://ubuntuforums.org/showthread.php?t=1717648](http://ubuntuforums.org/showthread.php?t=1717648)

---

### Post by d3v1150m471c on 2012-06-10
network-manager sucks anyways.
```

apt-get install wicd wicd-gtk

```

---

### Post by johanmattsson on 2012-06-10
Thanks. I have tried all suggestions above except the wcid approach. I have a usb connected ZTE modem, lsusb tells me it is connected but nm-applet seems to be broken in some new way.

---

