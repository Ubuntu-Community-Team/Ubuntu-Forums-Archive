---
title: "Unable to reinstall cupsys"
date: 2009-07-07
forum: General Help
---

### Post by Agent Smith on 2009-07-07
Hello. I have been unable to get my printer working after some updates. I uninstalled the cups files from synaptic, and thought i would reinstall them.
This is what i get when i try:

jonathan@laptop:~$ sudo apt-get install cupsys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cupsys is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up cupsys (1.3.7-1ubuntu3.5) ...
chown: invalid group: `root:lp'
dpkg: error processing cupsys (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)

Any help would be appreciated. Jon

---

### Post by washakie on 2009-07-07
Do you have karmic listed at all as a repository in your /etc/apt/sources.list file?

If you're running jaunty, I highly discourage using the karmic sources... I've done it, and I'm pretty screwed this days it seems...

---

### Post by washakie on 2009-07-07
Not sure what your troubles are, but eventually it seems I was able to solve mine by removing any reference to cups, including cupsys, cups ANYTHING... from:

/etc/init.d/
/etc/rc2.d/
/var/cache/apt/archives/

also, it seems running aptitude just directly works quite well, though it is a little hard to get used to initially. Just type:

sudo aptitude -u

And you'll get into the textual interface to the program. It seemed to work better for me.

---

### Post by Agent Smith on 2009-07-07
I have fixed it by adding lp as a group in users and groups. I then reinstalled cupsys and it was ok.

---

