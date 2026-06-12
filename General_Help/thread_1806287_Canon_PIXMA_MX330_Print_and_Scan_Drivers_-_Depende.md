---
title: "Canon PIXMA MX330 Print and Scan Drivers - Dependency Problem"
date: 2011-07-17
forum: General Help
---

### Post by kroq-gar78 on 2011-07-17
Hello Ubuntu Forums Community,

I am trying to install my Canon PIXMA MX330 print driver on my 64-bit WUBI install of Ubuntu 11.04 Natty, and I keep getting some unresolved dependencies:

```

kroq-gar78@av3-ubu64:~/Downloads/cnijfilter-mx330series-3.10-1-i386-deb/packages$ sudo dpkg -i --force-architecture cnijfilter-common_3.10-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 309784 files and directories currently installed.)
Preparing to replace cnijfilter-common:i386 3.10-1 (using cnijfilter-common_3.10-1_i386.deb) ...
Unpacking replacement cnijfilter-common:i386 ...
dpkg: dependency problems prevent configuration of cnijfilter-common:i386:
 cnijfilter-common:i386 depends on libc6 (>= 2.3.4-1).
 cnijfilter-common:i386 depends on libcupsys2 (>= 1.2.1) | libcups2.
 cnijfilter-common:i386 depends on libpopt0 (>= 1.7).
dpkg: error processing cnijfilter-common:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cnijfilter-common:i386

```It turns out that I have an older version than required of libc6 and libpopt0. Is there any way to upgrade my libraries to the required version to make the driver work? I used --force-architecture because I have a 64-bit computer and the drivers/debs are 32-bit. I have installed this on my Ubuntu 32-bit 10.10 and 10.04 installs with no troubles, so why would there be a dependency problem in a newer version?

I am using the instructions from this site: [http://www.bartonphillips.com/mx330.php](http://www.bartonphillips.com/mx330.php)

Any help would be appreciated.

---

### Post by kroq-gar78 on 2011-07-19
*bump* I would really like this problem to be solved. Could I possibly install the correct versions of the libraries from the ubuntu pool? Would that even be safe (as in stable) for my system? Does the ubuntu package pool HAVE the library versions that I need?

Thanks in advance,
kroq-gar78

---

### Post by kroq-gar78 on 2011-07-20
*bump* again... I would really like to use this printer with ubuntu... It worked on one of my 10.10 installs, so why wouldn't it work on this 11.04 install?

---

### Post by kroq-gar78 on 2011-08-27
please?

The printer and scanner is working now, but I really wonder what is the deal with the dependencies.

Any help is appreciated.

---

### Post by kroq-gar78 on 2011-11-08
*LONG OVERDUE BUMP!*

The upgrade to Ubuntu 11.10 made my machine say that it has to uninstall the print/scan drivers because they are broken packages. It says that it needs the packages ending in "*:i386", but I have all of the regular packages. I have the 64bit packages, not 32bit. 

Thanks in advance,
kroq-gar78

---

### Post by Nickmunstr on 2011-12-28
I am having this exact same problem in 11.10 - did you ever find a resolution?

Thanks!

---

### Post by kroq-gar78 on 2011-12-28
> **Nickmunstr said:**
> I am having this exact same problem in 11.10 - did you ever find a resolution?

Thanks!
Nope, no solution yet. I'm lucky enough to have a separate computer (my mom's netbook) that's 32-bit, so that's how I'm printing in color now :/

So, let this post double-serve as a nice and friendly *bump*!!!!

PLEASE!!!

---

### Post by zoso990 on 2012-01-05
Have a look at this website:

[http://www.upubuntu.com/2011/12/how-to-install-canon-pixma-mp-canon-mx.html](http://www.upubuntu.com/2011/12/how-to-install-canon-pixma-mp-canon-mx.html)

I'm running Linux Mint 12, which is based off of Ubuntu Oneiric 11.10, and I successfully got my Canon MX340 multifunction machine working wirelessly on my 64-bit laptop using the PPA and packages off of that website. The instructions are very simple to follow, unlike everything else I've tried. Uninstall whatever cnijfilter and scangear packages you have installed, and try the ones from that website.

The scangear packages are actually not listed on that website, but after you add the PPA, go into Package Manager and search for "scangear". They should show up, and then you can install the appropriate one (the one without the i386).

The scangearmp application doesn't work, but Simple Scan now allows me to scan documents successfully. Printing works flawlessly, and now I can even change the print quality and grayscale settings directly from the print options window.

Good luck and let me know how it works out for you!

---

### Post by Nickmunstr on 2012-01-05
Incredible Zoso - that worked perfectly, thank you!

---

