---
title: "Lost gui/taskbar etc in 10.04 server"
date: 2011-09-16
forum: General Help
---

### Post by doktarZues on 2011-09-16
I've honestly no clue how it happened because I was not messing with anything (have not made configuration changes on my server in several months), but one day I turned the monitor on to my server and the taskbar was missing at the bottom (when I minimized windows, they would animate like they were minimizing but I couldn't see them).  In System>preferences>appearances it said that clearlooks would not work because parts of the gtk+ engine was not installed.  

So now I've uninstalled and reinstalled nautilus, (sudo apt-get remove/install nautilus) and when I try and startx it simply goes to a black screen with a cursor, but nothing else.  Can't even figure out how to get back to the cmd line without rebooting. 

I can post error logs or configuration files on request but wouldn't know where to start without direction.  Any help would be greatly appreciated.

---

### Post by dcstar on 2011-09-17
> **doktarZues said:**
> I've honestly no clue how it happened because I was not messing with anything (have not made configuration changes on my server in several months), but one day I turned the monitor on to my server and the taskbar was missing at the bottom (when I minimized windows, they would animate like they were minimizing but I couldn't see them).  In System>preferences>appearances it said that clearlooks would not work because parts of the gtk+ engine was not installed.  

So now I've uninstalled and reinstalled nautilus, (sudo apt-get remove/install nautilus) and when I try and startx it simply goes to a black screen with a cursor, but nothing else.  Can't even figure out how to get back to the cmd line without rebooting. 

I can post error logs or configuration files on request but wouldn't know where to start without direction.  Any help would be greatly appreciated.

Completely remove and reinstall the **ubuntu-desktop** package.

---

