---
title: "uninstalling help"
date: 2011-04-25
forum: General Help
---

### Post by akTHEbak on 2011-04-25
i have windows 7 and ubuntu 10.10 installed on my machine..dual boot..i want to get rid of ubuntu..should i go to my computer and clcik manage and delete the partition i had ubuntu on??? and i heard that people where having problems booting??? can someone guide me through the correct way of doing this

---

### Post by lithopsian on 2011-04-25
Yes, uninstalling Ubuntu is as simple as removing the partition(s) it is on.

If you do this with a dual boot machine you will most likely be left with an non-working Grub in the master boot record, so your machine won't boot.  There are utilities to replace this so you can boot directly to windows again.  In XP there was a command on the recovery disk, and I guess Windows 7 would be the same.  Or you may have a separate /boot partition and still be able to boot to Windows through Grub.

---

### Post by bodhi.zazen on 2011-04-25
> **lithopsian said:**
> Yes, uninstalling Ubuntu is as simple as removing the partition(s) it is on.

It is not that simple, you need to fix your master boot record.

It also depends on how you installed ubuntu . Wubi or standard ?

There are tons of guides available to do this, some even from microsoft.

[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

If you have specific questions, feel free to ask. Otherwise good luck to you.

---

