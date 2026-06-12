---
title: "Help please am new to the Linux community"
date: 2010-01-24
forum: General Help
---

### Post by Zannith on 2010-01-24
1st: How can I get the driver for HD4850 

2nd: Says under system memory i'm only using like 509mb memory and I have 8gb RAM in my comp

Where can I get it to say my Ghz and HDD space?

Any protips for things I should do or watch for while using Ubuntu?    :confused:

---

### Post by duanedesign on 2010-01-24
Ubuntu installs the open source driver for ATI cards. You install that by going to System > Administration > Hardware Drivers and choose the package Ubuntu recommends a package for you. Some users however prefer the proprietary fglrx driver for various reasons. There is a wiki page that covers the two ways to install this driver. Installing it using the repository is preferred, but you will not get as new a version. I would however try that first. If you then determine that the performance is buggy or this is some issue, then i would try and install the driver fom the AMD site.

[Ubuntu wiki page]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") with instructions for installing ATI proprietary driver

[AMD website]("http://support.amd.com/us/gpudownload/Pages/index.aspx") where you can get the newest Catalyst Driver. (this link is referenced in the wiki above)


As far as the RAM. Where are you seeing this? You mention you are only using 509MB. Just to be clear, you are only using, or your computer only sees 509MB? 
You can go to System > Administration >. System Monitor then under the 'System' Tab you will see a section 'Hardware' where it will list your memory.

Another way to test this is to open a Terminal (Applications > Accessories > Terminal) and enter the following command:

```
free -m
```
here is the result, showing total memory available in the first column.
```
             total       used       free     shared    buffers     cached
Mem:          2764       2221        543          0        156        943
-/+ buffers/cache:       1121       1643
Swap:         4722          0       4722

```

---

### Post by linux nut on 2010-01-24
Tips: Don't give up on things right away if they don't work if u tinker with them a little bit they usually work.

---

### Post by junapp on 2010-01-24
> **Zannith said:**
> Where can I get it to say my Ghz and HDD space?
sounds like you might be interested in hardinfo. Install from synaptic package manager or from the terminal:```
sudo apt-get install hardinfo
```

[http://hardinfo.berlios.de/HomePage](http://hardinfo.berlios.de/HomePage)

after install it will likely be in Applications -> System Tools -> System Profiler and Benchmark

---

### Post by JiuJitsu500 on 2010-01-24
Do all updates first, then drivers, then tinker is my rule when doing a new computer for a friend or my own every now and then (got two old laptops i love playing with).

System monitor will tell you everything you need to know for the most part... System > admin > system monitor... CPU speed/usage, RAM, Network sent/recieved bytes, etc...

And 32-Bit OS's don't recognize more than a usable 3GB of RAM (you will probably see 2.9GB), to see your massive 8GB you'd have to get the 64-bit (that recognises up to 64GB)

And definately, Linux is meant to fall apart when you tell it to, and be rebuilt better than anything you imagined. that's the point... so embrace the fact that you will have to play and guess and rebuild and make mistakes and learn and so on and so on and so on.... then do it all over again periodically.... you get my point :) It's great fun learning this all, as I still definately am.... hope u find it as interesting as I do.

Oh... let me add, if you never update or change anything after you get it the way you want, you will never have a computer problem again... linux is literally that damn solid. But, you will want security updates, etc, so you will be tinkering often enough to learn at a pretty constant rate. Enough is customizable (everything) that you'll never run out of things to find out or tweak, and mess up then come back here for pro advice, or to other fantastic forums and websites :)

Community certainly describes it best, albiet an understatement to how helpful it can be, and is.

---

### Post by junapp on 2010-01-24
> **JiuJitsu500 said:**
> System monitor will tell you everything you need to know for the most part... System > admin > system monitor... CPU speed/usage, RAM, Network sent/recieved bytes, etc...
I was just about to edit my post to state just this - I went overboard suggesting hardinfo likely.

---

### Post by JiuJitsu500 on 2010-01-24
maybe not... I haven't used it so I can't judge :) but if you find it a good app then I can guarantee others do and will again... System monitor is just built in and is easiest for new users to see their things they want to... especially because it's GUI. As I become more involved, I start replacing old apps with new and improved ones... And still learning the terminal, I need lots of GUI to help lol

I think that's just the way I see the cookie crumbling :) I'm goona look up hard info now

---

