---
title: "Uninstalling forced architechture deb packages"
date: 2011-09-15
forum: General Help
---

### Post by promet on 2011-09-15
Hello,

I have been using some force-installed i386 packages, and would like to uninstall them and use some corresponding 64bit debs that I've got. 

I've tried uninstalling them with the Ubuntu Software Center, Synaptic, Aptitude, Gdebi, etc., none of which seem to be able to recognize or locate the packages, though, when trying to install the 64bit packages, I get the following:

```

sudo dpkg -i nxclient_3.5.0-7_amd64.deb
 
dpkg: error processing nxclient_3.5.0-7_amd64.deb (--install):
 nxclient: 3.5.0-7 (Multi-Arch: no) is not co-installable with nxclient:i386 3.4.0-7 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 nxclient_3.5.0-7_amd64.deb

```Anyone have any ideas how I could locate, and eradicate this "phantom" package?

Thanks!

---

### Post by thingdeux on 2011-11-04
Spent an annoyingly large amount of time figuring this out:

Had to have DPKG  purge the phantom files, for some reason even though the application is removed the DPKG database still maintains the entries.

This command fixed it for me.

dpkg -P nxclient:i386

Enjoy!

---

