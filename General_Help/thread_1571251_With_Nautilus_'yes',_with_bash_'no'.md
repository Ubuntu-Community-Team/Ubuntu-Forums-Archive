---
title: "With Nautilus 'yes', with bash 'no'"
date: 2010-09-09
forum: General Help
---

### Post by luigi_mb on 2010-09-09
I have been using an external USB drive (LaCie 360GB). Suddenly, while the drive behaves perfectly with Nautilus, I have all sorts of problems in the console. For example, 

```

$ ls -al /media/LACIE360

```

yields

```

ls: cannot access /media/LACIE360: No such file or directory

```

Sometimes the above commands yields only the "." and ".." folders, but no subfolders. 

Notice that any other USB drive, plugged into the same port, works fine with both Nautilus and bash. 

Notice also that on another machine, running the same OS (Lucid), equally up-to-date, the drive is perfectly accessible from the console.  

I used gparted, and "checked" the drive. Everything is ok, except that it offered to try to expand the partition, but concluded that it was already the largest possible.

Any suggestion will be greatly appreciated.

/luigi

---

### Post by luigi_mb on 2010-09-09
More info. With the drive plugged in, /media shows three entries:

drwxrwxrwx  2 luigi luigi 4096 2010-09-07 14:43 LACIE320
drwx------  2 root  root  4096 2010-09-08 21:12 LACIE320_
drwxr-xr-x 30 luigi luigi 4096 2010-06-15 14:44 LACIE320__

I can access the drive, in the console, normally as in the past, using the third entry. 

What I would like to do now is remove the first two, and rename the third from "LACIE360__" to "LACIE360". 

Is this advisable?

Would the change have any effect on Nautilus?

Thank you for any help.

/luigi

---

### Post by silverglade00 on 2010-09-09
I think I had this happen when I yanked the plug on an external drive too quickly. You should be able to fix it by disconnecting the drive. Make sure the drive is disconnected. Look again to make sure there is at least 3 meters between the end of the drive's USB plug and your computer in case of freak lightning arcs. Ok, now that fun time is over and your data is relatively safe, just delete the three directories as root. ```
sudo rm -rf /media/LACIE32*
``` Then plug your drive back in and it should automatically pick it up as /media/LACIE320 again.

---

### Post by luigi_mb on 2010-09-09
> **silverglade00 said:**
> I think I had this happen when I yanked the plug on an external drive too quickly. You should be able to fix it by disconnecting the drive. Make sure the drive is disconnected. Look again to make sure there is at least 3 meters between the end of the drive's USB plug and your computer in case of freak lightning arcs. Ok, now that fun time is over and your data is relatively safe, just delete the three directories as root. ```
sudo rm -rf /media/LACIE32*
``` Then plug your drive back in and it should automatically pick it up as /media/LACIE320 again.

Thank you! Indeed just before reading your reply, I had unmounted the drive and (sudo) renamed the 'bad' items LACIE320 and LACIE320_ to LACIE320.bad and LACIE320_.bad respectively. When I plugged the drive back in, the drive was recognized, and I could access it as usual from the console.

I am not sure how all this happened, since I always, religiously use "ejecter" to safely unmount all my external drives. 

Thank you again. I guess this thread should be marked "solved".

/luigi

---

