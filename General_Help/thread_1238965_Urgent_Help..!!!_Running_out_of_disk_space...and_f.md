---
title: "Urgent Help..!!! Running out of disk space...and fast"
date: 2009-08-13
forum: General Help
---

### Post by madhavhmk on 2009-08-13
I have only about 30 MB left on my linux partition....with each booting it seems to get smaller....


Someone kindly help me out by telling me which files i can safely delete, inside system folders(temporary files) without causing turmoil...


I dont have any music, video or other files in linux partition except sytem files and installed packages...

in the meantime I have to figure out how I can add some space by freeing memory from windows partition....

Thanks

---

### Post by akudewan on 2009-08-13
Try this in a terminal:
```

sudo apt-get clean

```

That should clean the apt-get cache. It may provide temporary relief.

---

### Post by madhavhmk on 2009-08-13
I typed in that....but it seems it has not done considerably good in getting more free space...:(
But thanks....for me, every bit is counting...!

---

### Post by QIII on 2009-08-13
How large is the partition?

Do you have a proper Linux partition (i.e.: dual boot) or a Wubi installation?

---

### Post by Yvan300 on 2009-08-13
Check your trash folder :)

---

