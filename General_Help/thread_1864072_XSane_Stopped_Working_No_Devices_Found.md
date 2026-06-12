---
title: "XSane Stopped Working: No Devices Found"
date: 2011-10-18
forum: General Help
---

### Post by gracchus on 2011-10-18
I used my scanner (a canon mx860) yesterday for the first time after installing xsane.  It worked fine.  The scanner is connected over the wireless network by an external wifi print server.  I tried to start the program today and now it's saying "No Devices Found".  I tried rebooting, running xsane as root, reinstalling xsane, and adding the scanner ip to /etc/sane.d/net.conf (even though I don't think this would be correct since its not a server sharing the scanner).  I can ping the scanner fine.  What else should I try?  This is really frustrating since it worked fine and then broke for no reason.

---

### Post by gracchus on 2011-10-18
Well an update is required.  I somehow fixed the detection problem by pinging the scanner while I started the program.  There's a different issue now where the graphics are messed up for the preview window so none of the buttons show including the one to grab a preview.  If I try to do a scan without using the preview window I get "operation was canceled".

---

### Post by gracchus on 2011-10-18
Well restarting the comp fixed the preview window and operation canceled problem.  I still had to ping the scanner to get it to detect it.  Weird bugs!

---

