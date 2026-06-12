---
title: "Help on Command Line!!!"
date: 2009-12-11
forum: General Help
---

### Post by Uncas on 2009-12-11
I'm using a rescue Remix on a friends computer. The machine has Vista and it's not booting up. I believe the boot sector is damaged, because the data is still there. I formated the computer not long ago and the disk SMART indicator said the disk was failing.
 
Her user on Vista is composed of two names (i.e. Jack Black), I was able to mount the disk and go to the users folder, but when I go cd Jack Black it says
 
"-bash: cd: Jack: No such file or directory"
 
Any ideas on how to get into that folder?
 
Thanks.

---

### Post by Physical Hook on 2009-12-11
```
cd "/media/somewhere/Jack Black/"

```

---

### Post by i.r.id10t on 2009-12-11
cd Jack\ Black 

or

cd "Jack Black"

---

### Post by Uncas on 2009-12-11
Thanks...

---

