---
title: "Error when mounting NTFS drive"
date: 2010-08-28
forum: General Help
---

### Post by Gizim on 2010-08-28
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdc1 is already mounted on /
mount failed

Not sure what happened but it worked fine till last reboot :-/
It's a 250g NTFS drive named MEDIA device /dev/sda1
Not sure what happened or why it won't mount now.

---

### Post by Lars Noodén on 2010-08-29
If you get your data back, give consideration to using a sounder filesystem like EXT, JFS, or HFS.   

NTFS is really not advisable to use for anything except trouble.

---

### Post by QLee on 2010-08-29
[QUOTE=Gizim]Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sdc1 is already mounted on /
mount failed[/QUOTE]

You didn't tell us anything about the situation under which this error occurred but note that the error states /dev/sdc1 is already mounted so you must have tried to mount sdc1.

[QUOTE=Gizim]Not sure what happened but it worked fine till last reboot :-/
It's a 250g NTFS drive named MEDIA device /dev/sda1
Not sure what happened or why it won't mount now.[/QUOTE]

Note you state /dev/sda1 is the one that won't mount but that isn't the one the error message refers to.

Can you explain a bit better what it is you are trying to do? Probably a good idea to tell what you were trying to do just before a problem occurred too if you changed something.

---

### Post by Mark Phelps on 2010-08-29
> **Lars Noodén said:**
> If you get your data back, give consideration to using a sounder filesystem like EXT, JFS, or HFS.   

NTFS is really not advisable to use for anything except trouble.

OK, so everyone is entitled to their own opinion ... but like many others, I've been using NTFS volumes to share files between MS Windows and Linux distros for YEARS, and have YET to encounter ANY problems at all!!

---

### Post by jerome1232 on 2010-08-29
In that error your either attempting to mount you ntfs drive as / which is what sdc1 is mounted as, or you not actually attempting to mount your ntfs drive your attempting to mount sdc1.


What is actually going on, is this an error happening at boot up and you have your ntfs drive in your fstab?


More details, also a list of partitions and your fstab would probably be useful, as well as where everything is mounted now. The output of the commands below along with more details of what's going on and what your doing to get that error message would help alot.

```
cat /etc/fstab
mount
sudo fdisk -l
```

---

