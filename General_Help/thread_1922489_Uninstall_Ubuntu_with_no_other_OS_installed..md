---
title: "Uninstall Ubuntu with no other OS installed."
date: 2012-02-08
forum: General Help
---

### Post by Asfixia on 2012-02-08
I used to use Windows, but then I heard about Linux, the Ubuntu, BackTrack and Debian stuff, I started to read about this system that sounded marvellous to me, I've read everything was free, that there were no viruses, that I'm never going to have any issue, and damn... After using Windows for many years, Linux was temptating, so I decided to isntall Ubuntu alongside with Windows, then, I fall in love with Ubuntu, so I decided to uninstall Windows, it worked well after a few days and now, it's a headache to me, it's giving me a lot of problems (More problems than Windows) all started when my computer dind't wanted to turned of, so I was forced to use Terminal when I want to Reboot it or Turn it off, then, it didn't mount External HDD or USB's, then, when I turn it on, it says: "HDD disk controler is not ready or is not present, press S to skip or M to manually Mount." So, when I turn it on I do always have to press S, and wait like 15 minutes for my desktop to load even if I have 2.5 GB of RAM and a Core 2 Duo processor (It may not be the best of the market, but it's not to bad) and now, it can't even read CD'S, so when I try to install Windows from Boot, it inmediatly runs Ubuntu, I'm tired of Ubuntu, was a big deception to me, the idea is good, but the results were not good to me.
Now, please help me, I need you to solve this, how can I install Windows and delete Ubuntu without lossing any files?
Please remind that it does not what to read CD's or I don't know what happens, but tell me please, as I need to work and study, and for that I need a working computer.

---

### Post by Bucky Ball on 2012-02-08
Something obviously screwed up when you uninstalled Windows or with a Ubuntu update. You are jumping the gun blaming your woes wholly on Ubuntu though.

Tried backing up your files (you could do this by booting from the Ubuntu LiveCD and 'Try Ubuntu' then saving them to an external device or USB dongle) and reinstalling a STABLE release of Ubuntu??? (you might try the current long-term support release 10.04 LTS).

You haven't mentioned what release of Ubuntu you have been using, either. 

To install Windows you need to boot from the install CD so the fact that Ubuntu can't read CDs is sort of irrelevant for this purpose. You need to alter the boot device to CD, NOT hard drive. I would boot from the Ubuntu CD, Try Ubuntu, open Gparted (partition editor), delete all your Ubuntu partitions (EXT*) leaving the whole disk as free space (leaving any NTFS or FAT partitions you may have created and want to keep) then boot from the Win install CD.

---

