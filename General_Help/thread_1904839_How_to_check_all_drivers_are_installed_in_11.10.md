---
title: "How to check all drivers are installed in 11.10"
date: 2012-01-05
forum: General Help
---

### Post by meetdilip on 2012-01-05
How to see if all drivers are installed ? Is there anything similar to device manager in Ubuntu ? Mine is Dell laptop with AMD graphics card.

---

### Post by Paddy Landau on 2012-01-06
All drivers are automatically downloaded and installed. However, Ubuntu may find proprietary drivers that need to be enabled.

Open *Additional Drivers*. If you see any there, you can enable them there.

What do you need them for -- is something in your system not working?

---

### Post by Mark Phelps on 2012-01-06
There is something similar to Device Manager, but t unlike with MS Windows, you don't need to worry about drivers.  As already mentioned, the proper drivers are found and installed during initial setup.

But, I would hold off on installing any additional drivers unless you're having real problems.

---

### Post by meetdilip on 2012-01-07
> **Paddy Landau said:**
> All drivers are automatically downloaded and installed. However, Ubuntu may find proprietary drivers that need to be enabled.

Open *Additional Drivers*. If you see any there, you can enable them there.

What do you need them for -- is something in your system not working?

Thanks for the reply. Just wondering if graphics card and sensors drivers are installed. It has finger print reader and fall safety sensors. Also, I want to disable tapping in touch pad which is quite annoying. I checked additional drivers, it has 2 AMD drivers which does not activate even after 1 + hour of downloading (my connection is a bit slow).  But among 3, wireless card driver shows green.

---

### Post by meetdilip on 2012-01-07
> **Mark Phelps said:**
> There is something similar to Device Manager, but t unlike with MS Windows, you don't need to worry about drivers.  As already mentioned, the proper drivers are found and installed during initial setup.

But, I would hold off on installing any additional drivers unless you're having real problems.

Thanks Mark. Any tool which shows system devices info. Like CPU-Z, Speccy for Windows ?

---

### Post by bluexrider on 2012-01-07
> **meetdilip said:**
> Thanks Mark. Any tool which shows system devices info. Like CPU-Z, Speccy for Windows ?
YES!

I use HardInfo. Available here [http://linux.softpedia.com/get/System/System-Administration/HardInfo-9395.shtml](http://linux.softpedia.com/get/System/System-Administration/HardInfo-9395.shtml)

---

### Post by meetdilip on 2012-01-08
Very useful app. Thanks bluexrider. It does not show my graphics card installed :(

May be it is still not having drivers. I tried 

> sudo apt-get install fglrx-amdcccle-updates fglrx-updates


but it said all drivers are up to date like that. :confused:

---

