---
title: "initial dual boot, deleted ubuntu, cannot load into vista"
date: 2010-05-20
forum: General Help
---

### Post by noobion on 2010-05-20
Hi, I had karmic koala installed a few months back, but wasn't using it cause i didn't have time to properly configure it. Last night, i was thinking of probing around with it a little and found an update for it and went ahead and installed it. After rebooting, GRUB refused to load any of the OSes, but i was still able to access ubuntu with a reduced graphics option (safe mode?). Tried reinstalling etc etc but nothing worked. In my frustration, i whipped out my windows CD and deleted the partition for ubuntu. Now, after the loading of bios, i get "error: no such partition. grub rescue>".

Is there anyway i can get delete grub and get my vista to boot normally? or would i need to reformat everything again? maybe someone can point me in the right direction if a similar thread had been posted before. otherwise, any form of help is greatly appreciated.

thanks in advance!

---

### Post by john newbuntu on 2010-05-20
Follow the instruction for "Fix mbr in vista" from this link:
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

At the command prompt, you need to type
bootrec.exe /fixmbr
bootrec.exe /fixboot

Hope that fixes it.

---

### Post by noobion on 2010-05-20
yes it did! thanks so much!

---

