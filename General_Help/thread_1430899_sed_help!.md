---
title: "sed help!"
date: 2010-03-15
forum: General Help
---

### Post by blur xc on 2010-03-15
I'm writng a script, and I need to find and delete a line from a text file, one at a time while the script runs.  So, I've been reading up on sed usage- and I'm getting frustrated with my results.  

I created a directory - testdir, and in it I crated 10 empty files (touch file{1000..1010}.txt} to practice on.  Then I created a text file (ls -l > list.txt).

```
cat list.txt
total 8.0K
drwxr-xr-x 2 barna barna 4.0K 2010-03-14 23:32 .
drwxr-xr-x 3 barna barna 4.0K 2010-03-14 23:19 ..
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1000.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1001.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1002.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1003.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1004.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1005.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1006.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1007.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1008.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1009.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1010.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:37 list.txt
```then- the sed command gives me this:
```
sed '/file1000.txt/d' list.txt
total 8.0K
drwxr-xr-x 2 barna barna 4.0K 2010-03-14 23:32 .
drwxr-xr-x 3 barna barna 4.0K 2010-03-14 23:19 ..
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1001.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1002.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1003.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1004.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1005.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1006.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1007.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1008.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1009.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:32 file1010.txt
-rw-r--r-- 1 barna barna    0 2010-03-14 23:37 list.txt
```which looks good. But when I redirect the output back into the original file I get an empty file, as if all lines are deleted:
```
sed '/file1000.txt/d' list.txt > list.txt
cat list.txt
```I get nothing.  I'm googling, ran across a site that shows pretty much the same thing, yet when I do it, all lines go away, not just the one I need to go away.

If I redirect into a new file like list2.txt, it looks good.  But I can't keep creating a new file every time my script runs.

What am I doing wrong?

Thanks,
BM

---

### Post by blur xc on 2010-03-15
I guess I thew in the towel too early.  The -i option is what I wanted...

BM

---

