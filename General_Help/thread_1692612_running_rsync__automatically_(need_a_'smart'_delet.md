---
title: "running rsync  automatically (need a 'smart' delete)"
date: 2011-02-21
forum: General Help
---

### Post by afrodocter on 2011-02-21
i want to keep two directories in sync automatically using rsync.

i know how to use rsync to push up changes and pull down changes, but there is a problem when i delete a file, and it gets pushed or pull back from the older copy. using the --delete flag is not sufficient, because then order matters. 

can rsync know the difference between a file which has been deleted vs 'not created yet'? 

thanks 
alex

---

### Post by cjhabs on 2011-02-21
> **afrodocter said:**
> i want to keep two directories in sync automatically using rsync.

i know how to use rsync to push up changes and pull down changes, but there is a problem when i delete a file, and it gets pushed or pull back from the older copy. using the --delete flag is not sufficient, because then order matters. 

can rsync know the difference between a file which has been deleted vs 'not created yet'? 

thanks 
alex

I don't know if that can be done, but how about syncing both folders through Dropbox, which can do that.

---

### Post by afrodocter on 2011-02-22
after some more research it doesnt seem like rsync has this capability. 

the main problem is that a there needs to be a way to determine if a file was created **since** the last synchronization, and to my knowledge, rsync doesnt have this ability. 


it appears that the program 'unison' is the most popular choice for this functionality.

---

