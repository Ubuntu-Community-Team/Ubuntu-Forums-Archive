---
title: "badblocks output format"
date: 2012-08-29
forum: General Help
---

### Post by mkljun on 2012-08-29
Hi,

My external hard drive went nuts and I'm running badblocks command on it. The problem is I can not find what the output of the command means. 

This is a part of it:

```
desktop ~ $ sudo badblocks -v /dev/sdb1 | tee bad-blocks
[sudo] password for jast:
Checking blocks 0 to 976074751
Checking for bad blocks (read-only test): 3202944 done, 1:47 elapsed
3203004 done, 1:52 elapsed
3203005 done, 1:55 elapsed
3203006 done, 1:57 elapsed
3203007 done, 2:00 elapsed
3203056 done, 2:05 elapsed
3203057 done, 2:07 elapsed
3203058 done, 2:10 elapsed
3203059 done, 2:12 elapsed
3203496 done, 2:15 elapsed
3203504 done, 2:20 elapsed
3203505 done, 2:22 elapsed
3203506 done, 2:25 elapsed
3203507 done, 2:27 elapsed
3203516 done, 2:32 elapsed
3203517 done, 2:35 elapsed
3203518 done, 2:37 elapsed
3203519 done, 2:40 elapsed
3203536 done, 2:45 elapsed
3203537 done, 2:48 elapsed
3203538 done, 2:50 elapsed
3203539 done, 2:53 elapsed
508814344one, 4:58:13 elapsed
508814388one, 4:58:18 elapsed
508814389one, 4:58:20 elapsed
508814390one, 4:58:23 elapsed
508814391one, 4:58:25 elapsed 
```


Are the numbers in each line the numbers of badblocks? And what is that "done" there?

Thanks

---

### Post by dcstar on 2012-08-30
> **mkljun said:**
> Hi,

My external hard drive went nuts and I'm running badblocks command on it. The problem is I can not find what the output of the command means. 
.......

```
man badblocks
```

---

### Post by mkljun on 2012-08-30
Thx .. but unfortunately the man pages say nothing about the output format.

At the very end (after 9 hours of running) it wrote:

```
done
Pass completed, 27 bad blocks found
```

So every line such as

```
92349553 done, 4:45:23 elapsed
```

means the number of a found bad block and the time elapsed from starting the command.

This is solved now.

m

---

### Post by ethanm97 on 2012-08-30
If you want to stop the drive from using the bad blocks, then try running
```
e2fsck -c
```
This will prevent data from being stored on these blocks.
Check [http://en.wikipedia.org/wiki/Badblocks](http://en.wikipedia.org/wiki/Badblocks)

---

