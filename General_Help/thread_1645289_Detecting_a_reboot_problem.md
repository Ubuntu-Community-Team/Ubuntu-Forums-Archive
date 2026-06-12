---
title: "Detecting a reboot problem"
date: 2010-12-14
forum: General Help
---

### Post by tkoco on 2010-12-14
Scenario:

Remote Linux system with BIOS set to reboot if "loss of power" happens. The system does reboot, but the web server sometimes does not start up properly. Seems to think that it is already running.

So, is there a clean way to detect that an unscheduled reboot has occurred? I am thinking about a cron driven script which would check for an unscheduled reboot and then restart the web server in a proper fashion should the reboot occur. If I reboot the system via ssh, I could touch a file which would block the script until I removed the file.

Any suggestions?

Update: Wrote a python script to look for the potentially missing process. The script creates a file which is tested for in the /etc/rc.local file. If the file exist, it cleans up the system and removes the file.

---

