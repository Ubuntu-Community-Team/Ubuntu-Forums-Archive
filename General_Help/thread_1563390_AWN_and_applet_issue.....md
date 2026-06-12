---
title: "AWN and applet issue...."
date: 2010-08-29
forum: General Help
---

### Post by juil on 2010-08-29
I installed AWN a while back. Didn't use it for several months and started using it again. TWO issues

**1**)I added the below to the /etc/apt/sources.list
#FILE: /etc/apt/sources.list
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) lucid main

then, in the terminal
$ sudo apt-get update
$ sudo apt-get install awn-core-applets-bzr

unfortunately it gave me this message:
Failed to fetch [http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

**2**)While investigating this problem, i ran into a topic by reacocard on how to install the applets in this link: [http://ubuntuforums.org/showthread.php?t=762363](http://ubuntuforums.org/showthread.php?t=762363)
The terminal instruction was:

$sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

The weird thing is that software centre says that AWN is installed but synaptic shows that the 3 packages above is NOT installed (white box).

Can someone help me out?

---

### Post by sikander3786 on 2010-08-29
I think there are some unmet dependencies. To fix these type in terminal

***sudo apt-get install -f***

Also check for any broken packages in synaptic by using "Broken" filter.

---

### Post by juil on 2010-08-29
How can i tell if they are broken packages? I did the filter option and there's a list of packages shown that are and are not installed in the right window...

---

### Post by sikander3786 on 2010-08-29
Go to Synaptic Package Manager >>> Custom Filters >>> Broken and see if any packages are listed there. Alternatively try reconfiguring dpkg in terminal

***sudo dpkg --configure -a***

---

### Post by juil on 2010-08-30
Oh, haha i see it. Ok that was simple.
And no I don't have any broken packages.
Maybe I should uninstall and reinstall again?

---

### Post by sikander3786 on 2010-08-31
Have you tried uninstalling and reinstalling? Solved?

---

