---
title: "Everytime GRUB2 updates, I lose the ability to boot"
date: 2010-05-07
forum: General Help
---

### Post by gohanssjn on 2010-05-07
Basically, I cannot load 10.04 without 'nomodeset' being set in the boot line.  Is there a way to make GRUB2 append this to every entry automatically?

Can I change the entry I have now somehow?  Not a fan of GRUB2 so far here...

---

### Post by louieb on 2010-05-07
If I recall right that can be done by editing /etc/default/grub - look for GRUB_CMDLINE_LINUX_DEFAULT=  and modify it to your needs. 

[Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275")

---

