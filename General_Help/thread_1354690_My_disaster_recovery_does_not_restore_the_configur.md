---
title: "My disaster recovery does not restore the configuration"
date: 2009-12-14
forum: General Help
---

### Post by OldGrantonian on 2009-12-14
I have Karmic. I've experimented with grsync, and I can use it successfully. I hope :)

My disaster recover plan was as follows:

• Re-install Karmic from ISO CD.
• Recover the following offline directories from HDD:
&#8728; /etc
&#8728; /home
&#8728; /usr/local
&#8728; /var

When I try this plan, I was assuming that my configuration would then be identical to the pre-disaster configuration. 

The test configuration that I've backed up is as follows:
• DVD player working OK
• Broadcom STA driver activated
• Wireless working OK
• gnome-commander installed
• gnometris (a default game) uninstalled (grsync will delete files from the destination that are not on the source)

However, when I test my plan by re-installing from CD, then using grsync to pull back the directories, I don't see any change from the installed CD configuration. None of the "backed up" configuration changes take effect. 

BTW: When I do the grsync restores, I can see many files being transferred from my external HDD to my laptop. This proves that something is happening, because I've configured grsync so that files on the laptop can be updated, but identical files are not transferred.

Am I backing up the correct directories to restore a pre-disaster configuration?
.

---

### Post by nishant.singh28 on 2009-12-14
Try this...done it 4-5 times :D
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

---

