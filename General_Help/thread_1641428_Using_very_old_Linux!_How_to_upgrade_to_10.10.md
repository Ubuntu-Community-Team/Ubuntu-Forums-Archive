---
title: "Using very old Linux! How to upgrade to 10.10?"
date: 2010-12-09
forum: General Help
---

### Post by DeathByLinux on 2010-12-09
Hey guys, I just posted something stupid a second ago, but it seems I need to figure out how to upgrade to 10.10. 
Background.
I am using 9.10 and in the Update Manager, I only see the option to upgrade to 10.04. I wanna upgrade to 10.10. 
Is there a terminal command for this? If someone could tell me that would be swell. :)
-DeathByLinux

---

### Post by kainalu on 2010-12-09
This page explains the procedure for that :


[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by DeathByLinux on 2010-12-09
None of them really say how I can go from 9.10 to 10.10. I found this thread:
[http://ubuntuforums.org/showthread.php?t=1628494](http://ubuntuforums.org/showthread.php?t=1628494)
I am guessing this guy just went from 9.10 to 10.04 and then to 10.10. I just think that's so weird. You'd think I'd be able to just jump from 9.10 to 10.10, but I may just not know how the upgrades work.
Should I go ahead and start doing it that lengthy way, or is there something I missed?

---

### Post by sikander3786 on 2010-12-09
No direct path from 9.10 > 10.10. You need to upgrade step-by-step from 9.10 > 10.04 > 10.10.

Only LTS releases can be upgraded directly with skipping releases in between i.e, 8.04 > 10.04.

---

### Post by DeathByLinux on 2010-12-09
Okay... fine... :(
I'll mark this as solved after I am done.
Gonna start now.

---

### Post by Sef on 2010-12-09
If you upgraded directly from 9.10 to 10.10, it would render your system useless.

---

### Post by DeathByLinux on 2010-12-09
Okay, so I am on 10.04 now and Upgrade Manager doesn't seem to give me the button to upgrade to 10.10. Do I have to do it manually, then?

---

### Post by Ibidem on 2010-12-10
I suspect that 10.04 defaults to setting "Show new distribution releases" to "LTS releases only".
Click Settings and check what that says.
Ibidem

---

### Post by DeathByLinux on 2010-12-10
So, in the settings, under the "Updates" tab in the Release upgrade  heading it says, "Show new distribution releases: [Long term support  releases only]". The other selections are "Normal releases" and "Never".  
I just changed it to "Normal releases" and it worked. 
My thanks to: Ibidem, Sef, Sikander and Kainalu for all your help. 
-DeathByLinux

---

