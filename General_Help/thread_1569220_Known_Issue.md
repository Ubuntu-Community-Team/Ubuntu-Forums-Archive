---
title: "Known Issue??"
date: 2010-09-06
forum: General Help
---

### Post by Lolpanda on 2010-09-06
Possible bug I found with jockey., just wanted to get some people's opinions before I made a  bigger deal out of it.

Went to install the 10.04.1 last night and today, every time I would go to install the hardware drivers, they'd install fine, reboot, my screen would be, for lack of a better word, mangled and distorted to the point I'd drop back to a CL with shift-alt-f1 just to do ANYTHING

At first I thought it was just a random install bug, so I went back, forced my way through screen and had jockey uninstall the drivers. Rebooted, everything is fine. Go to reinstall them, reboot, same issue comes back. This happened across multiple ISO's (32bit 10.04.1 downloaded from the ubuntu site), multiple OS installs (CD and USB source) and multiple driver-installs (All through jockey) , over and over and over. 

Finally, it turned out that jockey wasnt correctly blacklisting the "radeon" and "radeonhd" modules under /etc/modprobe.d/blacklist after installing the fglrx drivers, and this lead to the system fighting between the two drivers whenever it drew something, causing tears, distortions and other visually ugly things.


I can understand why jockey wouldnt add them, incase the user would want to fall b ack to the open-source drivers, this would create an issue of searching through the file and deleting the correct lines.

But something should be done by the dev's for 10.10 to ensure this cannot happen. The easiest way would be to add 2 commands after jockey finishes the install that would only have to be

echo blacklist radeon >> /etc/modprobe.d/blacklist
echo blacklist radeonhd >> /etc/modprobe.d/blacklist

that would prevent the radeon* drivers from loading and causing the problems I had, though as I said it would create a small problem of 'what if the user would remove fglrx'


If this is a new bug, or a confirmation of an old one, I'd love it if someone with a launchpad account would submit/confirm this bug up there, as I do not and havent used launchpad before

---

### Post by Lolpanda on 2010-09-06
Right then, this has officially gone from a bug report to a help request as blacklisting only worked for one reboot, then the next time I brought the system back up, the graphically problems were back. (Screenshot attached) I really dont know where to start on this one. Apparently it wasnt the conflicting drivers that were the cause of this, and if they are, then the kernel isnt correctly reading the blacklist file which is an entirely different issue.

---

