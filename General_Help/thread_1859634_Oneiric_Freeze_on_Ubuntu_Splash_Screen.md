---
title: "Oneiric Freeze on Ubuntu Splash Screen"
date: 2011-10-14
forum: General Help
---

### Post by windfix on 2011-10-14
I just installed 11.10.  It restarts after completion and boots fine.  Once I log out or restart, however, it freezes on the Ubuntu splash screen.

After the first time, I re-installed it; same behavior.  One successful login, then freeze.

Help?


(I am on a W7 dual boot, W7 is fine.  I installed by formatting the old Natty partition and mounting it as /, left my separate home partition unformatted and mounted as /home.  I also have a swap partition, which I left alone.)
(Second time through the installer, I just chose to "upgrade 11.10 to 11.10 and clear system settings - rather than assigning the partitions manually)

---

### Post by windfix on 2011-10-14
After a 3rd installation, I can log in again.  

I have an Nvidia GT218 [NVS 3100M] graphics card. My theory is that:
1st attempt:  I did not wait long enough for the Additional Drivers utility to identify it and download the proprietary driver. On logout, the lack of driver caused the problem.
2nd attempt:  I attempted to install the recommended Nvidia driver, but I though that the installation hanged and cut it short.  Another fail
3rd attempt:  I ran the proprietary driver install and went away for 45 minutes.  Eventually it did download and activate. Unfortunately, I chose the "post-release updates) version rather than the recommended version, and still can only run Unity 2D

Hopefully I can change to the recommended version without another reinstall.

---

