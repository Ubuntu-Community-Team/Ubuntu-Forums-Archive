---
title: "wireless internet disabled"
date: 2010-10-25
forum: General Help
---

### Post by nedearb on 2010-10-25
I have a windows 7 laptop and I just got Linux. But i'm having trouble connecting to my local wireless network. I'm using a card : "Linksys Wireless-G Notebook Adapter with SpeedBooster" and when I'm in Linux it says its disabled. But on windows it works perfectly. Please help!

Thanks in advance. :)

---

### Post by yetiman64 on 2010-10-25
> **nedearb said:**
> I have a windows 7 laptop and I just got Linux. But i'm having trouble connecting to my local wireless network. I'm using a card : "Linksys Wireless-G Notebook Adapter with SpeedBooster" and when I'm in Linux it says its disabled. But on windows it works perfectly. Please help!

Thanks in advance. :)

Have you looked in System > Administration > Hardware Drivers, there may be a download there for your network card. If not see below.

Check this link, [http://ubuntuforums.org/showthread.php?t=1419368](http://ubuntuforums.org/showthread.php?t=1419368), you may have a firmware problem.

In terminal run,
```
dmesg | grep firmware
```If it comes back with an entry similar to the link, you may be able to fix it with the instructions there (particularly post #6).

---

