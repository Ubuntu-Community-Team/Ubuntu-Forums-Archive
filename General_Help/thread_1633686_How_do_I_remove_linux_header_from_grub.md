---
title: "How do I remove linux header from grub"
date: 2010-11-29
forum: General Help
---

### Post by germanix on 2010-11-29
The latest update installed a new linux header 2.6.35-23. The older version 2.6.35-22 also appears in grub. What would be the sense in keeping them both? And if not required how do I remove the older version from grub?
I tried:  "sudo update-grub" which changed nothing
I would appreciate some guidance in this matter.

---

### Post by Rubi1200 on 2010-11-29
After kernel updates an entry is added to the GRUB menu.

Most experienced users will advise you to keep at least one spare entry in the event that an update fails and you need to boot an earlier version for troubleshooting purposes.

If you have just those 2 entries, I would not worry too much about it.

Updating GRUB, as you saw, does not change it.

If you are interested in creating a custom menu, understanding how GRUB2 works, and how to add/remove entries take a look here at the guide written by drs305:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by germanix on 2010-11-29
Thank you very much for this information. I will take your good advice and keep them both. Thank you also for the link to the guide. I will surely look into it. Have a nice day.

---

### Post by Rubi1200 on 2010-11-30
You are more than welcome :)

There is a lot of information in the guide and drs305 has done a fantastic job of putting it all together for us.

---

