---
title: "Firefox segmentation fault after installing Firetray"
date: 2009-12-11
forum: General Help
---

### Post by kneedan on 2009-12-11
I am running Ubuntu 9.10 and Firefox 3.5.5.  Earlier this evening, I installed Firetray 0.2.3.  After the installation, I told Firefox to restart -- like you do after installing a new add-on -- but it only closed without restarting and the two methods I could think of to address this do not work: 1) If I try to open it from the GUI, I see a "Starting Firefox Web Browser" tab open on the taskbar, which sits there for about eight seconds before it disappears, with no observable effect. 2) Trying to run Firefox from the terminal results in the message "Segmentation Fault."

If this were Windows, with which I am more familiar, failing all else I would just uninstall Firefox and start over afresh, but that does not appear to be an option here.  I also tried to hunt through the filesystem for some reference to firetray, thinking that maybe I could just delete it manually, but I found nothing in usr/lib/firefox.

Any assistance would be greatly appreciated.

---

### Post by kneedan on 2009-12-11
Update: firefox -safe-mode from the terminal was enough at least to remove Firetray.  I can get Firefox to start without any trouble now.  I'm still curious whether anyone has an idea how I can get the Firetray add-on to work on this machine.

---

