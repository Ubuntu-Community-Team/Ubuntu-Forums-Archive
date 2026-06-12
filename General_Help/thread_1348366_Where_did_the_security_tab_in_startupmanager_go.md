---
title: "Where did the security tab in startupmanager go?"
date: 2009-12-07
forum: General Help
---

### Post by Rytron on 2009-12-07
Hi.
In Ubuntu 9.04 I used startupmanager to password protect GRUB. However in Ubuntu 9.10, the security tab is missing from startupmanager.
Why is this? Is there another GUI method/program to password protect GRUB?

---

### Post by sisco311 on 2009-12-07
GRUB 2 is the default boot loader for new installations of Karmic, replacing the previous GRUB "Legacy" boot loader.

Grub2 is still beta software, the password protection of menu entries is not implemented yet.

Also some users reported that SUM doesn't play nice with Grub2, I would suggest you to configure Grub2 manually.

If you want to password protect the menu entries, you have to install Grub Legacy.

[uhelp]community/Grub2[/uhelp]
[thread=1302743]Grub 2 - 5 Common Tasks[/thread]
[thread=1287602]Grub 2 Title Tweaks[/thread]
[thread=1195275]The Grub 2 Guide[/thread]

---

### Post by Rytron on 2009-12-07
Thank you sisco311. Perhaps so in the future, startupmanager will have the security tab feature restored?

---

### Post by sisco311 on 2009-12-07
Yes, I don't see why not. :)

BTW, it looks like that some basic authentication support has been implemented in Grub2:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/392158]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/392158")

---

