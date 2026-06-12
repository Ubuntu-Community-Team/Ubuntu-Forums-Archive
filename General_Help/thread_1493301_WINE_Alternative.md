---
title: "WINE Alternative"
date: 2010-05-25
forum: General Help
---

### Post by daldude on 2010-05-25
Is there a better way to run Windows programs in Ubuntu 9.04 64-bit other then WINE? I've tried the VMWARE Trial but after installing it I could not figure out how to run Windows Programs with it or even get it tunning. The instructions on the Webpage said to type in a command in a terminal window and then it ran Firefox and I could see some stats on VMWARE as if it was running on a server at VMWARE.

Thanks

---

### Post by bodhi.zazen on 2010-05-25
Most people use virtualization.

I suggest you look at VirtualBox

And yes, there is a bit of a learning curve with virtualization, but it works better / easier then wine, IMHO.

---

### Post by daldude on 2010-06-04
I tried  VirtualBox and removed it because it does not allow Windows access to your other partitions that are formatted in NTFS or FAT and does not allow access to USB or Serial ports plus it ate up all my hard drive space on my Linux partition and even after uninstalling VirtualBox it did not remove it's files so I had to manually delete all it's files after useing Disk usage analyzer to find all of it's files.

QUOTE=bodhi.zazen;9359711]Most people use virtualization.

I suggest you look at VirtualBox

And yes, there is a bit of a learning curve with virtualization, but it works better / easier then wine, IMHO.[/QUOTE]

---

### Post by T-rock007 on 2010-06-04
You can try Cedega or Crossover.I've heard that Cedega is the best but you have to pay for them, where wine is free.

---

### Post by dino99 on 2010-06-04
wine is the better choice i've never used

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by bodhi.zazen on 2010-06-04
> **daldude said:**
> I tried  VirtualBox and removed it because it does allow Windows access to your other partitions that are formatted in NTFS or FAT and does not allow access to USB or Serial ports plus it ate up all my hard drive space on my Linux partition and even after uninstalling VirtualBox it did not remove it's files so I had to manually delete all it's files after useing Disk usage analyzer to find all of it's files.

QUOTE=bodhi.zazen;9359711]Most people use virtualization.

I suggest you look at VirtualBox

And yes, there is a bit of a learning curve with virtualization, but it works better / easier then wine, IMHO.[/QUOTE]

That does not sound right at all.

First Virtualbox will use USB devices, you need the PUEL version (download from the sun Viertualbox web site).

I do not know how your Windows guest was able to access your FAT or NTFS partitions (unless you specifically configured it to do so via shared directories).

And stating that the application takes up your HD space is just inaccurate. Yes you need to assign HD space to the guests.

With that said, you may do better with wine as it has less over head, especially with a Window guest, but wine will take some time to learn.

If you want to use wine, you need to use the Wine web page, specifically the AppDB

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Fine your application(s) on the list and follow the instructions. Wine tends to be a bit unstable, termed "regression", so you often need to use specific version of wine for specific applications. Simple applications (utorrent) are easy to use with wine, large and complex applications are more complicated and buggy (games).

---

