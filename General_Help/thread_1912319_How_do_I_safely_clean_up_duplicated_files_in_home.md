---
title: "How do I safely clean up duplicated files in /home"
date: 2012-01-20
forum: General Help
---

### Post by SuperFreak on 2012-01-20
In the past I backed up my root partition and home partitions with a copy command suggested on another forum thread. I now find I have duplicate folder and files in /home/david and /home. I am worried that I am going to trash my system if I just start deleting files (some of which are locked) in /home.
screenshots attached

---

### Post by dcstar on 2012-01-20
> **SuperFreak said:**
> In the past I backed up my root partition and home partitions with a copy command suggested on another forum thread. I now find I have duplicate folder and files in /home/david and /home. I am worried that I am going to trash my system if I just start deleting files (some of which are locked) in /home.
screenshots attached

The **only** files in /home should be folders to valid user accounts and possibly a "lost+found" folder), the rest are rubbish.

Install the Nautilus gksu extension (and manual patch to make it work) and you can then delete files with root privileges:

[http://ubuntuforums.org/showthread.php?t=1861721](http://ubuntuforums.org/showthread.php?t=1861721)

---

