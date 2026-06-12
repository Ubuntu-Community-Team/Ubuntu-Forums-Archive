---
title: "moving home directory"
date: 2010-06-29
forum: General Help
---

### Post by BarryDocks on 2010-06-29
really basic question but I can't seem to find the answer.  

I would like to move the /home directory to a different location, there only seem to be guides on how to move it to it's own partition.

I have a drive (/dev/sda5) mounted as /media/data

I would like to move /home to /media/data/home?

I have tried usermod but get the following error:
```

test@TestServer:/media/data$ sudo mkdir /media/data/home
test@TestServer:/media/data$ ls
home  lost+found
test@TestServer:/media/data$ sudo usermod -dm /media/data/home
usermod: user '/media/data/home' does not exist
```

HELP!!


Thanks

---

### Post by BarryDocks on 2010-06-29
solved this,

renamed original /home as /home_old
created new /home 

added to fstab:
/media/data/home /home none    defaults,bind 0 0

reload fstab (mount -a)

---

### Post by Chronon on 2010-06-30
I'm glad you figured it out.  Since it's solved could you mark it as such?

---

