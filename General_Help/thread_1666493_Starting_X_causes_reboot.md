---
title: "Starting X causes reboot"
date: 2011-01-13
forum: General Help
---

### Post by aydun on 2011-01-13
Ubuntu 10.10 32-bit has been running fine but now gets stuck in a loop when booting.  It gets as far as the ubuntu graphic screen with the 5 dots and then the PC reboots.

If I use the recovery option (single-user) and then "resume normal boot", it boots ok but does not start all the services. 

I disabled gdm (by renaming /etc/init/gdm.conf to /etc/init/gdm.conf-off) and then it boots normally (without gdm).  If I then rename the conf file and start gdm manually (initctl start gdm) then again it reboots.  Alternatively, if use "startx" instead of gdm, it reboots sometimes but not always.

If X does start then things are stable, but it is intermittent whether starting X works normally or causes a reboot.

There have been no changes other than standard updates.

Has anyone else seen this?

---

