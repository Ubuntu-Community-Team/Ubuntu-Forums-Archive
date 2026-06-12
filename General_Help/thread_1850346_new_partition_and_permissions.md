---
title: "new partition and permissions"
date: 2011-09-26
forum: General Help
---

### Post by liquidmonkey on 2011-09-26
i have just created a new partition in 11.04, so have one that is 80gig and another that is 30gig.

the new partition (30gig) will not let me create a new folder or copy anything to it.

i have a feeling its a permissions thing but not aware how to allow myself to do these things.


any ideas?


and one more thing, its a newly created partition BUT ALREADY SHOWS 1.7gigs as being used???!?!!?

used for what? and why is there a lost and found folder already?


thanks!

---

### Post by TeoBigusGeekus on 2011-09-26
Change the ownership of its mount point.
```
sudo chown -R yourusername: /media/name_of_mount_point
```

---

### Post by liquidmonkey on 2011-09-26
> **TeoBigusGeekus said:**
> Change the ownership of its mount point.
```
sudo chown -R yourusername: /media/name_of_mount_point
```



genius!
thank you!


and any idea why there is already 1.7gigs of space taken?
i could understand 100megs or so but 1.7GIG is alot :(

---

### Post by SlugSlug on 2011-09-26
sudo du -sch  /media/name_of_mount_point

---

### Post by TeoBigusGeekus on 2011-09-26
Probably the lost and found folder; don't worry too much about it, I think the space will be released if you want to use it.

---

