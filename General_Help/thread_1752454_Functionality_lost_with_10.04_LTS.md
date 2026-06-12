---
title: "Functionality lost with 10.04 LTS"
date: 2011-05-07
forum: General Help
---

### Post by ghelbig on 2011-05-07
I finally upgraded my desktop from 9.10 to 10.04.

I do not feel that this was a step forward; a lot of little things just don't work.

For example, when shutting down with 9.10, it automatically shuts down in 60 seconds.  With 10.04, it waits *forever* for a 2nd mouse click.

The USB drive - there used to be an option to un-mount it without removing it.  That's gone now, and I'm guessing that I will find more of these as the days go on.

And all the colors have been removed from the panel applets.  Not really a functionality issue, but it is a negative to the user experience.

So my question is:  How can I restore these features?  Is there a configuration somewhere I can edit?

Thanks!

---

### Post by wolfen69 on 2011-05-07
Upgrades can sometimes go bad. I would do a fresh install.

---

### Post by 73ckn797 on 2011-05-07
Fresh install will prevent many issues. If you do that and have not created a separate /home partition then that will be the way to go. It will mean that you can move to a newer version without losing documents and settings for programs. You would have to still reinstall later added programs but would still have the settings you made.

Backup what documents you have before making the changes. You can designate the separate partition for /home during the installation.

---

### Post by tgalati4 on 2011-05-07
Any new distro (including dist-upgrades) will require tweaking to get them to work properly.  You didn't buy your machine with Ubuntu installed, so you have some legwork to do.  Most problems are fixable, but take patience.

Those things that don't work, but worked before are called "regressions".  Every update will have regressions.  It is the nature of Ubuntu to "refactor"--rewrite substantial sections of code to get new features.  This has the unintended effect of breaking things that used to work.  

Had you upgraded to Natty, then your machine would have been so balled up that you wouldn't be able to even ask for help on these forums.

On my lucid machine, shutdown only takes 6 seconds.  So something is hanging.  Check your log files (/var/log).

For the USB problem, Hotplug and HAL underwent major changes.  When you right-click on the USB-stick on the desktop, is there not an unmount or eject option?

For the panel applets, what desktop environment are you using?  If it is gnome, then perhaps removing those widgets and reinstalling them may fix the issue.

---

