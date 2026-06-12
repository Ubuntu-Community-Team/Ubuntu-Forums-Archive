---
title: "remove repeats in text file"
date: 2011-07-05
forum: General Help
---

### Post by conradin on 2011-07-05
Hi all, 
I have 2 lists of names, they aren't sorted, and may contain repeats.
What I would like to do with a bash script is compare the 2 documents and find and remove each repeat name, saving only one of them. Then concatenate the files. Or if it were easier, concatenate first and find and remove all internal repeats.

---

### Post by dino99 on 2011-07-05
[http://www.addictivetips.com/ubuntu-linux-tips/clean-up-ubuntu-remove-duplicates-with-fslint-filesystem-lint/](http://www.addictivetips.com/ubuntu-linux-tips/clean-up-ubuntu-remove-duplicates-with-fslint-filesystem-lint/)

[http://www.ubuntugeek.com/how-to-find-duplicate-copies-of-files-using-fdupes-in-ubuntu.html](http://www.ubuntugeek.com/how-to-find-duplicate-copies-of-files-using-fdupes-in-ubuntu.html)

[http://ubuntuforums.org/showthread.php?t=647883](http://ubuntuforums.org/showthread.php?t=647883)

---

### Post by WorMzy on 2011-07-05
```
cat list1 list2 | sort | uniq > list3
```

---

### Post by hawthornso23 on 2011-07-05
Very elegant Wormzy

---

### Post by conradin on 2011-07-05
> **WorMzy said:**
> ```
cat list1 list2 | sort | uniq > list3
```

I love it!! Worked perfect!

---

### Post by sisco311 on 2011-07-05
```
sort -u file1 file2
```

---

