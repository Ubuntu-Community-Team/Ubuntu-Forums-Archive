---
title: "Please explain this"
date: 2010-11-13
forum: General Help
---

### Post by TNT1 on 2010-11-13
```
The following packages have been kept back:
  linux-backports-modules-alsa-lucid-generic-pae 
  linux-backports-modules-headers-lucid-generic-pae 
  linux-backports-modules-wireless-lucid-generic-pae 
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

Why am I getting this? I did search the forum, and no real answer was given to others asking a similar question. 

It doesn't seem like a problem, at least for me, as my system is just peachy, but I'd still like to know why it says this.

---

### Post by TNT1 on 2010-11-15
Anyone?

---

### Post by gmargo on 2010-11-15
If you upgrade with "apt-get upgrade" or "aptitude safe-upgrade", then certain packages do not get upgraded, like kernel related packages.  Use the next level to get a complete upgrade: either "apt-get dist-upgrade" or "aptitude full-upgrade".

---

### Post by NightwishFan on 2010-11-15
It is quite possible that the package cache is just in transition, try running sudo apt-get update in a few hours and then upgrade again.

---

### Post by TNT1 on 2010-11-16
> **gmargo said:**
> If you upgrade with "apt-get upgrade" or "aptitude safe-upgrade", then certain packages do not get upgraded, like kernel related packages.  Use the next level to get a complete upgrade: either "apt-get dist-upgrade" or "aptitude full-upgrade".

Tried those, still same thing. And using update manager, it shows the three kernel images, but you can't check them.

Sorry, "full-upgrade gives me this now:
```
:~$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  linux-backports-modules-alsa-lucid-generic-pae 
  linux-backports-modules-headers-lucid-generic-pae 
  linux-backports-modules-wireless-lucid-generic-pae 
The following packages will be REMOVED:
  appmenu-gtk{u} bamfdaemon{u} indicator-appmenu{u} indicator-datetime{u} 
  libbamf0{u} libclutk-0.3-0{u} libdee-1.0-0{u} libunity-misc0{u} 
  libunity0{u} unity-asset-pool{u} unity-place-applications{u} 
  unity-place-files{u} 
3 packages upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
Need to get 12.7kB of archives. After unpacking 3,174kB will be freed.
The following packages have unmet dependencies:
  linux-backports-modules-alsa-lucid-generic-pae: Depends: linux-backports-modules-alsa-2.6.32-26-generic-pae which is a virtual package.
  linux-backports-modules-headers-lucid-generic-pae: Depends: linux-headers-lbm-2.6.32-26-generic-pae which is a virtual package.
  linux-backports-modules-wireless-lucid-generic-pae: Depends: linux-backports-modules-compat-wireless-2.6.34-2.6.32-26-generic-pae which is a virtual package.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
linux-backports-modules-alsa-lucid-generic-pae [2.6.32.25.27 (lucid-updates,
now)]
linux-backports-modules-headers-lucid-generic-pae [2.6.32.25.27 (lucid-updates,
now)]
linux-backports-modules-wireless-lucid-generic-pae [2.6.32.25.27 (lucid-updates,
now)]

Score is 260
```

And the y/n/q options.

What should I do?

---

### Post by TNT1 on 2010-11-16
Bump... What to do? y/n/q?

---

### Post by NightwishFan on 2010-11-16
No (n), if you need the backports modules. They seem like they are not available yet. Try again now. (sudo apt-get update && sudo apt-get dist-upgrade). Do you get the same message?

---

### Post by TNT1 on 2010-11-16
I went with yes, the description sounded ok, and I don't have a funky kernel or anything, so what would I need backports for?  Anyway it all seems fine...

Just this bit I don't understand:
```
Keep the following packages at their current version:
linux-backports-modules-alsa-lucid-generic-pae [2.6.32.25.27 (lucid-updates,
now)]
linux-backports-modules-headers-lucid-generic-pae [2.6.32.25.27 (lucid-updates,
now)]
linux-backports-modules-wireless-lucid-generic-pae [2.6.32.25.27 (lucid-updates,
now)]
```Cause I said yes to all of them, and uname -a gives:
```
2.6.32-26-generic-pae #46-Ubuntu SMP Tue Oct 26 18:18:31 UTC 2010 i686 GNU/Linux
```

And I went back to software sources, check and un checked the backports on updates and it doesn't come up with those three.

---

