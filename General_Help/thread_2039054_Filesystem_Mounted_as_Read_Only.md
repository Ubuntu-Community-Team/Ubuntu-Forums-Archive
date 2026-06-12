---
title: "Filesystem Mounted as Read Only"
date: 2012-08-08
forum: General Help
---

### Post by Orcris on 2012-08-08
I was just doing normal web browsing, and I suddenly started getting error messages because I didn't have permission to write to my disk. I booted into recovery mode and tried typing ```
chown -R me:me .
``` in my home directory, but I got the same error. Right now, I'm posting this from a live CD I have lying around, and I'm in the process of backing up my drive. How do I fix this?

---

### Post by steeldriver on 2012-08-08
To remount the filesystem as read-write from within recovery mode you can do

```
mount -o remount,rw /
```*note there is no space between remount and rw

HOWEVER I can think of no good reason why your home dir ownership would spontaneously change so it sounds like you have other issues - maybe a failing disk? or your filesystem full or damaged?

Also DON'T do use the relative path '.' to change ownership in recovery mode - you won't be in your user home dir and it will screw up system permissions. If you still think you have an ownership problem you should do

```
chown -R you:you /home/you
```

---

### Post by dcstar on 2012-08-08
> **Orcris said:**
> I was just doing normal web browsing, and I suddenly started getting error messages because I didn't have permission to write to my disk. I booted into recovery mode and tried typing ```
chown -R me:me .
``` in my home directory, but I got the same error. Right now, I'm posting this from a live CD I have lying around, and I'm in the process of backing up my drive. How do I fix this?

Filesystems are mounted RO when they are damaged.

Use the Live CD to do a fsck on the partition (or use the Disk Utility).

---

### Post by Orcris on 2012-08-08
I ran an fsck, and it seems like it fixed the problems. What types of things could corrupt my disk?

---

