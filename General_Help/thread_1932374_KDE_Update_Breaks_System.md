---
title: "KDE Update Breaks System"
date: 2012-02-27
forum: General Help
---

### Post by sdewittofm on 2012-02-27
Had a weird problem yesterday when I tried to update my system through the Muon Package Manager.  It tried to install a bunch of kde 4.8 updates and ended up uninstalling plasma-desktop.  As near as I could figure out the problem was unmet dependencies and was fixed by enabling the kubuntu backports ppa and running a dist-upgrade.  Not sure what is going on here, but I wanted to share the problem and solution in case anyone else runs into a similar problem.  

Also, if you have plasma-widget-icon-tasks installed from the gnumdk ppa it will break the update to KDE 4.8.  Bug report and solution to the problem can be found here, [https://bugs.launchpad.net/kubuntu-ppa/+bug/913080](https://bugs.launchpad.net/kubuntu-ppa/+bug/913080)

---

### Post by nortexoid on 2012-12-05
This bug has been around for AGES. I've been using a Mac primarily but I still use Kubuntu on an old system. I just tried upgrading that system yesterday from 12.04 to 12.10 and it removed critical packages without reinstalling them. This happened to me with something like Kubuntu 10! This is almost a reason to switch to a different distro.

---

