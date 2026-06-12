---
title: "How to move home directory to another ubuntu"
date: 2012-05-30
forum: General Help
---

### Post by sturdy on 2012-05-30
I have finally gotten AMD64 Precise installed on a new drive. I still have i386 Precise on an older drive. All Apps on the old drive have been installed in the AMD64 Precise. How can I move my Home directory to the new drive?

---

### Post by Habitual on 2012-05-30
```
rsync -avz source/ destination/
```

---

### Post by llamabr on 2012-05-30
rsync is a good bet.  you can also tar the whole thing, and then untar it in the right place.

---

### Post by raja.genupula on 2012-05-30
we have a GUI backup tool too , open system settings there you can find it .

---

### Post by sturdy on 2012-05-31
Thanks to all for the responses. I used rsync to copy the Home directory and it seems to be working. My real question which I forgot to ask is if the Home directories created by 32 and 64 bit systems are compatible? Or is there a config file or something waiting to blow up?

---

### Post by 0011235813 on 2012-05-31
> **sturdy said:**
> Thanks to all for the responses. I used rsync to copy the Home directory and it seems to be working. My real question which I forgot to ask is if the Home directories created by 32 and 64 bit systems are compatible? Or is there a config file or something waiting to blow up?

There is a lot of confusion with 32-bit and 64-bit floating around. The only thing you need to know is: executable binaries that are programmed to use address spaces with a bit greater than the host OS won't run. This only applies to executable binaries and not stuff like documents of videos.

Hope that cleared up the confusion.

EDIT: Can you mark this thread as solved?

---

### Post by sturdy on 2012-05-31
Thanks to all...I'm up and running.

---

