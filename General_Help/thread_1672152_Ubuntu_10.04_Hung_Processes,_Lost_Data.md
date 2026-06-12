---
title: "Ubuntu 10.04 Hung Processes, Lost Data"
date: 2011-01-20
forum: General Help
---

### Post by Chernevik on 2011-01-20
Today Ubuntu (10.04) began running several processes quite slowly.  First one terminal window, running vi, hung.  Then Chrome started taking forever to process some (but not all) sites, frequently reaching the 'not responding kill / wait?' dialog.  Then an upgrade (for sudo) began taking forever.  Then _several_ vi terminal windows hung.  Running 'ls' in a new terminal window hung.

I tried killing the vi jobs, no luck, closed the terminal windows.  They still appeared in the System Monitor.  I killed the Synaptic package upgrade. 

I then rebooted.  This seemed to hang.  Pressing escape got the message 'searching (waiting?) for unattended upgrades'.  I killed the power and restarted.

The data in the vi windows, and a number of files saved in the same directory earlier in the day, were gone.  No swap files, nothing.

The data loss here is only a few hours' work, as I back up a lot.  Still, this is alarming.

I've also been getting complaints from the package manager that a number of repositories are out of date.  

Any ideas?  Have I been hacked?

---

