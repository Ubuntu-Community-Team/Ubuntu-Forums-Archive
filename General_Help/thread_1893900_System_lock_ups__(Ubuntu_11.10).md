---
title: "System lock ups  (Ubuntu 11.10)"
date: 2011-12-11
forum: General Help
---

### Post by larsjuh on 2011-12-11
Hello,

First of all, my laptop specs are:

:: Processor
Intel Core i7 2630QM 2 GHz
:: Mainboard
Intel HM65
:: Memory
4096 MB, DDR3-1333 (1x4 GByte, max. 8GByte, 2 Banks)
:: Graphics adapter
NVIDIA GeForce GT 540M - 1024 MB, Core: 672 MHz, Memory: 900 MHz, Shader clock: 1344 MHz, NVIDIA Optimus, ForceWare 266.72
:: Harddisk
Samsung HN-M500MBB, 500GB 5400rpm 5400 rpm, 8 MByte Cache, Sata II 300

I am using ubuntu 11.10 (which looks and works awesome btw)
But i am experience a little problem, when i am either installing, copying etc, my system gets short freezes (like 2-3 sec) 
I can't really multi task, it looks like i am working on a 1ghz CPU with 256 MB ddr.

Its like all the processing power goes to the installing/copy process and i have nothing left to do other things (like browsing the web)

Any1 have an idea, or has the same experience? Im trying to fix this.

Thanks

---

### Post by carranty on 2011-12-11
I'm not running 11.10 so can't help with specifics, but try running top in a terminal

```
top
```

and then copying a file.  This will show you the name of the process that is clogging up your system.  If you post the offending process, it might help someone more knowledgeable than me help you out.

---

### Post by larsjuh on 2011-12-11
Thanks for your answer,

I made a screenshot of when installing something

It seems to be mount.ntfs ? it uses like 90%+ CPU whole the time.

When i did this, and tried to make a screenshot (with prt sc) my mouse were frozen for like 5-6 sec..

---

### Post by larsjuh on 2011-12-11
Looks pretty much to me, only for installing or unzipping something?

---

### Post by larsjuh on 2011-12-12
I've found at least what the problem is...

Its a "bug" in ntfs-3g

I don't get it, am i the only one who gets this though?
There must be more people? If you are not experiencing this, are you using a dual boot? (windows/linux , like i am) or just linux only..

Im curious

Source:
[https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/392204](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/392204)

---

### Post by nickjhs on 2012-01-06
Same here, it seemed to start when using chromium, then because I thought this was an issue with the browser I tried to remove it and synaptic locked, then machine started locking soon after boot up, now I have refined the issue to two areas

1. the minimise/maximise/quit buttons do not work,to shut down programs I need to navigate to file-> quit

2. the machine appears locked because it is unable to jump between open programs. Once the open program has been closed then I can get back to the desktop and the windows/app screen



Any thoughts ?

---

