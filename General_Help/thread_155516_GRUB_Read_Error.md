---
title: "GRUB Read Error"
date: 2006-04-05
forum: General Help
---

### Post by bradgentry on 2006-04-05
Hello; I have a nearly done for hard drive that's been giving me trouble.  I've backed up all the data and I want to take it out, but when I disconnect it and reboot, GRUB cannot load, giving me a read error in stage1.5.  The hard drive I am disconnecting is the slave on the primary IDE channel.  Anyone know what I have to alter to make GRUB forget about this HD?  Yes, I already tried hitting it.  Didn't work :-?   Thanks!

---

### Post by bradgentry on 2006-04-07
Anyone had a chance to look at this yet?

---

### Post by testube_babies on 2006-04-07
Have you tried kicking it?



But seriously, I've heard that GrubConf ([http://grubconf.sourceforge.net/]("http://grubconf.sourceforge.net/")) has many options for configuring GRUB.  Although I've never used it myself, it might be worth a try.

---

