---
title: "Ubuntu 11.04 not powering off properly"
date: 2011-09-15
forum: General Help
---

### Post by LordJamba on 2011-09-15
Hello, been having kind of a strange problem after installing 11.04 X64. When I try to reboot/poweroff my machine it begins the shutdown process but stops with 3 orange dots frozen on the screen, this does not occur every time I shut down, and issuing the poweroff/reboot command from the CLI seems to make no difference ( as opposed to using the gnome interface to shut down.) I have done a bit of searching on the topic and have found other cases with the same problem, but have yet to find a fix for it. 

Any help would be greatly appreciated.

-Thanks

---

### Post by 2F4U on 2011-09-15
Did you already look into syslog and, maybe, /var/log/Xorg.0.log and ~/.xsession-errors? Those log files may contain valueable information.

---

### Post by LordJamba on 2011-09-15
I took a peek at the syslog before work today, didn't see anything that stood out, I'll check the X logs and post the results when I get home. 

Thanks for your help

---

### Post by brucehohl on 2011-09-15
I have the same problem and have been trying various possible fixes.  See this topic: [http://ubuntuforums.org/showthread.php?t=1838460](http://ubuntuforums.org/showthread.php?t=1838460)

This is a known problem.  If you indicate that this bug affect you that will increase the 'bug heat':
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203)

---

