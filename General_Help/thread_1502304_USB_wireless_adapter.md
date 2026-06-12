---
title: "USB wireless adapter"
date: 2010-06-05
forum: General Help
---

### Post by Cpierce on 2010-06-05
I am using 10.04. I am looking for a USB wireless adapter that will work properly when plugged into Ubuntu 10.04 that is already installed. I want it to handle N networks as well as G. I do not want to have to use "nidswrapper" ??????  I have looked at some tables listing adapter here, but would rather have some personal recommendations.

---

### Post by dino99 on 2010-06-05
[http://linux-wless.passys.nl/query_hostif.php?hostif=USB](http://linux-wless.passys.nl/query_hostif.php?hostif=USB)

[http://www.google.fr/search?as_q=usb%2Bwireless%2Badapter%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.fr/search?as_q=usb%2Bwireless%2Badapter%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by Cpierce on 2010-06-05
Thank you for the info. Very helpful.  I assume that if it is green and has been included in kernel since xx/xx/xxxx then it should plug in and work right away. Is that correct ?

---

### Post by Cpierce on 2010-07-15
Based on the table provided above, I purchased a Linksys WUSB600N ver. 1.  The table showed this adapter as "green" and said "Driver included in mainline kernel since 2.6.29". I thought I could just plug it in and it would see it and work. I was wrong. I ran the sysinfo program, and the computer is not seeing the adapter. 

Any help on getting this thing to work is greatly appreciated.

---

### Post by Cpierce on 2010-07-15
A little more info. I went to package manager and saw there was some rt2500 and some other packages, but not the rt2870 I needed. I just downloaded the rt2870 tar which is supposed to be for  WUSB600N version 1 according to the table above. I extracted, make install and rebooted. Nothing. If I pull out the 600, then I get a message that "network has been disconnected". 
I went back to sysinfo and it is still not seeing the adapter. 

Please Help

---

### Post by Cpierce on 2010-07-15
Tried this [http://ubuntuforums.org/showthread.php?t=1452178](http://ubuntuforums.org/showthread.php?t=1452178) and still not working.

---

### Post by Cpierce on 2010-07-15
I got it working, for me this did it
[http://psk87.blogspot.com/2010/06/linksys-wusb600n-step-by-step.html](http://psk87.blogspot.com/2010/06/linksys-wusb600n-step-by-step.html)

working with WPA2 and seems to be fast

---

