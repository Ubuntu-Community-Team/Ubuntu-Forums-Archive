---
title: "Menu.lst not in /boot/grub?"
date: 2010-07-25
forum: General Help
---

### Post by parham-d on 2010-07-25
Hello,

My girlfriend has installed Ubuntu, but does not find the menu.lst file in /boot/grub folder, even though she has run 'sudo update-grub'. When she types 'grub' however, she gets told that she does not have grub installed.

Thanks!

---

### Post by kerry_s on 2010-07-25
ubuntu has grub2, it doesn't use menu.lst

---

### Post by drs305 on 2010-07-25
Recent releases of Ubuntu now use Grub 2. There are major changes to the files used by Grub 2, and there is no longer a "menu.lst". Read about Grub2, if that is what her system uses, via the links in my signature line. The community doc is Grub2, Grub2 Basics is a post on this forum. "G2 Tasks" covers a few of the most common things a user might want to change, such as menu timeout, default OS, etc.

She can tell if she is using Grub2 by checking the version at the top of the menu when she boots, or by running this command:
```
grub-install -v
```

Grub legacy is version 0.97, Grub2 is 1.96 or later.

---

### Post by parham-d on 2010-07-25
Thanks. The link in your signature talked about start-up manager, and since she's not a fan of command prompt and terminal,  I recommended that to her. It worked, apparently. She chose Microsoft Windows as her default operating system. :)

---

### Post by parham-d on 2010-07-25
> **parham-d said:**
> Thanks. The link in your signature talked about start-up manager, and since she's not a fan of command prompt and terminal,  I recommended that to her. It worked, apparently. She chose Microsoft Windows as her default operating system. :)
Thanks, worked!

---

### Post by drs305 on 2010-07-25
Startup-Manager will work with some but not all of the Grub 2 settings. Fortunately it still works for the major tweaks such as the default OS.

If you don't have any more questions on this subject, would you please mark the thread SOLVED via the "Thread Tools" link at the top right of the first post. It lets 'helpers' concentrate on unresolved issues. (You can reverse the SOLVED designation if necessary from the same link). Thanks.

---

