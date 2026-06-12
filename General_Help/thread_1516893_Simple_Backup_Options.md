---
title: "Simple Backup Options"
date: 2010-06-24
forum: General Help
---

### Post by gvernold on 2010-06-24
I'm running Ubuntu 10.04 32 bit on a machine that we use as a casual server. When I mean casual I mean that it gets switched on and off once a day, runs Samba and provides us with file storage. We now have a second hard drive that we want to use as backup (not redundancy so RAID is no good).

What we want to be able to do is set up a partition on the new drive the same size as the data partition on the first one. Then when a file is written to, or deleted or whatever it just repeats the process onto the second drive so the partition is just like an identical image to the first. Yes, I know this sounds like RAID but I don't want to be bothered with setting all that up and I need to be able to easily remove the second drive about once a month to offload to another machine.

Either that, or a solution that will just backup changes made to the first drive during the day and automatically runs, say at 5pm each evening.

Each time I have checked a backup utility it goes on about incremental backups, complete backups, compression etc. Not sure what I need really but I want straight copies of all the files on the first drive and not everything compressed up into a single file.

Thanks for any responses.

---

### Post by ajgreeny on 2010-06-24
It sounds as if **unison** is the application you need, as it will sunc across two drives very well, and you should be able to cron the use to once a day, or whatever you want.  Unison is in the repos.

---

### Post by huwjenjinn on 2010-06-24
I've set up **rsync** to do something very similar for myself, the difference being I'm manually calling the back up after specific changes. Am impressed with it and it's hugely configurable if you like the command line.

An example would be:
```
rsync -rvt --modify-window=1 --update --exclude '*.db' /home/enjinn/Pictures/. /"media/My Book/My Pictures"/.
```

Which backs up my Pictures folder onto a mirrored structure on my external USB HD. It doesn't remove files, ever, from the USB HD it just adds new ones, except for files ending with db.

---

### Post by gvernold on 2010-06-28
Thanks guys, I'm just trying both methods to see which is more suitable. Unison seems pretty decent though and fairly close to what I need, however there is more help online with rsync.

Thanks again.

---

### Post by gvernold on 2010-06-28
Thanks guys, I'm just trying both methods to see which is more suitable. Unison seems pretty decent though and fairly close to what I need, however there is more help online with rsync.

Thanks again.

---

