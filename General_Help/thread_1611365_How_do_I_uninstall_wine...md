---
title: "How do I uninstall wine..?"
date: 2010-11-01
forum: General Help
---

### Post by Omnomnom on 2010-11-01
How do I uninstall wine?

I did sudo apt-get purge wine, it said it isn't installed but in the Applications menu it says that it is still there. Even though I removed it and purged it.

---

### Post by HiImTye on 2010-11-01
try
```
rm -R ~/*.wine*
```
that aught to delete any prefixes that are remaining and the menus should disappear

---

### Post by LJD on 2010-11-22
I have the same problem. The purge command worked, but Wine is still there in apps. I ran the code above and got this back: 

lou@ubuntu:~$ sudo apt-get purge wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lib32bz2-1.0 lib32ncurses5 ia32-libs wine1.2 linux-headers-2.6.32-24-generic
  libc6-i386 lib32gcc1 lib32asound2 lib32nss-mdns linux-headers-2.6.32-24
  ttf-symbol-replacement wine1.2-gecko cabextract ttf-mscorefonts-installer
  lib32z1 lib32stdc++6 winbind lib32v4l-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lou@ubuntu:~$ rm -R ~/*.wine
rm: cannot remove `/home/lou/*.wine': No such file or directory
lou@ubuntu:~$


Trying autoremove gives me this:

lou@ubuntu:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
lou@ubuntu:~$


Am I root?:confused:

---

