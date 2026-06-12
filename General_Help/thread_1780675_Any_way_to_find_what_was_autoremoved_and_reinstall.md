---
title: "Any way to find what was autoremoved and reinstall?"
date: 2011-06-12
forum: General Help
---

### Post by Bucky Ball on 2011-06-12
Hi all,

Is there any way to find out what packages were removed by the last 'sudo apt-get autoremove' command? Is that info in a log somewhere?

I am setting up a recently installed minimal install and my last autoremove seemed to remove some dependencies which has in turn killed my network connections, wired and wireless. 

All ideas welcome ... ;)

---

### Post by coffeecat on 2011-06-12
Open the log file viewer - or it might be called System Log Viewer in Maverick - and look near the end of the dpkg.log. In Maverick, iirc, Log File Viewer is under System > Administration.

---

### Post by Bucky Ball on 2011-06-12
Sorry, this is a 10.04 LTS minimal install on another partition to the 10.10. ;)

I'll have a look at that log file. I reinstalled the older driver for my wireless and got the network configuration back to pretty much how it was and wireless seems to be working again but not wired. That's fine. Setting up my network via the terminal without a network manager so it's a bit of a learning curve but having fun with it! 

Thanks for your tip. ;)

* UPDATE: Yea, that file (/var/log/dpkg.log) seems to be where the autoremove info would be but all logging to that file stops at 16:51 and it is now 00:10, seven hours later. I can see things there I installed but nothing that specifically says 'autoremove' or uninstalling of anything.

---

