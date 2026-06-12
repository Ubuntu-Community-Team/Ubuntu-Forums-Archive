---
title: "nVidia / TwinView crashes"
date: 2011-09-02
forum: General Help
---

### Post by Kentucky88 on 2011-09-02
A long time ago, I would boot my computer, it would start loading Ubuntu 11.04, then right after the purple screen, screen would go blank, hard drive would be running, but simply no display.  I would have to reboot and after a few tries, I would successfully boot into Ubuntu.  It did this for a few days, then went away.  Last night, it came back.  I have tried several things including uninstalling / reinstalling the nVidia drivers.  Now I can successfully boot into Ubuntu most of the time, but when I try to activate my second monitor through TwinView, the the display goes blank and there's nothing else I can do besides restart the system.  After doing this several times, I think my Ubuntu installation is screwed up.  I can boot fine into Ubuntu Recovery Mode / Low Graphics Config, but this TwinView issue is driving me nuts.  How to I completely reinstall all X-Org and Nvidia packages?  I basically want to do a repair install without having to track down every damn file on my computer that is important to me and saving it to disk.  I have the important stuff backed up on two flash drives and one hard drive, but I really don't want to wipe the HDD clear and reinstall.  There must be a smarter way.  Anyone?

Edit: Extra notes - I already deleted /etc/X11/xorg.conf before and after reinstalling nvidia drivers.  My HDD / Ubuntu desktop used to run in a different computer that ran on Intel integrated graphics...I sure miss those Intel integrated graphics...those open source drivers were so much more reliable.

---

### Post by apos on 2011-09-09
Could you please commit your problem to:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/813343](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/813343)

---

