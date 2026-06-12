---
title: "How do I find put the mount path of a folder"
date: 2010-08-22
forum: General Help
---

### Post by lmicu on 2010-08-22
I mean I have a folder on my root /share and I want to find out how much free space do I have left on the hdd, problem is I have 4 HDD and I don't know if /share is mounted on / or where ..... what is the command line?

---

### Post by lmicu on 2010-08-22
df /share

---

### Post by WorMzy on 2010-08-22
To find out where everything is mounted you have a couple of options. You can look at mtab:
```
cat /etc/mtab
```

Or you can run:
```
mount -l
```

Both show essentially the same thing, with a couple differences.

Once you know where the partition is mounted, you can analyse it with baobab.

e.g.
```
baobab /media/Windows
```

---

