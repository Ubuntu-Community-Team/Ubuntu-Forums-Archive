---
title: "partitions shared betwwen computers"
date: 2009-06-30
forum: General Help
---

### Post by yanivgo on 2009-06-30
HI all
newbie here :)
have 3 partitions on my machine
one holds XP 
second holds ubuntu 9.04
third is a shared partition formated to ntfs
when booting to ubuntu i want to be able to see my shared partition on other computers on my network runing windows
can't find the correct way to do it
your help is highly appreciated

---

### Post by kixome on 2009-06-30
Put a folder on the partition named shared, or whatever you want to see from the other comps, and then right click on it and click sharing options, after you share it you will need to restart the computer.

---

### Post by kixome on 2009-06-30
You may even have to re-share it if your sharing service isnt installed by default, after you restart.

---

### Post by yanivgo on 2009-06-30
Thanks kixome
Can't I share the root of the partition?

---

### Post by kixome on 2009-06-30
Yes, but it is a very dangerous thing to do. You would have to actually share the mount point, i.e. /media/whatever_mount_point_for_your_drive

---

### Post by kixome on 2009-06-30
your mountpoint doesnt have to be in /media, just type mount in a terminal and you will see where your drives are mounted

---

### Post by yanivgo on 2009-06-30
OK so here is what I did
using sudo nautilus I changed the share options to the entire volume at the mountpoint (media)
this works good and now I able to see read and write to my shared partition from other machines on my network.
I'll be happy to know why is that a security issue since I only shared the partition containing docs I want to share and there is no access to critical data or to other parts of the filesystem
thanks for your patience

---

