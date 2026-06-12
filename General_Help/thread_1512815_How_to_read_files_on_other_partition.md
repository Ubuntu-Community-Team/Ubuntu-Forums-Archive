---
title: "How to read files on other partition?"
date: 2010-06-18
forum: General Help
---

### Post by penern on 2010-06-18
I was trying to uninstall all my audio drivers/software because of conflict issues. Anyway, somehow I corrupted/deleted/destroyed important stuff. When I try to boot I get this message, "Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure them yourself". I tried doing some of the various things suggested on the forum, to no avail. It wont let me log directly to the computer at the any terminal it offers because it wont accept my user name etc. Anyway, I partitioned the drive and loaded a fresh copy of 10.04 (which is what I already have) and would like to view the files on the corrupted side so I can import my urgent documents. How do I do that?

---

### Post by bobcollard on 2010-06-18
> **penern said:**
> I was trying to uninstall all my audio drivers/software because of conflict issues. Anyway, somehow I corrupted/deleted/destroyed important stuff. When I try to boot I get this message, "Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure them yourself". I tried doing some of the various things suggested on the forum, to no avail. It wont let me log directly to the computer at the any terminal it offers because it wont accept my user name etc. Anyway, I partitioned the drive and loaded a fresh copy of 10.04 (which is what I already have) and would like to view the files on the corrupted side so I can import my urgent documents. How do I do that?
Try running your Live CD and see if you can read anything on that partition through the File Manager.  You may need root access to move or copy anything.

---

### Post by penern on 2010-06-18
I don't have Live CD and how do I get root access? When I look at the partition details, it tells me that it is not a bootable drive, which had become obvious. I am thinking that I might have to take the drive out and access it from my other computer using  my USB  hard drive adapter. This worked for getting my photos off an old dead laptop. I was rather hoping that there was a way of viewing the unbootable drive's contents from within the new partition.

---

### Post by penern on 2010-06-19
I fixed the boot problem by running *$ sudo apt-get install ubuntu-desktop* This got my computer up and running again AND somehow fixed the Skype sound issue that caused all this. However, I would still like to know how to read files from the other partition if anyone can help.

---

### Post by bobcollard on 2010-06-19
> **penern said:**
> I fixed the boot problem by running *$ sudo apt-get install ubuntu-desktop* This got my computer up and running again AND somehow fixed the Skype sound issue that caused all this. However, I would still like to know how to read files from the other partition if anyone can help.
If you didn't use a live CD you may have used a USB thumb drive to install, either way look in the File manager for the partition.  You may even see it in the left column of the File Manager for your new partition.  To get root access open Terminal and type in   ```
gksu "file manager"
```  where file manger for me is thunar, yours may be something else, without the quotes.

---

