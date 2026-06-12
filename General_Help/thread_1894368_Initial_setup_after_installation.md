---
title: "Initial setup after installation"
date: 2011-12-12
forum: General Help
---

### Post by supradave on 2011-12-12
If I were to install a system for someone and then deliver it, is there a utility to do the initial setup again, like user, time zone, et. al.  Yes, I know I can do a dpkg-reconfigure, but I'm looking for a turn-on-the-system setup.

Thanks,
Dave

---

### Post by arubislander on 2011-12-12
Not sure of a utility, but there is an install procedure: Do an OEM Install.

---

### Post by oldtimer7777 on 2011-12-12
> **supradave said:**
> If I were to install a system for someone and then deliver it, is there a utility to do the initial setup again, like user, time zone, et. al.  Yes, I know I can do a dpkg-reconfigure, but I'm looking for a turn-on-the-system setup.

Thanks,
Dave

What I do instead is create a backup of the existing system you want to duplicate with Remastersys Backup (use the backup option, not the dist option) and create a live bootable USB Flash Drive with Startup Disc Creator with the custom.iso created with Remastersys Backup of the old system.  You can then reinstall the entire backup on any computer you want. That includes everything, even login info, time zone, etc.   Make sure you backup all your data, just like you normally would, and get the system compressed size down below 4.7 gb.  That means, you need to do data migration onto an external hard drive from the old system and remove any packages you don't need, etc etc.. Then you move the rest of the backup files from the external onto your reinstalled restored system.   The system will be identical that way..

More info:

[https://debianhelp.wordpress.com/2011/10/12/relinux-a-new-fork-of-remastersys/](https://debianhelp.wordpress.com/2011/10/12/relinux-a-new-fork-of-remastersys/)

---

