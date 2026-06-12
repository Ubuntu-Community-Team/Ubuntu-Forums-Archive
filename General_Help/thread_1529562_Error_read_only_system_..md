---
title: "Error read only system ."
date: 2010-07-12
forum: General Help
---

### Post by Maximus20 on 2010-07-12
Well i've searched the forum for this problem but i didn't find anything good to fix it.
Lets get to the point :
I've rebooted my system like 30 minutes ago...and all the sudden i get the error related the that program in ubuntu 8.04 that checks the disk after reboot for bugs an stuff like that...
The error is caused by "read only system" mode...it can't write anything onto the HDD .
I can't even change /etc/fstab file with nano or anything else...btw is server edition...i mean when i want to save the file (fstab) same damn thing read-only system how can i change that ?...'cuz i'm going crazy...thats my hosting server :|...

Thanks in advance .

---

### Post by 3rdalbum on 2010-07-12
The filesystem has gone read-only because of errors in it. The errors could be compounded by you trying to write to the filesystem, that's why it has been mounted read-only to prevent it from more damage.

Just run fsck on the affected filesystem; for instance if it's /dev/sda1 you would do:

```
sudo fsck /dev/sda1
```

You'll be asked about a bunch of things that should be fixed, just keep hitting 'y'.

Then reboot and you should be fine.

---

### Post by Maximus20 on 2010-07-12
Yes sorry i didn't read all the info provided when the error ocured :D...thank you very much .

---

