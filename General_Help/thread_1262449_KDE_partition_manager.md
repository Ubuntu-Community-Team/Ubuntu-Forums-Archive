---
title: "KDE partition manager"
date: 2009-09-09
forum: General Help
---

### Post by voteforcondit on 2009-09-09
i am trying to use kde partition manager and i keep getting this

Warning: You do not have administrative privileges. 
It is possible to run KDE Partition Manager without these privileges. You will, however, not be allowed to apply operations. 
Do you want to continue running KDE Partition Manager?

how do i get these administrative privileges??

---

### Post by voteforcondit on 2009-09-10
in my user and group settings it says that i have administrative priv.... i dont get it...

---

### Post by VolkerLanz on 2009-09-18
> **voteforcondit said:**
> i am trying to use kde partition manager and i keep getting this

Warning: You do not have administrative privileges. 
It is possible to run KDE Partition Manager without these privileges. You will, however, not be allowed to apply operations. 
Do you want to continue running KDE Partition Manager?

how do i get these administrative privileges??

KDE Partition Manager requires root privileges to perform all its tasks. This is so because the Linux kernel needs to be notified of what you did with your partition tables once you're done and this notification will only be accepted from someone with root privileges.

Normally you shouldn't even see this message if you're running KDE Partition Manager from the KDE application launcher or from KRunner because KDE Partition Manager's desktop file will make KDE ask you for your root password before you can continue.

If you see this message, you probably ran KDE Partition Manager from a shell directly. In this case, try

$ kdesudo partitionmanager

Ps. What version are you using?

---

### Post by fevemo on 2010-03-22
I had the same problem and I was able to solve it running:
[CENTER][COLOR=DarkRed]sudo partitionmanager
[/COLOR][LEFT][COLOR=DarkRed][COLOR=Black]on terminal:)[/COLOR][/COLOR]
[/LEFT]


[/CENTER]

---

