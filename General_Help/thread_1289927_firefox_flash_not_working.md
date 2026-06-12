---
title: "firefox flash not working"
date: 2009-10-12
forum: General Help
---

### Post by bd41 on 2009-10-12
sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1768B of archives.
After this operation, 41.0kB of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 122534 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.32.18ubuntu0.9.04.1_amd64.deb) ...
Setting up flashplugin-installer (10.0.32.18ubuntu0.9.04.1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing flashplugin-installer (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on flashplugin-installer; however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 flashplugin-installer
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Kareeser on 2009-10-13
Have you closed synaptic?

---

### Post by dyingsun on 2009-10-13
Also, have you restarted Firefox?

I personally had no end of trouble with the nonfree plugin. Can I suggest doing it this way?

[_Install and run 64 bit Flash on Linux_]("http://usefulsoftwaregamesandknowledge.blogspot.com/2009/09/install-and-run-64-bit-flash-on-linux.html")

That's the easiest way, IMO. Just make sure you follow the instructions, especially those first ones about purging the old plugin!

After the install, close and reopen Firefox, and test it out on Youtube, or wherever.

---

