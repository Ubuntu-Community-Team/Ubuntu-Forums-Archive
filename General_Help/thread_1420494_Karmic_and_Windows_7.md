---
title: "Karmic and Windows 7"
date: 2010-03-03
forum: General Help
---

### Post by Michael_Parr on 2010-03-03
This isn't a huge issue, but something i'd like to fix. I'm not even 100% sure its related but i'll see what you think.

I just installed Ubuntu 9.10, on a second partition on my second hard-drive. It installed... well enough (Lots of hardware issues to sort though). So i now have it duel booted with Windows 7 Ultimate 64bit.

Problem now is, when i go back into Windows 7, i'm unable to load the.. Computer manager (Right click My Computer - Manage) to see drive partitions, services and such.

I get the following error - "This file does not have a program associated with it for performing this action. Please install a program or, if one is already installed, create an association in the Default Programs control panel".

[B]1. Is this related to my install of Ubuntu?
[/B]**2. How do i fix this problem?**

---

### Post by gsmanners on 2010-03-03
Windows doesn't come with any ext format drivers, so if you want to see those partitions in Windows you need to install [Ext2Fsd]("http://www.ext2fsd.com/").

---

