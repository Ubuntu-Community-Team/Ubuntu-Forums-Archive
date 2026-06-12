---
title: "Duplex printing on Canon MP780 Disappeared with 12.04"
date: 2012-07-14
forum: General Help
---

### Post by nowhere@cox.net on 2012-07-14
I was running 11.10 and the "recommended" gutenprint driver for the Canon MP780 worked brilliantly including duplex printing. Now, in 12.04 duplex is not allowed. 

How can I enable it in the current driver or where can I get the older driver and install it?

Thanks!

---

### Post by BigTuna on 2012-08-16
Any luck with finding a fix? I came across the same problem with my MP780 as well. 

FWIW, I also have the same issue with Fedora 17. 

F17 uses v5.2.9 Gutenberg driver and Ubuntu 12.04 uses v5.2.8 Gutenberg driver. I believe Ubuntu 11.10 used v5.2.7 and that seems to work. Perhaps something broke between 5.2.7 and 5.2.8?

---

### Post by BigTuna on 2012-08-17
After searching around a bit I found that some have had luck with the ip4100 driver for the Canon MP780.

[http://askubuntu.com/questions/134416/how-can-i-get-canon-pixma-mp780-printer-to-print](http://askubuntu.com/questions/134416/how-can-i-get-canon-pixma-mp780-printer-to-print)

Indeed, after switching to the Canon PIXMA iP4100 - CUPS+Gutenprint v5.2.8-pre1 driver, my MP780 appears to work just fine (including duplex). I did not need to install cnijfilter-pixusip4100series as the link suggests.

In case you don't know, you can switch to this driver by directing your web browser to localhost:631. Select Administration --> Manage Printers. Click on the appropriate queue name. Select Modify Printer from the drop-down box. Hit Continue twice and then select the ip4100 driver from the driver drop-down box. Click Modify Printer and you should be done.

---

