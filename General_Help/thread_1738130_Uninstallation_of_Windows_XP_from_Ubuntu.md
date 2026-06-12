---
title: "Uninstallation of Windows XP from Ubuntu"
date: 2011-04-24
forum: General Help
---

### Post by wutzerface77 on 2011-04-24
Hey guys! This is my first thread so here goes: I recently installed Ubuntu 10.10 Maverick and I love it! I was already used to Ubuntu before i did this install, but there was one question I wanted to ask. How do I un-install Windows XP? I already checked my drive and it said there was no partition, and i don't have the disc for windows any more. I have no need for Windows because of Wine for Ubuntu, so if there is ANY suggestions at all, that would be great!

Thanks, Tim


:confused:

---

### Post by mike555 on 2011-04-24
no partition ???  if you installed inside XP (wubi ) then you can't just uninstall XP ......... 
 I suggest if you want to get rid of XP (and everything else on your computer), backup your stuff on an external drive then reinstall Ubuntu to whole hard drive.

---

### Post by mörgæs on 2011-04-24
Wubi has not been mentioned!

If you run Gparted from Ubuntu, you can see (and delete) the Windows partitions. 
After this works (test with a reboot), you can expand the Ubuntu partitions to use the free space. This must be done from a live boot.

---

### Post by wutzerface77 on 2011-04-24
Yeah i used Wubi and i do not have a live CD of Ubuntu.

---

### Post by wilee-nilee on 2011-04-24
> **wutzerface77 said:**
> Yeah i used Wubi and i do not have a live CD of Ubuntu.

Here is a thread on moving the wubi to a partition.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Before you do this though you should have a Ubuntu cd of Maverick it is your better tool maybe the best for fixing any problems.

Ask any questions if needed, and notice the automated transfer portion of the link.

---

### Post by wilee-nilee on 2011-04-24
> **mörgæs said:**
> Wubi has not been mentioned!

If you run Gparted from Ubuntu, you can see (and delete) the Windows partitions. 
After this works (test with a reboot), you can expand the Ubuntu partitions to use the free space. This must be done from a live boot.

Should be confirmed though before advising as we see here.;)

---

