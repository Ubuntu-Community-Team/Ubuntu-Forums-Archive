---
title: "incremental tar backup"
date: 2010-05-18
forum: General Help
---

### Post by stevepoppers on 2010-05-18
This is my scheduled command:

```
tar -cvpjf /media/external2/backups/$(date +\%a)/$(date +\%a).tar -g /media/external2/backups/$(date +\%a)/$(date +\%a)_log /home/anthony /etc
```

I made an initial backup on Monday, let it sit overnight. I checked it this morning and it ran, but the Tuesday backup is empty. I suspect it has backed up incremental changes. It shouldn't though, because I'm not referencing the same meta file that I did on Monday, a la the date thingy.

I hope it's obvious what I'm trying to do and how I have it set up.

Why did what happened happen?

---

### Post by stevepoppers on 2010-05-19
Still happening...

---

### Post by stevepoppers on 2010-05-21
Hey, whaddya know? Still happening.

---

### Post by john newbuntu on 2010-05-21
A few things to look into:
1. A new directory gets created every day in the destination.  Does this exist?  If not that could be a problem.
2. Is this command run from cron?  If so, how is it being run? Please capture the stderr and have a look at it.  Also check return code from tar.

---

### Post by stevepoppers on 2010-05-21
A directory exists for every day of the week, named appropriately. The .tar and meta files are being created. They just don't contain anything.

I believe it is being run through cron, but I used the GUI, "Scheduled tasks" so the finer details of cron are over my head at the moment. I'll look into whatever I need to.

Thanks for the reply.

---

