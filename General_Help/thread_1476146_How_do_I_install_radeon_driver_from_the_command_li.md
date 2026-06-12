---
title: "How do I install radeon driver from the command line?"
date: 2010-05-07
forum: General Help
---

### Post by ubudillo on 2010-05-07
Hello forums, I got given an old (non brand name) laptop and have installed XP and kubuntu 10.04 on it. The graphics card is Radeon Mobility X1600. Kubuntu gets a very strange problem which does not happen in XP:

Although the installation graphics are OK (sort of, there are some strange font irregularities), when it tries to reboot and fire up the graphics all hell breaks loose, the display is broken in two parts and shifted up with the overflowing region coming up from below. I 'm guessing something in the X server is trying to start and failing because when I try to drop to a text terminal (Ctrl-Alt-F<something or other>) I get pages filling up with error messages.

Unfortunately I can't remember what the messages say and I don't want to try to recreate it in a hurry because after this happens, subsequent reboots start the computer in this split screen mode (weirdly omitting the BIOS POST message) and I 'm not sure how to get it fixed, so far removing the battery, reseting the BIOS to default and letting it cool down seem to work, eventually.

Anyway, I figured since XP seems to be fine, it must be a software problem, although I 'm mystified how it persists and jumps between reboots (the split screen persists even all the way to the BIOS menu). I tried getting the driver from the ATI site:

ati-driver-installer-9-3-x86.x86_64.run

and running it but it fails like so:

```
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
ESC[31m ATI Technologies Linux Driver Installer/Packager ESC[0m
==================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib::none:2.6.32-21-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.i3fXeb
```

So, if I can't run the ATI driver, my other option is to run whatever it is that the "Hardware Drivers" KDE menu item runs to get it to sniff out the driver I need. But I can't start an X server so I need to either run whatever it is that runs behind it or get the package I need through apt-get? Any help?

---

### Post by ubudillo on 2010-05-09
Not really solved by bypassed by wiping out lucid and installing karmic. So far so good.

---

