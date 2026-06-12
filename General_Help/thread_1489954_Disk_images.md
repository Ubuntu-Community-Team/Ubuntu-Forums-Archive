---
title: "Disk images"
date: 2010-05-21
forum: General Help
---

### Post by belnac on 2010-05-21
Hello,

I'm about to move my Ubuntu install from my external 250 GB HD (USB connected) to my laptop's master 90 GB SATA HD but before I do so I'd like to create a backup disk image of the SATA HD.

Trouble is the SATA HD contains two NTFS partitions and a Windows XP install and I'm not even sure if it is possible to create a safe and fully restorable disk image of NTFS partitions in Linux. If it is, how?

Also, when the time comes to migrate my Ubuntu install to the master HD, I was thinking of moving only a subset of all the data on it so as to keep certain folders (i.e. my mercurial repository; music; videos; basically anything that takes too much space) separate on the external drive. Is this possible at all or would it be better and perhaps safer to just install Ubuntu from scratch on the SATA HD?

Would really appreciate some pointers!

---

### Post by C.S.Cameron on 2010-05-21
You should be able to do it using the dd command, it will do just about anything,
Start here:

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

