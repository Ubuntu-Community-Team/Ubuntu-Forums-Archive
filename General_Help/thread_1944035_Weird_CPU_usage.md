---
title: "Weird CPU usage"
date: 2012-03-20
forum: General Help
---

### Post by Excelzn on 2012-03-20
Ok, so I have an Acer Aspire One netbook that was running Windows XP Home and I decided to install Ubuntu 11.04 on it. The problem is that this netbook's USB ports are all broken so I pulled the HDD and plugged it into my desktop to do the install. After plugging it back into the netbook, I tried to open a pdf file, which sent my CPU usage from barely anything to 100% and locked up the system. I thought it might be the Desktop Environment so I downloaded XFCE and installed it, but the problem just got worse (opening Thunar now also causes my CPU to skyrocket). I can't figure out why this is happening. Any suggestions?

---

### Post by dmouck on 2012-03-20
To see what's hogging the CPU, open up a terminal and enter "top" . Then, while it is displaying the CPU usage of your various processes, try to open the PDF and watch for the process that's taking up your CPU.

---

