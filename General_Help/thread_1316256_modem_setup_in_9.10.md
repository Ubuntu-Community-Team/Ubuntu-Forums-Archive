---
title: "modem setup in 9.10"
date: 2009-11-05
forum: General Help
---

### Post by AlP36 on 2009-11-05
I have been using Ubuntu 6.06LTS for over 2 1/2 years and have been pleased with it. Then I tried to install a newer version (clean install on different disk) - bad news. I loaded 9.04 first, it crashed on a random schedule requiring a cold boot each time. It also did this with the live CD. So I reformatted the disk (gparted) and installed 8.04LTS from a Ubuntu live cd. It refused to let me sudo into root and the modem dialed out before I logged in, so I decided to reinstall and since 9.10 was out by this time I used it. I downloaded the ISO file on another computer with high speed connect. Now I find that 9.10 does not support dialup modems. What is with these people??? Surely I am not the only poor soul in the world who still has dialup?? I went to the official doc on modem setup and found this little jewel:
"NetworkManager doesn't currently support modem connections, so you will need to install the gnome-network-admin package. If you have no working Internet connection, then you will need to obtain this package and install it, see Downloading and installing a .deb package for more information."
I looked on the installation cd and it did not include the gnome-network-admin package. there was a network-manager-gnome package but I think this is what screwed up my modem in 8.04. I have used pppconfig but now I get the message that I must be in the 'dip' group. If anybody is listening maybe you could supply me with better info, otherwise I will search until I get the thing working, BUT this is the reason most people will avoid Linux and keep M-s.
I also do not have any sound altho I had it in 6.06.

---

### Post by SanoTwo on 2009-11-07
grrrrr.

Me too, sort of.

George Vita addresses the problem here, [http://ubuntuforums.org/showthread.php?p=7245790#post7245790](http://ubuntuforums.org/showthread.php?p=7245790#post7245790)  but #2#3#4 links are useless.

From your info I may revert to 9.04. _sigh_

---

