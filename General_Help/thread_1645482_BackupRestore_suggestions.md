---
title: "Backup/Restore suggestions?"
date: 2010-12-14
forum: General Help
---

### Post by ventrical on 2010-12-14
I would like to hear of some suggestions on backing up /home/ files etc for a back-up session so that if I get the so called 'black-screen' I can then do a restore without having to reconfigure my whole system. so far Ubuntu 10.4 and 10.10 have worked excellently off the update manager but I would just like to be prepared in case I do get a system crash.

any ideas on the best Open source software for this task .. and tips and tricks??

thanks

---

### Post by Ocxic on 2010-12-14
just copy your home folder to your backup device.
rsync will work nicely for doing incremental backups.

---

### Post by Foxheadz on 2010-12-14
I use deja dup backup tool. it's in the software center

---

### Post by Dex73 on 2010-12-14
> **Ocxic said:**
> just copy your home folder to your backup device.
rsync will work nicely for doing incremental backups.

I can confirm this... rsync will take the same amount of time to back everything up the first time, but then when you need to use it again, it only copies the changes.(much faster!)  There is also a really good GUI interface for it called Luckybackup if you don't like the command line. Plus, with Luckybackup, you can save that process of backing up files e.g. where directory is to be copied from is located, where the directory to be copied to is located, and then name it something like "BACKUP"

It really does work great!

---

### Post by ventrical on 2010-12-14
Ok..so I do a back-up of my home folder to my back-up device. Then, if my system crashes then how do I restore it ?

---

### Post by Foxheadz on 2010-12-14
Well deja dup has two buttons backup and restore pretty self explanatory but i guess drag home folder onto your home folder and press replace

---

### Post by ventrical on 2010-12-15
Ok.. you guys are great.. but I have a few more questions. Like how do I back up all the updates that I did and all the programs and settings. I looked in the /home/ folder and there is hardly nothing there.

 When I do a back-up does that mean that it will not backup all of my settings and updates and that if I have to do a fresh install that I will have to do all the updates over again??

---

