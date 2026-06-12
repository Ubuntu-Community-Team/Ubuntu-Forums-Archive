---
title: "Memory Problem"
date: 2010-05-10
forum: General Help
---

### Post by Richiegs on 2010-05-10
I installed Ubuntu using Wubi in my PC. Now my PC always warns me that "The computer has only 46 MB disk space remaining." My PC has 160 GB of memory and I have used a total of 50 GB so far. Thus, I should have 110 GB of disk space remaining in my hard disk. 
Can anyone offers me a solution to solve this problem? Many thanks

---

### Post by MooPi on 2010-05-10
I'm going to assume that your Linux side is giving you this warning. The warning is because the wubi install has limited space and is running out. Your hard drive is not filling up just your Ubuntu install. The wubi Ubuntu install is inside your Windows folder and has a finite space. Maybe it's time to download the install CD and try the full install dual boot ?

---

### Post by 3rdalbum on 2010-05-10
When you installed Ubuntu using Wubi, it asks you how much space you want to allocate to Ubuntu. It does this because Ubuntu will sit inside a file on your hard disk, of fixed size. Obviously this file is getting full. It doesn't matter how much space you have on your disk, if the Ubuntu file is 16 gigabytes, it can't expand.

Now that you've been using Ubuntu for six or seven months, it's probably a good time for you to repartition your hard disk and install Ubuntu for real, as a real dual-boot system (or single-boot, if you're ready to dump Windows).

Otherwise you could check out the Misc section of the Wubi Guide ([https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)) for details on resizing the Ubuntu file.

---

### Post by Richiegs on 2010-05-11
I just spent the entire Sunday to install Ubuntu 10.04 and other applications in my PC last week. Is there an easy way to fix this problem without reinstalling Ubuntu as a separate system? Moreover, the dvd drive in my PC is broken. Many thanks

---

