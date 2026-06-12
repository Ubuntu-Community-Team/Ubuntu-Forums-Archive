---
title: "Can you explain these error msgs?"
date: 2010-04-23
forum: General Help
---

### Post by JEBB on 2010-04-23
I tried to add some fonts and now get the error messages below when running software update.  Can you tell me what they mean and how to fix the problems?  Thanks.

----------------------------------------------------------------------
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)/dists/jaunty/multiverse/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom://Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Some index files failed to download, they have been ignored, or old ones used instead.

--------------------------------------------------------------

E: ttf-mscorefonts-installer: subprocess post-installation script returned error exit status 1

E: msttcorefonts: dependency problems - leaving unconfigured

---

### Post by byStanderone on 2010-04-23
...seems the update/install was not successful, try a sudo apt-get autoclean, if the problem does not corrects itself...try a sudo apt-get clean...

---

### Post by Irony on 2010-04-23
Go to Synaptic > Settings > Repositories and untick the cdrom option.

Then hit reload (the big blue circular symbol)...

---

### Post by JEBB on 2010-04-23
Irony's suggestion worked.  Thanks!!

---

