---
title: "How do you monitor system performance historically?"
date: 2011-09-02
forum: General Help
---

### Post by nik1979 on 2011-09-02
How do I get a historical output from System monitor? I appreciate it can give live graphical performance, but I was wondering if someone made a way for a non-app dev or non-IT like me see what happened in the entire time my system was on. 

I was imagining turning system monitor on and after 4-5 hours of use before I close my laptop I can just take a historical and then save it. 

my intended use is to be able to track its resource demands, how using the 4 screens may be affecting performance. The no. of windows I open and the kinds of programs I am using. Also it would help seeing how historically effective my internet and network bandwidth was. 

Thanks in Advance

Ubuntu 11.04
Lenovo Idea Pad y430
No-Dual boot

---

### Post by Habitual on 2011-09-02
I use and LOVE sar from the sysstat package.

[http://linuxboxadmin.com/articles/tools-and-utilities/tracking-system-performance-using-sar.html](http://linuxboxadmin.com/articles/tools-and-utilities/tracking-system-performance-using-sar.html)

Homepage:
[http://sebastien.godard.pagesperso-orange.fr/features.html](http://sebastien.godard.pagesperso-orange.fr/features.html)

---

### Post by dcstar on 2011-09-03
> **Habitual said:**
> I use and LOVE sar from the sysstat package.

[http://linuxboxadmin.com/articles/tools-and-utilities/tracking-system-performance-using-sar.html](http://linuxboxadmin.com/articles/tools-and-utilities/tracking-system-performance-using-sar.html)

Homepage:
[http://sebastien.godard.pagesperso-orange.fr/features.html](http://sebastien.godard.pagesperso-orange.fr/features.html)

And **sarcheck** is a commercial package that has been around for years (even before Linux) turning sar data into valuable info:

[http://www.sarcheck.com/](http://www.sarcheck.com/)

---

### Post by nik1979 on 2011-09-03
Thanks checking this out. :D

---

### Post by tommpogg on 2011-09-04
Is there a simple tool to monitor the network traffic?
My contract with an internet provider limits my download/upload traffic to 3 Gb/month. So I need to know the cumuative traffic on my PC.

Thank you

---

### Post by nik1979 on 2011-09-06
Thanks for the help guys, I checked it out. Although in the end I ended up using System Profiler and Benchmark [http://hardinfo.berlios.de/](http://hardinfo.berlios.de/) because it was easier to install. 

Sorry for the brain fart, I should have checked first software center.

[s]Another Brain fart, I can't figure out how to put Solved in this thread?[/s]

---

### Post by tommpogg on 2011-09-06
> **nik1979 said:**
> Thanks for the help guys, I checked it out. Although in the end I ended up using System Profiler and Benchmark [http://hardinfo.berlios.de/](http://hardinfo.berlios.de/) because it was easier to install. 


Can it be used to monitor the network?

Thanks

---

### Post by Habitual on 2011-09-11
Sorry for the late reply, but you can monitor your network (TX/RX) usage with the following shell script...

```

#!/bin/bash
echo "Tx (MiB) for this hour is" $(for i in `date +%H` ; do vnstat --dumpdb | \grep "h;$i" ; done | cut -c 17- | cut -d\; -f1)
echo "Rx (MiB) for this hour is" $(for i in `date +%H` ; do vnstat --dumpdb | \grep "h;$i" ; done | cut -c 17- | cut -d\; -f2)

```
**The above reports for *hourly*.**

This script _would have to be modified_ to give you the total(s) metric you are looking for (month) and I'd be willing to do that.
It also requires the vnstat package to be installed

```
sudo apt-get install vnstat
```

I am subscribed with interest if you would like to proceed.

Please let me know...

---

