---
title: "Ubuntu hibernation: Locks up on resume, but SysRq + R E will successfully wake"
date: 2011-09-19
forum: General Help
---

### Post by Coopster on 2011-09-19
The title pretty much describes my problem. I dual boot Windows 7 + Ubuntu 11.04 (both x64). I use s2disk (from the uswsusp package) in a script that hibernates Ubuntu and boots into Windows.

The system hibernates and reboots without a problem. However, on resume the system locks up and is unresponsive. If I use SysRq+R, I see the kernel message that input is returning to raw mode. If I then use SysRq+E, I see the message that it is terminating processes. At this point, there is a delay and then I see the locked GNOME session login screen. I can log in and successfully resume my work.

It's worth noting that my laptop (System76 netbook with same software stack) suffers from the exact same symptoms. Has anyone run into this problem? Alternatively, if someone is suffering from the 'locks up on resume from hibernate' issue, what happens if you try Ctrl+Alt+SysRq+R,E ?

---

