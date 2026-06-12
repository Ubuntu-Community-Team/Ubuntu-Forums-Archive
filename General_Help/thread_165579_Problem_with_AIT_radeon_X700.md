---
title: "Problem with AIT radeon X700"
date: 2006-04-24
forum: General Help
---

### Post by xptiger on 2006-04-24
I've installed ubuntu 5.04, 5.10 and 6.06 beta on my pc many times already, and each time i install i will get error message "Failed to start the X server (your ghapical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagose the pronblem?" and when i answer YES, i got all the stuff that i don't know on the screen. my pc specification is: HDD 160G with 8partitions , AMD 3800+ x2 64bit, Radeon X700 PCI E 256MB, Gigabit A8N Sli Mother board. Sorry i really novice about linux and really want to install Ubuntu.

---

### Post by MeneK on 2006-04-30
Edit /etc/X11/xorg.conf (you could use nano: sudo nano /etc/X11/xorg.conf ). Change the line Driver from "ati" to "vesa".

```

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon X700 (RV410)"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

```

Afterwards, you can read [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") and get the non-free ati driver fglrx to work.

---

### Post by macarrao37 on 2006-06-25
I have the same problem, and i cant fix editing xorg.conf... when i do that, i just get a blank screen with no signal to the monitor..
Whats wrong?

---

