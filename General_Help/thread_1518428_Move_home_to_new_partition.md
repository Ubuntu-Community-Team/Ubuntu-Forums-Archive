---
title: "Move home to new partition"
date: 2010-06-26
forum: General Help
---

### Post by Vexiphne on 2010-06-26
I've read some tutorials on how to move my home to another partition and I'm soooo confused. Is it really that hard? Everything I've tried has failed and I've had to re install ubuntu like 5 times now. :frown: 

Is there an easy way to move home to another partition. Like a tool I can use? Or maybe a tutorial for beginners? [-o<

---

### Post by arrange on 2010-06-26
Can you give us more details? Provide a screenshot from GParted or the output of ```
sudo fdisk -l
```and then explain what you want to achieve.

---

### Post by dabl on 2010-06-26
Depending on what you want to do, it may be easier to make data folders on the new partition, and symlink them in to the existing /home/user folder.

The new partition, after being formatted, can be set up in /etc/fstab to be mounted at boot time.  Then you can make a folder or folders (directories) on it, name them something useful like "MYPICS" or "MYMUSIC", give them your user's permissions, and link them in so you can see and use them in your user folder.

---

### Post by ajgreeny on 2010-06-26
> **Vexiphne said:**
> I've read some tutorials on how to move my home to another partition and I'm soooo confused. Is it really that hard? Everything I've tried has failed and I've had to re install ubuntu like 5 times now. :frown: 

Is there an easy way to move home to another partition. Like a tool I can use? Or maybe a tutorial for beginners? [-o<
When you re-installed, that would have been the time to make a separate /home partition.  As you must have all your personal files backed up already, in order to have done the re-install, do it now.

See [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome) for the best detailed tutorial.

---

### Post by Vexiphne on 2010-06-26
After several hours of searching I found the solution and it Worked :D

I found this [https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

---

### Post by jmszr on 2010-06-26
Vexiphne,

If you haven't already tried this link: [http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html](http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html) it seems to be pretty straightforward.
 If any part of it doesn't make sense to you please ask and someone will be able to answer your question(s).

---

