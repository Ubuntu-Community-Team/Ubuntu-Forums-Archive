---
title: "HW Support"
date: 2012-10-04
forum: General Help
---

### Post by ferronica on 2012-10-04
Need help regarding installation of Ubuntu 12.04 64bit, my system HW list below Compatible or not.

AMD
Gigabyte GA-MA790GP-DS4H
Processor Phenom X4 9950 Black Edition Revision DR-B3
RAM DDR2 4GB Corsair
SSD OCZ Agility 3 60GB

---

### Post by ajgreeny on 2012-10-04
You have actually shown the parts of the system that have the least probability of difficulties with a linux OS.  The more important bits as far as most Linux OS compatibility is concerned are the graphic card and, if there is one, the wireless adapter card.

---

### Post by ferronica on 2012-10-04
> **ajgreeny said:**
> You have actually shown the parts of the system that have the least probability of difficulties with a linux OS.  The more important bits as far as most Linux OS compatibility is concerned are the graphic card and, if there is one, the wireless adapter card.
You mean my Hardware fully compatible with ubuntu 12.04 64BIT. i'm not going to use any Graphic card and WireLess LAN Card.

In this Board ATI Radeon HD 3300

---

### Post by ajgreeny on 2012-10-04
OK, I think that card is fully supported by the ATI/radeon open source driver; it certainly is listed in [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by ferronica on 2012-10-04
Thanks for quick reply will install and let you know, One more question what i heard SSD performance Drops after some days when SSD get 30% Full is that TRUE?

---

### Post by windscape on 2012-10-04
Hi,

SSDs do have a tendency to get slower over time as they fill with data. Modern SSDs and the Ubuntu kernel support the TRIM command that can help combat this. TRIM support needs to be manually enabled after installing Ubuntu by modifying the mount parameters of the partitions on the SSD to include the discard option. The page here: [http://askubuntu.com/questions/18903/how-to-enable-trim]("http://askubuntu.com/questions/18903/how-to-enable-trim") describes how to enable TRIM support in Ubuntu.

---

### Post by ferronica on 2012-10-04
Ok then no issue from SSD because installing on OCZ Agility 3 60 GB SSD (AGT3-25SAT3-60G)

---

### Post by Mark Phelps on 2012-10-04
Rather than FORCE the installation, you would do better booting from an Ubuntu LiveCD/LiveUSB and selecting the Try Ubuntu mode.

Once you get to a desktop, you can then see how well Ubuntu detected your hardware and installed all the proper drivers.

This way, if something did not work, you have a chance to find resolutions to that before you force and install and end up with a nonworking system.

---

