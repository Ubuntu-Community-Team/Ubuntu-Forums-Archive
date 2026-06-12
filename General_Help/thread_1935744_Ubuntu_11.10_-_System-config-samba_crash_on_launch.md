---
title: "Ubuntu 11.10 - System-config-samba crash on launch..."
date: 2012-03-04
forum: General Help
---

### Post by Roasted on 2012-03-04
I'm running 11.10 on four different machines, however one in particular is giving me trouble with the system-config-samba package to manage my samba shares. It just flat out doesn't work... I launch it, put in my password, and nothing else happens whatsoever. I checked syslog but there's nothing in there to suggest what's up. In fact, while tailing syslog, nothing is populated when the issue occurs. Is there a different log file I should be checking?

---

### Post by Roasted on 2012-03-05
Looks like I got it working with the help of this thread:

[http://ubuntuforums.org/showthread.php?t=1869247&highlight=samba+gui](http://ubuntuforums.org/showthread.php?t=1869247&highlight=samba+gui)

Can anybody tell me what exactly pyNeighborhood does and why I needed it for the Samba GUI to be utilized?

---

### Post by Roasted on 2012-03-05
Here's some confusion:

Laptop - Ubuntu 11.10 - pyNeighborhood is NOT installed, yet the system-config-samba GUI works fine.

HTPC - Ubuntu 11.10 - pyNeighborhood IS installed, system-config-samba GUI Works fine. However, prior to installing pyNeighborhood, system-config-samba GUI did not launch.


Eh???

EDIT - so I just went to the HTPC and removed pyNeighborhood. I also noticed in the terminal output there were some dependencies that apt-get autoremove would take care of, one being smbfs. I thought I remember smbfs being antiquated but I ran apt-get autoremove anyway for kicks. To my surprise, system-config-samba worked fine. Okay, okay... But let's reboot! That will cause it to not work like before - right? Wrong. I rebooted after running apt-get autoremove, etc., and it worked fine. I checked Synaptic and pyNeighborhood was NOT installed.

So now, it looks like things are good and no pyNeighborhood is existent on this system, just like the other systems. But I still have to wonder, what in the world happened at first then??

---

