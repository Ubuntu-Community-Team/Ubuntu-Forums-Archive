---
title: "Epson Artisan 710 All In One"
date: 2011-01-26
forum: General Help
---

### Post by DrWho8 on 2011-01-26
I have an Epson Artisan 710 printer, which Ubuntu recognized and I can print. I can not use the scanner. I have been to the Epson site and tried to find scanner drivers but was unsuccessful. Is there anyone in this forum who has gotten the scanner to work and how did you do it?

Thanks, TD

---

### Post by SoFl W on 2011-01-26
I don't know when you looked but the site said they were having problems.

Go to the [COLOR=DarkOrchid]BOTTOM[/COLOR] set of links. 
[SIZE=1]-** Image Scan! for Linux & Photo Image Print System Lite**
[/SIZE]                                                  [SIZE=1]                                                                                                                                                             Artisan 710,[/SIZE][SIZE=1]Epson
Stylus Photo PX710W/
[/SIZE][SIZE=1]TX710W                                                                                   [/SIZE]
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)
Once you get there you will have to download several packages for your system.  It might give you a dependency error, because the packages are not in the correct order.  You might have to install a package further down on the page first.  (If I remember correctly) 



I have the Workforce 610 and used these other threads:
[http://ubuntuforums.org/showthread.php?t=1393162](http://ubuntuforums.org/showthread.php?t=1393162)
[http://ubuntuforums.org/showthread.php?t=1407631](http://ubuntuforums.org/showthread.php?t=1407631)

---

### Post by DrWho8 on 2011-01-26
This is what I had to install, and now it works.

ibltdl3_1.5.26-1ubuntu1_amd64.deb
[http://mirror.pnl.gov/ubuntu//pool/main/libt/libtool/libltdl3_1.5.26-1ubuntu1_amd64.deb](http://mirror.pnl.gov/ubuntu//pool/main/libt/libtool/libltdl3_1.5.26-1ubuntu1_amd64.deb)

iscan-data_1.6.0-0_all.deb
[http://linux.avasys.jp/drivers/iscan-data/1.6.0/iscan-data_1.6.0-0_all.deb](http://linux.avasys.jp/drivers/iscan-data/1.6.0/iscan-data_1.6.0-0_all.deb)

iscan_2.26.1-3_amd64.deb
[http://linux.avasys.jp/drivers/iscan/2.26.1/iscan_2.26.1-3_amd64.deb](http://linux.avasys.jp/drivers/iscan/2.26.1/iscan_2.26.1-3_amd64.deb)

[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/)

Which leads to 
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do)

Maybe this will help someone else.

---

### Post by SoFl W on 2011-01-27
Glad you got it working and thanks for posting the solution, it might help someone else.  
(You can mark the thread "solved" in the thread tools at the top)

---

