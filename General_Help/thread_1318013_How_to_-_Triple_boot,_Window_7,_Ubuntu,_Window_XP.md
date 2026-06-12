---
title: "How to - Triple boot, Window 7, Ubuntu, Window XP"
date: 2009-11-07
forum: General Help
---

### Post by netlaptop on 2009-11-07
For some reasons, I need to install a really Window XP (not on virtual machine, or Window XP mode on Window 7).

I have only 1 HDD. And there are 4 partitions on it.

Unallocated---- Window 7---- Ext 4 (Ubuntu)----Swap

I installed Window Vista first then upgraded to Window 7 Home Premium, then Ubuntu 9.04.

Now I would like to install Window XP to that unallocated partition? :D

Any ideas?

---

### Post by adamdotanderson on 2009-12-02
Assuming the partition is large enough, you should be able to run the installer from the Windows XP disc normally, selecting the unallocated space as your destination. Once complete, you will need to boot your system from you Ubuntu disk and reinstall the grub bootloader since Windows XP will overwrite it during the install process. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by netlaptop on 2009-12-04
Thnx for your reply.

I will try doing it when I finished my current project.

---

