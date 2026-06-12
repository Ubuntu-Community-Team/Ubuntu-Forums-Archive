---
title: "Disk Usage Analyzer missing data"
date: 2011-05-01
forum: General Help
---

### Post by quantumriff on 2011-05-01
I am attaching a screenshot, but I have recently upgraded from 10.10 to 11.04.. Recently, I got a warning that I was running low on HD space.  I emptied the trash (I had about 20GB in there, mostly old virtual machines).  However, looking at disk usage analyzer, My home directory is adding up to 235GB, but if you look at the folders and files, they only add up to about 40% of that.

df shows my hard drive as 93% full as well, so both tools are showing its getting full, which is stange, I recently moved from a 160GB drive that was 80% full..

How can I find what to delete, when disk usage analyzer isn't even giving me useful info?

---

### Post by blueridgedog on 2011-05-01
du --max-depth=1 | sort -g will show directory sizes small to large.  So to investigate your home directory issue:

```
cd /home
sudo du --max-depth=1 | sort -g
```

From there, look at the sizes and keep cd'ing into suspect directories and running the same command until you find the issue.

---

### Post by antaios256 on 2011-05-01
> **quantumriff said:**
> I am attaching a screenshot, but I have recently upgraded from 10.10 to 11.04.. Recently, I got a warning that I was running low on HD space.  I emptied the trash (I had about 20GB in there, mostly old virtual machines).  However, looking at disk usage analyzer, My home directory is adding up to 235GB, but if you look at the folders and files, they only add up to about 40% of that.

df shows my hard drive as 93% full as well, so both tools are showing its getting full, which is stange, I recently moved from a 160GB drive that was 80% full..

How can I find what to delete, when disk usage analyzer isn't even giving me useful info?

i never really used the disk usage analyzer i found the best disk usage was 


```

df -h

```

---

### Post by quantumriff on 2011-05-01
There was a file /home/brian/.gvfs that was owned by ???.  I could not look at it even as root (nor could I CHown, or Chmod it).

I rebooted into "recovery mode" and opened a root shell, and deleted the file manually. (its part of gnome).  My Home folder now shows 120GB less space being used, and the numbers add up now

---

