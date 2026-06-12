---
title: "I lost my GUI"
date: 2009-11-01
forum: General Help
---

### Post by john5023 on 2009-11-01
I recently upgraded to Karmic Koala from Jaunty.  I noticed via the software center I had Python 2.6 and Python 3.1 installed.  I removed 2.6.  I was given a warning that Ubuntu was going to remove some packages.  Unfortuneately I did not pay attention to what the packages were and during the uninstall of 2.6 my Ubuntu GUI was lost and all I have is the command line to work with.  I have attempted to install ubuntu-desktop but I also have no internet connection.  I am using a laptop with wireless internet access, but I also used my ethernet connection.  Ifconfig shows the host ip address as 127.0.0.0, ifconfig eth0 shows no ip address.  So I guess i have two questions.  How can I get my desktop back, and how can I enable eth0 to establish an internet connection to run apt-get to install packages?  I have tried startx and that only runs a cleaner terminal.  Any help is greatly appreciated as I am very happy with Ubuntu and would like to resolve this issue without having to reinstall it.  Thanks

---

### Post by liquidbee on 2009-11-01
```
sudo ifconfig eth0 up

```

Any changes ?

---

### Post by lswb on 2009-11-01
Assuming your wired ethernet is connected to a router of some kind, try plugging in and 

```

sudo ifconfig eth0 up
sudo dhclient eth0

```

---

### Post by john5023 on 2009-11-01
Hey lswb and Liquidbee those commands worked and I was able to download and install the ubuntu desktop!!!  While the desktop was installing I saw several references to Python 2.6.  Note to self, "Never uninstall Python 2.6"  Thanks again guys for the help and making ubuntu forums a great place for support.

-john5023

---

