---
title: "How do i copy all of my files using shell"
date: 2011-02-16
forum: General Help
---

### Post by Zaytoven on 2011-02-16
well my drive has errors where i can't mount it using a GUI but it will mount and let me see my files using shell or w/e it is that i'm using while in recovery mode. I have manage to change my directory to the one that has ALL of the files that i want and need to copy. I was wondering whats the easest way to copy ALL of the files which are like 20 GB onto my 500 GB external HDD? and How will i know everything is done copying?

---

### Post by sanderd17 on 2011-02-16
the easiest command is the cp command
```

cp /source/* /target

```
 will copy all the files from the source directory to the target directory.

to compare the 2, use diff with ls commands:

```

diff <(ls /source) <(ls /target)

```
if you get no output, everything is copied. Otherwise, diff will tell you what files are in one but not in the other direcotry.

---

### Post by iponeverything on 2011-02-16
giving cp the -a option will get it to also pick up the subdirectories.

---

