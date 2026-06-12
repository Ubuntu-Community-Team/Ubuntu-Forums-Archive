---
title: "backing method: raid 1 or just copy to other hd?"
date: 2009-10-02
forum: General Help
---

### Post by david90 on 2009-10-02
If you have to pick a method which would you choose?  What's a good backup program for ubuntu?

---

### Post by Lars Noodén on 2009-10-02
Copy to another HD, one that is removable.  If it's on the same machine, then it's not a backup.  That includes RAID.  What ever happened to the first disk can also happen to the second.  

RAID1 is there in case of physical failure of a drive.  You can choose to keep running for a while if one drive fails.  If you have hot-swap capability on the RAID1 components, then the defective drive can be replaced without stopping the system.  

rsync is a good option for backup.  It saves a lot of time and bandwidth by only copying the changes.  

```

rsync -a /home/david90/ /media/RemovableDisk/david90/

```

That will add all new files and transfer all new changes to the removable disk, assuming it's mounted at the path shown.

From time to time you may want to delete the files that don't exist on the original anymore:

```

rsync --delete -a /home/david90/ /media/RemovableDisk/david90/

# or
rsync --delete-after -a /home/david90/ /media/RemovableDisk/david90/

# or
rsync --delete-delay -a /home/david90/ /media/RemovableDisk/david90/

```

---

### Post by sedawk on 2009-10-02
Raid is redundancy, not backup ;-)

E.g when deleting your mp3 collection by accident (with
GUIs and focus in the wrong windows this can happen 
really fast with a few keystrokes in the wrong window)
a RAID will not help, but a backup disk that you
synchronize with rsync you can get back what you lost.

Typically a Ubuntu box doesn't include any or much
3rd party software by design (as most of the software
you need is in the repositories).
So I never bother do backup the OS itself, only my
data (e.g. /home) and a list of changes I might
have done to the OS (e.g as a changes.txt in your
home folder).

---

