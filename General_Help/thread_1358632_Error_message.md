---
title: "Error message"
date: 2009-12-18
forum: General Help
---

### Post by ubuntu1 on 2009-12-18
I'm getting the following error message and I can't seem to sort it out. Can you help?

E: /var/cache/apt/archives/python2.6-minimal_2.6.4-0ubuntu3_i386.deb: subprocess dpkg-deb --control returned error exit status 2

---

### Post by internalkernel on 2009-12-18
It means the package you are installing... python2.6-minimal_2.6.4-0ubuntu3_i386.deb is throwing an error. Sorry, for the captain obvious part... 

What are you trying to do? install or uninstall, what's the command that is causing the error? 

Try opening a terminal and typing: 
```
sudo apt-get install python2.6-minimal 
```

maybe that error will be a little more clear...

---

### Post by ubuntu1 on 2009-12-19
Its running synaptics thats caused the problem, the pc locked up during the upgrade process.

---

### Post by ubuntu1 on 2009-12-19
Heres the output -

Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 libdns50 libnspr4-dev
  linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  python2.6-minimal
1 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.
2 not fully installed or removed.
Need to get 0B/1,348kB of archives.
After this operation, 0B of additional disk space will be used.
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/python2.6-minimal_2.6.4-0ubuntu3_i386.deb
debconf: apt-extracttemplates failed: Bad file descriptor
dpkg-deb: `/var/cache/apt/archives/python2.6-minimal_2.6.4-0ubuntu3_i386.deb' is not a debian format archive
dpkg: error processing /var/cache/apt/archives/python2.6-minimal_2.6.4-0ubuntu3_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/python2.6-minimal_2.6.4-0ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by internalkernel on 2009-12-19
Your pc locked up during an upgrade? 

Open Synaptic package manager: System --> Administration --> Synaptic, then click on Settings --> Preferences and the Files tab. Click on "Delete Cached Package Files"

Then Reload and Mark all Upgrades, Apply. 

Then you can search for that python package in synaptic again and re-install/install...

I think that particular package was probably corrupted in the download, but it still exists in the local archive so when you try to install it, it doesn't get downloaded - apt tried to install the local package and hence the error. We'll see if this gets us any farther... 

~~
I would have responded sooner but we lost power in a snow storm last night...

---

