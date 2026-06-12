---
title: "Pidgin can't connect to any Server"
date: 2009-12-18
forum: General Help
---

### Post by nikhilbhardwaj on 2009-12-18
i've set up my mobile internet connection
[http://ubuntuforums.org/showthread.php?t=1353713](http://ubuntuforums.org/showthread.php?t=1353713)

i have to connect with 
sudo wvdial

but the network applet shows no connection even when i'm connected

and pidgin says
waiting for network connection

i can't connect to gtalk or msn

so how can i get ubuntu to recognize my network connection

---

### Post by nikhilbhardwaj on 2009-12-24
bump

---

### Post by Belinrahs on 2009-12-24
Hey nikhilbhardwaj, and welcome to the Ubuntu forums.

What version of Ubuntu are you using? i.e. 9.10/Karmic Koala, 9.04/Jaunty Jackalope.

What are you using to connect to mobile internet? (i.e. 3G Broadband "LaptopConnect" card.) What brand and model?

When you connect using sudo wvdial, and it connects, can you access the internet using your Web browser (Firefox) or any other programs?

Thanks!

---

### Post by nikhilbhardwaj on 2010-01-01
> **Belinrahs said:**
> 

What version of Ubuntu are you using? i.e. 9.10/Karmic Koala, 9.04/Jaunty Jackalope.

What are you using to connect to mobile internet? (i.e. 3G Broadband "LaptopConnect" card.) What brand and model?

When you connect using sudo wvdial, and it connects, can you access the internet using your Web browser (Firefox) or any other programs?

Thanks!
I'm using 9.10 Karmic Koala x86_64
i'm using a cdma 1x usb modem the company is epivalley
my isp is tata i'm in india

yes
i can access the internet with sudo wvdial using firefox
but the gnome network applet still shows disconnected
moreover i can install and update packages normally too

but pidgin or empathy can't connect
they show a message 
waiting for network connection

---

### Post by Iowan on 2010-01-01
Network Manager isn't controlling the connection, so it claims "no connection". It may be possible to change */etc/NetworkManager/nm-system-settings.conf*.

---

### Post by nikhilbhardwaj on 2010-01-03
> **Iowan said:**
> Network Manager isn't controlling the connection, so it claims "no connection". It may be possible to change */etc/NetworkManager/nm-system-settings.conf*.
could you please elaborate
what changes am i required to make??

---

### Post by Iowan on 2010-01-03
```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
```
No guarantees for success, but change to "managed=true"
I presume you know to use **sudo nano** or **gksudo gedit** to edit the file... otherwise, ask for details. :)

---

### Post by noSelf on 2010-01-15
i had the exact same problem on 64-bit 9.10 (with a dsl line, and using NetworkManager) - i couldn't connect to any of the 4 IM accounts i have, couldn't figure it out. My 32-bit 9.10 machine had no problem. All other network services (email, web, ssh, OpenVpn) worked fine.

i tried again after the latest update, which included the 2.6.31-17 kernel, and it's suddenly working again!

---

