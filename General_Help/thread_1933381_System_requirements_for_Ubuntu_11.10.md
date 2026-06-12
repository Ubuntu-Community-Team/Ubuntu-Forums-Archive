---
title: "System requirements for Ubuntu 11.10"
date: 2012-02-29
forum: General Help
---

### Post by viktorjano on 2012-02-29
I would like to know what are the system requirements for (Ed)Ubuntu 11.10!

The systems that I have are CPU: Pentium 4 3.4GHz, RAM DDRII 2GB, HDD 80GB! And how can I install driver for graphic card on Linux machine?

One more thing... which is the best way for partitioning the hard drive? Since in the process of installation there's one stop where one chooses how to partition the drive. I usually choose entire drive in one partition, but still I would like to know if it is better to have it partitioned some other way.  For example like in windows (C partition and D partition).

Ok , thanks in advance!

---

### Post by winh8r on 2012-02-29
You can check through the documentation/release notes for 11.10 here:

[https://help.ubuntu.com/11.10/installation-guide/i386/hardware-req.html]("https://help.ubuntu.com/11.10/installation-guide/i386/hardware-req.html")

Any questions that you still have after that, just ask!

Hope this helps you.

---

### Post by howefield on 2012-02-29
Try this page for installing Edubuntu, you'll find minimum hardware requirements, your specs should run Edubuntu admirably :)

[http://edubuntu.org/documentation/10.10/installation-guide](http://edubuntu.org/documentation/10.10/installation-guide)

Nothing wrong in using the whole drive as you have done previously, but it can be useful to separate out your home folder, basically meaning 3 partitions, one for /, one for /home and one for /swap.

You can create them before hand or use the installer partitioner.

Installing drivers for your graphics card depends on the make/model of the card, you should be up and running out of the box but there may be proprietary drivers available for you after installation of the OS.

---

### Post by chait on 2012-02-29
Hi,
  Please check this link: [https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#System_Requirements](https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#System_Requirements)

Cheers.:popcorn:

---

### Post by Mark Phelps on 2012-02-29
> **viktorjano said:**
> ... And how can I install driver for graphic card on Linux machine?

It's not only unlikely that you will have to manually install graphics drivers, it's possible that the default drivers that will get installed as part of the setup will be the only working drivers.

AMD (and to a lesser degree, Nvidia) dropped restricted driver support for older video chipsets such that today, no such drivers are available.

To see what chipset you have, boot from an Ubuntu desktop CD, open a terminal, and enter "lcpsi" -- and look for the line containing "VGA".  That will tell you the make and model video chipset.  Post that info back here.

---

