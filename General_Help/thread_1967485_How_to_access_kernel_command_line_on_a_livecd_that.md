---
title: "How to access kernel command line on a livecd that won't load?"
date: 2012-04-28
forum: General Help
---

### Post by Flame_Phoenix on 2012-04-28
Hello gentleman. 
A few days ago I recognized that windows XP was too heavy for my machine, so i decided to install one of the many different versions of Ubuntu (which one doesn't matter, the problem is global). 
after a whole night of search and asking for help I concluded that the problem was in proprietary firmware - b43 firmware to be more specific - and that to fix this I have to access the kernel's command line and blacklist the driver b43 that I actually need. 

Once the b43 driver is blacklisted, I can proceed with loading the LiveCD knowing that it will no longer freeze, and using an Ethernet cable I will be able to update the Ubuntu software and to download the wireless adapter driver later.

However, after searching (again) I found no ways of accessing the kernel's command line while using the LiveCD and without the OS being loaded (the only thing I can see is the "Try without installing" menu ... I can press "Esc" to access a command line, but that really doesn't help).

Is there a way of making this possible?

There is however, another solution: to manually change Ubunut's livecd to include the b43-firmware driver. However I have no idea on how to do this. 
Can someone help me?

For further information about this problem refer to this link:
[http://ubuntuforums.org/showthread.php?t=1967054](http://ubuntuforums.org/showthread.php?t=1967054)

---

### Post by MorrisseyJ on 2012-04-28
This is answered in post #6 here: [http://ubuntuforums.org/showthread.php?t=1966631](http://ubuntuforums.org/showthread.php?t=1966631)

---

### Post by Flame_Phoenix on 2012-04-28
Lol, I actually missed that one ... Guess I should have seen if someone had replied before posting this xD

---

