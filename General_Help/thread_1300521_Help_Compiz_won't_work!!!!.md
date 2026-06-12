---
title: "Help Compiz won't work!!!!"
date: 2009-10-25
forum: General Help
---

### Post by Trumpet19019 on 2009-10-25
When i type compiz into the terminal i get:

Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Received a NET_CURRENT_DESKTOP message from a broken (outdated) client who sent a 0 timestamp
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x4200004 (familycomp)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.


What does this mean, and is there anyway i can fix it? or is there any way i can still run compiz?

---

### Post by lidex on 2009-10-25
Run this command instead:
```
compiz --replace
```

---

### Post by Trumpet19019 on 2009-10-25
> Run this command instead:
 	Code:
 	compiz --replace



i did that and i got this
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity

---

### Post by lidex on 2009-10-25
Google is your friend:
[http://ubuntuforums.org/showthread.php?t=962520]("http://ubuntuforums.org/showthread.php?t=962520")
[http://ubuntuforums.org/showthread.php?t=981644]("http://ubuntuforums.org/showthread.php?t=981644")
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/297234]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/297234")
[http://techspalace.blogspot.com/2009/04/compiz-problem-in-jaunty-solved.html]("http://techspalace.blogspot.com/2009/04/compiz-problem-in-jaunty-solved.html")

---

### Post by P4man on 2009-10-25
Your videocard is blacklisted because it (or its drivers) is known not to work with compiz. Im guessing you have an old ATI card.

---

