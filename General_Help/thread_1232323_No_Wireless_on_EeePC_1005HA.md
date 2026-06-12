---
title: "No Wireless on EeePC 1005HA"
date: 2009-08-05
forum: General Help
---

### Post by GreyArea2 on 2009-08-05
Just bought an EeePC 1005HA yesterday. Ubuntu does not recognize the wireless card.

I already tried the following: 
[http://ubuntuforums.org/showpost.php?p=7525735&postcount=2](http://ubuntuforums.org/showpost.php?p=7525735&postcount=2) 
and 
[http://ubuntuforums.org/showthread.php?t=1219931&highlight=unclaimed](http://ubuntuforums.org/showthread.php?t=1219931&highlight=unclaimed)

Wired ethernet does work, but no wireless. Since I obviously have a different problem, I decided to make my own thread. 

Please help. Thank you.

---

### Post by GreyArea2 on 2009-08-05
Just tried this:
[http://ubuntuforums.org/showpost.php?p=7718408&postcount=17](http://ubuntuforums.org/showpost.php?p=7718408&postcount=17)

Does not work. 

Anyone?

---

### Post by MichealH on 2009-08-05
Have you tried Madwifi-drivers that work with unsupported card :D

---

### Post by GreyArea2 on 2009-08-05
Thank you! That seemed to do it.

For the record, the necessary driver can be found here: [http://packages.ubuntu.com/jaunty/i386/madwifi-tools/download](http://packages.ubuntu.com/jaunty/i386/madwifi-tools/download)

Download, install the .deb, restart the netbook, and it works.

As a side note, Karmic alpha 3, running from a flash drive, recognizes the wireless with no trouble.

Thanks again!

---

### Post by jackal242 on 2009-09-02
I downloaded the madwifi tools package from the link above, installed it on the EEEPC 1005HA, and rebooted.

Absolutely nothing changed.

Still no wireless OR ethernet.

I installed Ubuntu for desktop 9.04....

---

### Post by ubuntnoob on 2009-11-07
I have the same netbook (1005HA).  Installed Ubuntu Netbook Remix and wifi works great out of the box.

---

