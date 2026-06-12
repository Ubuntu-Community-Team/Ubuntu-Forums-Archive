---
title: "Ubuntu 10.04 Software Center Problems"
date: 2010-07-17
forum: General Help
---

### Post by Speedcuber on 2010-07-17
Hi,

Today, I installed Ubuntu 10.04. About an hour ago, I opened up the Software Center for the first time and navigated to Quanta Plus, a program I wanted to install. I typed in my password as prompted and the installation began. After waiting for a few minutes, I clicked on the "In progress" button on the right and saw that the bar was at about 50%. While I waited, I minimized the software center and started to look at some of the other features.

I opened up "Disk Usage Analyzer" to have a look. However, the window was unusual; although the bar at the top was there, the interior of the window was white. I could not close this window. I then tried some other applications and encountered the exact same thing. (Firefox was still working, though.) I reopened the software center (which was also not white) and saw that the in progress button on the left had disappeared so I assumed that it had finished. I then restarted the computer.

When I rebooted, I got a message about disk problems. I pressed "f" to "try and fix" the problems. I then got a message saying to "report". Back at the desktop now, the white windows problem was fixed, but when I reopened the software center and try to install any program, I get the message "Package operation failed".

This is the "Details" when trying to install Quanta (which has not been installed).
```
E:I wasn't able to locate a file for the kompare package. This might mean you need to manually fix this package. (due to missing arch): Setting up libqt3-mt (3:3.3.8-b-6ubuntu2) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libqt3-mt (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up liblua50 (5.0.3-4) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing liblua50 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of klinkstatus-kde3: 
 klinkstatus-kde3 depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing klinkstatus-kde3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libavahi-qt3-1: 
 libavahi-qt3-1 depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing libavahi-qt3-1 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of liblualib50: 
 liblualib50 depends on liblua50 (>= 5.0.3); however: 
  Package liblua50 is not configured yet. 
dpkg: error processing liblualib50 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of kfilereplace-kde3: 
 kfilereplace-kde3 depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing kfilereplace-kde3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of kommander-kde3: 
 kommander-kde3 depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing kommander-kde3 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of kdelibs4c2a: 
 kdelibs4c2a depends on libavahi-qt3-1 (>= 0.6.16); however: 
  Package libavahi-qt3-1 is not configured yet. 
 kdelibs4c2a depends on liblua50 (>= 5.0.3); however: 
  Package liblua50 is not configured yet. 
 kdelibs4c2a depends on liblualib50 (>= 5.0.3); however: 
  Package liblualib50 is not configured yet. 
 kdelibs4c2a depends on libqt3-mt (>= 3:3.3.8-b); however: 
  Package libqt3-mt is not configured yet. 
dpkg: error processing kdelibs4c2a (--configure): 
 dependency problems - leaving unconfigured 

```Thanks for any help. By the way, I have rebooted many times with no change.

---

### Post by Speedcuber on 2010-07-17
OK...so I uninstalled and reinstalled Ubuntu Software Center using the terminal. I am encountering a peculiar problem, though...

I went to try and install Quanta Plus like I originally wanted to. This time, it seemed to install normally for a while, but then the same message came up, telling me that the package failed to install. However, Quanta had installed--I could run it perfectly normally. Why does the software center think that it is not working?

I guess most of my problem is solved--but I would really like to fix this glitch with the false error message. Any ideas?

---

### Post by Speedcuber on 2010-08-03
Ok...I'm still getting the same problem. Whenever I install or uninstall something, using either Ubuntu Software Center or Synaptic, I get the error message saying it did not work...but it did work! Even though everything seems to work, this false error message makes me feel as if there is something wrong with my system. Is there any way to fix this glitch?

---

