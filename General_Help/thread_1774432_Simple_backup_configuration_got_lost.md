---
title: "Simple backup configuration got lost"
date: 2011-06-03
forum: General Help
---

### Post by legendbb on 2011-06-03
uBuntu 10.10, Simple Backup

My backup stopped working at certain date. 

Went back in "Simple backup-Configuration", it says, there is no configuration.

What might cause trouble like this? Should I seek for more secure back up tool?

Please give me some hints, 

Thanks,

---

### Post by legendbb on 2011-06-07
I think I can add some thing here to share, let google direct people might needs such info.

It's not a bug of SBackup.

Synatic installs SBackup and creates two sets of shortcuts in Gnome menu, one set in Application>Accessories, another set in Application>System. Use the one in Application>System, better disable the one on Accessories cause it doesn't ask for root permission and might not work to folders which requires root privilege 

Application>Accessories is confusing too, since if you configured in Application>System>Simple Backup, your configure profile won't show up in Application>Accessories, that's all my previous confusion came from.

Other hint on configuring SBacup to 2nd harddrive:, make sure the 2nd harddrive automatically mount on boot, otherwise; if system reboots, and SBackup won't be able to find the hardrive, it will back up to $HOME of whoever configured the backup profile.

:popcorn:

---

### Post by ChrisKu on 2011-06-07
Thanks for sharing your solution.

---

