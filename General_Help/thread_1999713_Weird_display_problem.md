---
title: "Weird display problem"
date: 2012-06-08
forum: General Help
---

### Post by IanSammel on 2012-06-08
Since I updated to Precise I have problems with the display blanking.  The reason appears to be that dpms is enabled.  It is turned off in the system settings and disabled when I log on but gets enabled from time to time.  I can turn it off again with xset -dpms but after a while that gets annoying.

One sure way I have found to duplicate the problem is to perform a sofware update.  The last time an update was necessary I monitored the dpms state as the update progressed.  It stayed off until I had to enter the administrator password.  As soon as I entered the password and pressed enter, dpms was enabled.  I'm now at a loss as to how to proceed.  Does anyone have any suggestions please?  KDE version 4.8.3.
Thanks

---

### Post by Chris Musampa on 2012-06-08
Maybe something to try here
[http://www.kubuntuforums.net/showthread.php?58993-DPMS-Turns-Itself-On/page2](http://www.kubuntuforums.net/showthread.php?58993-DPMS-Turns-Itself-On/page2)

---

### Post by IanSammel on 2012-06-09
I already found that thread, but it didn't seem to correspond to my problem.  In my case it's completely reproducible.  When I enter the administrator password whilst doing a software update dpms becomes activated.  I can turn it off again with xset.  I wondered if anyone could suggest why that should happen.  However I'll add a post on the kubuntu thread as well.

---

