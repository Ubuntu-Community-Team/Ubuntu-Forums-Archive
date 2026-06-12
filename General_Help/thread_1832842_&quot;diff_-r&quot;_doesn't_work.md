---
title: "&quot;diff -r&quot; doesn't work?"
date: 2011-08-25
forum: General Help
---

### Post by CryptKeeper777 on 2011-08-25
I have three folders, let's call then folderA, folderB1 and folderB2. I want to compare the subfolder structure of folderA to that of folderB1 and folderB2 together to find out which subfolders are in folderA, but neither in folderB1 nor in folderB2. Google told me to use die command "diff" to compare folders, but it only takes two folders as input. So I made a new folderB in which I put a symlink to the two folderBs using "ln". That also worked, the command "tree -dl folderB" for example shows what it should.

But "diff -r folderA folderB" doesn't. It's output is like this:
```
Only in folderA: xxx1
Only in folderA: xxx2
...
Only in folderB: folderB1
Only in folderB: folderB2
```That's the same output as without "-r". Diff doesn't seem to follow the symlinks. But there are also subfolders in the xxx-folders, these should be displayed when I use "-r", but they aren't, so I assume the problem isn't so much the symlinks as rather that diff doesn't go recursively into the folder structures.

The diff-command doesn't seem to work correctly on my computer!

---

### Post by gmargo on 2011-08-25
**diff(1)** expects to find files at identical paths in each directory. You have to diff each "B" directory separately.

> 
I want to compare the subfolder structure of folderA to that of folderB1  and folderB2 together to find out which subfolders are in folderA, but  neither in folderB1 nor in folderB2.
Here's one way to do it.  (However this will show files as well as directories.)

```

# create test directories
$ mkdir -p folderA/{xxx1,xxx2,xxx3,xxx4}
$ mkdir -p folderB1/{xxx1,xxx2,xxx5}
$ mkdir -p folderB2/{xxx1,xxx3,xxx6}

# Diff folderA against each of the Bs
$ diff -r folderA folderB1 | sort | tee AtoB1.out
Only in folderA: xxx3
Only in folderA: xxx4
Only in folderB1: xxx5

$ diff -r folderA folderB2 | sort | tee AtoB2.out
Only in folderA: xxx2
Only in folderA: xxx4
Only in folderB2: xxx6

# Show common lines of each difference, which is the same
# as "subfolders of A that are not in B1 or B2".
$ comm -12 AtoB1.out AtoB2.out
Only in folderA: xxx4


```

---

