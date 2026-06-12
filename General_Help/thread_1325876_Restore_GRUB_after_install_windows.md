---
title: "Restore GRUB after install windows"
date: 2009-11-13
forum: General Help
---

### Post by vnluc on 2009-11-13
Assuming I install Windows on   /dev/sda2   and Ubuntu on   /dev/sda3

Now my Windows corrupt, I have to reinstall it but after that I can not boot to Ubuntu any more. How can I repair the GRUB loader so it will help me to dual boot again?

---

### Post by frank_acies on 2009-11-13
using a livecd should do it.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by caue.rego on 2009-11-18
> **frank_acies said:**
> using a livecd should do it.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I just noticed that **sudo grub** doesn't work anymore on Karmic Koala.

So try this instead: [http://ubuntuforums.org/showthread.php?p=8339670](http://ubuntuforums.org/showthread.php?p=8339670)

---

