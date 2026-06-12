---
title: "Nvidia, must manually set Refresh Rate after every reboot"
date: 2010-05-11
forum: General Help
---

### Post by zim2dive on 2010-05-11
Most threads I've found are on losing resolution.. my issue is different.. I get the correct resolution (1920x1080), but after every reboot my screen looks fuzzy.

When I go into nvidia-settings, I see that my Refresh Rate is set to "Auto".

If I manually change it to 60 (or even 50), the screen snaps into good focus.  Then I save the xorg.conf and quit.

When I reboot.. its back to fuzzy.

I've seen many suggestions to run

nvidia-settings --load-settings-only (or something like that) at boot.. as far as I can tell, refresh rate is NOT saved in the local nvidia-settings.rc ... so running that command does NOT appear to solve this issue.

You can query the Refresh rate from the command line (with -q), but as far as I can tell, you cannot set it from the command line (only from inside the nvidia-settings GUI)

I tried editting my xorg.conf, removing the range it had and leaving 60 as the only option>     VertRefresh     60.0 thinking I might trick it into thinking it did not have any choice except 60... but it still came up fuzzy with "Auto" as the selected mode.

Looking for other ideas on how I can get this to setting to survive a reboot.

EDIT: this has been an issue for me with every nvidia driver (using the proprietary drivers) and over 2 different GPUs, so I don't thinks its specific to any card, nor driver revision.

---

