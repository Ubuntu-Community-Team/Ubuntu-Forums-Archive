---
title: "Is it possible for Linux to get registry errors?"
date: 2010-06-06
forum: General Help
---

### Post by leeman101 on 2010-06-06
Is it possible for Linux to get registry errors?
may be a dumb question but im fairly new to linux and have not done anything too low-level.
thanks

---

### Post by jerenept on 2010-06-06
No. Have you seen any error like that in ubuntu?

---

### Post by leeman101 on 2010-06-06
No i have not.  I have a friend who is worried about registry errors and i did not believe it was possible.  Wanted to double check.   thank you.  :)

---

### Post by nemilar on 2010-06-06
No, because Linux does not use a registry in the Windows sense of the term. 

Linux does have many (and I mean *many*) configuration files, though.  Most system-wide configuration files go in the /etc directory.  Your individual user also has a lot of configuration files hidden in the home directory, for example under ~/.gconf

It is possible that these files can become corrupt, but generally only if you corrupt them.  It's not like one day you are going to boot up your system and BAM you have a corrupted configuration that won't boot anymore.

---

### Post by Mike'sHardLinux on 2010-06-06
You don't have to worry about registry errors in Linux. This is one of the things I like about Linux versus Windows:
Windows = all eggs in one basket (registry) - kill the registry, kill windows..period...and I HAVE in fact seen it happen many times. Sometimes you can recover, sometimes, you gotta do a fresh re-install.

Linux = flat text files for configurations, and all separate: network, fstab, grub, video driver config, etc....

---

### Post by stderr on 2010-06-06
Yeah as nemilar says, Ubuntu has GConf which is similar, but much less widely used than Winblows registry, and a recent addition at that. You'd have to do well to really mess the GConf data store up though!

---

### Post by leeman101 on 2010-06-06
Thanks guys.  This info helps a lot.  Always looking to learn more :) Im marking this thread as solved now...

---

