---
title: "Cannot delete or empty .Trash-1000 folder"
date: 2010-05-05
forum: General Help
---

### Post by LucHub on 2010-05-05
Hi all,

Straight to the problem on my [Ubuntu 9.10].

I cannot delete or empty my .Trash-1000 folder on my flash drive. I tried changing permission with chmod but no way, I cannot empty the folder via the Ubuntu main trash option 'Empty Trash'. I read a bunch of threads but no way.

Do you know a solution that works to this problem?

Even further. Do you know a way to tell nautilus to avoid using that folder in my USB devices and use instead the normal trash folder on my system?

Thanks in advance.

PS I don't have windows on my PC so please don't tell me to find a win software to solve the problem (I read it in many threads).

---

### Post by Peter09 on 2010-05-05
Use sudo chmod ......<file name>

---

### Post by dino99 on 2010-05-05
sudo rm -rf /the path to/.Trash-1000

---

### Post by LucHub on 2010-05-05
Thanks for the quick reply.

I tried to delete via command line but I have this message (I pout only an example for one of the files):

Command: *sudo rm -rf /media/LUCHUBUSB/.Trash-1000/*
Response: *rm: cannot remove `/media/LUCHUBUSB/.Trash-1000/files/rdiff-backup-data.2/pybackpack.set': Read-only file system*

So then I tried to change permission with chmod:

Command: *sudo chmod -R a+rw .Trash-1000/*
Response: *chmod: changing permissions of `.Trash-1000/files/rdiff-backup-data.2/pybackpack.set': Read-only file system*

BTW, even after this I cannot remove. Going further, there should be a way to avoid using the command line and to tell Nautilus at least the maximum dimension in MB of that folder.

---

### Post by Peter09 on 2010-05-05
Some flash drives have a small switch on the side which makes them read only - its worth a check.

---

### Post by LucHub on 2010-05-05
> **Peter09 said:**
> Some flash drives have a small switch on the side which makes them read only - its worth a check.
No, sorry

---

