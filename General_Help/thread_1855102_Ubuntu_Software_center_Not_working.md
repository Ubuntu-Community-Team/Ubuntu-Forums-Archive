---
title: "Ubuntu Software center Not working ?"
date: 2011-10-05
forum: General Help
---

### Post by Benjotter on 2011-10-05
Hi Peeps

Basically I've run in to another software center failure it again will not let me install or remove apps at all I have no idea why? it worked after fresh format but after I updated everything I rebooted and it stopped working. Please could some one give me some advice.

An unhandled error occured

There seems to be a programming error in aptdaemon. This is the software that allows you to install/remove software and to perform other package management related tasks.

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

My System is 

Asus M5A78L/USB3 AMD Socket AM3 8 Channel HD Audio ATX Motherboard

AMD Phenom II X4 955 Black Edition Socket AM3 3.2 GHz 6MB L3

G-Skill 8GB (2x4GB) DDR3 1600Mhz RipjawsX Memory Kit CL9 (9-9-9-24) 1.5V

WD 500GB 3.5" SATA 6Gb/s Caviar Blue Hard Drive - 7200RPM 16MB Cache

CM Storm Enforcer Case

Coolermaster 650W GX PSU

iteOn iHAS124-19 24x DVD±RW DL & RAM SATA Optical Drive

Arctic Cooling Freezer 7 Pro

Asus pg221 Gaming Monitor

Thanks in advance for reading

---

### Post by Benjotter on 2011-10-06
Ok nobody replied to my thread but when i woke up this morning software center was working :)

Thanks anyway guys

---

