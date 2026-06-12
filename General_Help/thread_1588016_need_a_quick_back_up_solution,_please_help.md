---
title: "need a quick back up solution, please help?"
date: 2010-10-04
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-04
I need to find a back up software for specific needs. I would love to use rsync, but i have no time at this point. Basically I have 3 drives. One drive holds the operating system, another contains a folder with important data and the final drive is a back up of that folder with the important data.

So to be more specific, I have this directory, containing important data:

/media/DATA-2TB/Important/

and I want to constantly have a mirror of those files in location:
/media/BU-2TB/Important/

Now, what i need is a mirror of the first location, in the second location. I need the program to constantly check (like every 24 hours) for differences.

Also an important point, I have already made a copy to the back up destination, so i want the software to take this into account.

I tried using back-in-time but it seems to create snapshops (copies) of it everytime it does a check. That's wasting space for me. Thanks for the help!

---

### Post by SaintDanBert on 2010-10-04
Use google(tm) to locate **LuckyBackup**.

L/B is a front-end or wrapper for an rsync-based backup and recovery.
Usage is very straight forward so your rush to use requirement gets met. GUI on top of rsync means that the data integrity is sound as the underlying target file systems.

Bonne Chance,
~~~ 0;-Dan

---

### Post by CrusaderAD on 2010-10-04
Check out Keep.

```
sudo apt-get install keep
```

---

### Post by HermanAB on 2010-10-04
Make this file with a text editor:

#! /bin/bash
rsync -av /media/DATA-2TB/Important/ /media/BU-2TB/Important/

Make it executable and put it in /etc/cron.daily

---

### Post by Irony on 2010-10-04
> **HermanAB said:**
> Make this file with a text editor:

#! /bin/bash
rsync -av /media/DATA-2TB/Important/ /media/BU-2TB/Important/

Make it executable and put it in /etc/cron.daily

To make the second file the same as the first I would do;

```
rsync -av --delete /media/DATA-2TB/Important/. /media/BU-2TB/Important/.
```

In other words this doesn't add to the backup but deletes anything in the backup that has been deleted in the original - the choice really depends on whether you want an exact copy or prefer the backup to be added to.

---

### Post by SaintDanBert on 2010-10-04
> **Irony said:**
> 
...
In other words this doesn't add to the backup but deletes anything in the backup that has been deleted in the original - the choice really depends on whether you want an exact copy or prefer the backup to be added to.

This presumes that you want to maintain two identical copies of a folder tree.

Another expectation of "backup copies" involves taking a snapshot or check-point of everything I have RIGHT NOW.  At some future point, I want to return to that snapshot and find everything regardless of what I might have deleted or changed (or damaged) in the interim. Some say that this behavior is more "archival" than "backup."

~~~ 0;-Dan

---

