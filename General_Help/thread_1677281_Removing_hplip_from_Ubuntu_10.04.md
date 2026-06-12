---
title: "Removing hplip from Ubuntu 10.04"
date: 2011-01-28
forum: General Help
---

### Post by Quarkrad on 2011-01-28
I would like to upgrade my current hp printer driver 3.10.9 to the latest version 3.11.1  According to 'Google' the command to remove the driver is **sudo apt-get remove hplip** but when I type this in terminal I get:
[B]
liz@lizubuntu:~$ sudo apt-get remove hplip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package hplip is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.[/B]

I'm a newbie so this is odd to me - I installed 3.10.9 as per the Launchpad website - it looks like Ubuntu is not 'seeing' hplip although it is installed and working.  I guess I need a more subtle command to get rid of all the hp driver files.  Or could I just install 3.11.1 over the top? (Would have thought best to remove 3.10.9 first).

---

### Post by Quarkrad on 2011-02-02
Install of 3.11.1 package removes old version.

---

