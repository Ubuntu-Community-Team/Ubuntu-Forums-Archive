---
title: "/boot/grub/menu.lst is missing"
date: 2010-06-30
forum: General Help
---

### Post by Bradj47 on 2010-06-30
This is really weird. I boot up my netbook this morning to have a look at my menu.lst file. It boot up without any problems. It brought me through the GRUB menu and everything. In fact I remember editing menu.lst weeks ago to remove excessive entries and it brought me to the GRUB menu of that same edit. Yet when I cd into /boot/grub and **vi menu.lst** I'm apparently opening a new file. Was there an update or something that moved the location of this file? Where is it?

---

### Post by Vaphell on 2010-06-30
maybe you use grub2 and the config file is in a different place?

---

### Post by SoFl W on 2010-06-30
Grub 2 doesn't use menu.lst.  To update the grub 2 menu use "sudo update-grub2".  I can't remember the configuration file/menu list.

---

### Post by Noz3001 on 2010-06-30
Yeah, it's moved to /boot/grub/grub.cfg and the syntax changed

---

### Post by Bradj47 on 2010-06-30
> **Noz3001 said:**
> Yeah, it's moved to /boot/grub/grub.cfg and the syntax changed

um... why?

---

### Post by Rubi1200 on 2010-06-30
See this:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

and this:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Hope this helps.

---

### Post by dabl on 2010-06-30
News flash:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by celldweller1591 on 2010-06-30
> Yeah, it's moved to /boot/grub/grub.cfg and the syntax changed +1 . From karmic onwards , its there. i.e grub 1.97(grub2)

---

