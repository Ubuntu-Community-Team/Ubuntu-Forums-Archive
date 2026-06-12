---
title: "Backing up files to external hard drive"
date: 2010-02-06
forum: General Help
---

### Post by thecliff on 2010-02-06
What is the recommended way to backup all files to an external hard drive?  Should it be done through CLI or should a third party program be used?

---

### Post by switch10 on 2010-02-06
I use rsync.  But you can also just use cp.  I don't like using any kind of GUI when I move large amounts of files.  I think there is a better chance of something crashing when using GUI.  CLI always has been smooth for me.

type this to see what rsync does:
```
 man rsync 
```

---

### Post by thecliff on 2010-02-06
Worked great for backing up the data I wanted.  

As simple as

```
rsync -a /home/... /media/...
```

**Thanks**

---

