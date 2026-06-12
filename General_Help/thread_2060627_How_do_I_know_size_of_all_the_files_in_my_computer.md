---
title: "How do I know size of all the files in my computer?"
date: 2012-09-20
forum: General Help
---

### Post by arroy_0209 on 2012-09-20
I want to know the size of all files (including the operating system (ubuntu10.04LTS) files, other installed program files  and my personal files) in my computer. How do I do that?

---

### Post by GreatDanton on 2012-09-20
Size of the files: open up System Monitor, and click on File System tab. You should see how much space is used, and how much is available.

Hope this helps.

---

### Post by oldfred on 2012-09-20
I find some of the gui tools include other mounted partitions in the total. 

You can also do this:
# check sizes of 
Partition sizes
df -Th | sort
Inodes:
 df -i
cd / or cd /home
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null

---

### Post by BrianBlaze on 2012-09-20
```

cd /
du -h

```

... lol

---

### Post by f8l_0e on 2012-09-20
+1 for du -h .. but if you want a quick overview of the whole filesystem, I like the disk usage analyzer utility.  

```
sudo apt-get install baobab
```

Then look for the disk usage analyser from the ubuntu menu.

---

