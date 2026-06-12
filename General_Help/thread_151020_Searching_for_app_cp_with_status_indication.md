---
title: "Searching for app: cp with status indication"
date: 2006-03-27
forum: General Help
---

### Post by TLE on 2006-03-27
Hi everyone.
I was wondering if any of you know a commanline application like cp but which also have a status indication off how far along in the copying it is (I have a lot of DVD's with 6-10 big files on them which I occassionably copy to my harddrive). 
I did actually, just for the fun of it, wirte a bash script to do this, which works quite fine but it is lacking options, most importantly the -r option.
Thnaks in advance, Regards TLE

PS: I found it difficult to search for this because searching, synaptic, the forum, the web or webpage with Linux apps, for words like "copy, cp, status" gives A LOT of hits but if I have missed an obvious way to find this plase let me know so that I may learn.

PPS: I know there's always the wonderfull midnigth commander (mc), but I just love that white text on black background CLI stuff. :-D

---

### Post by justleen on 2006-03-27
cp -v?
not adviseble in scripts though...

---

### Post by TLE on 2006-03-27
Ahh, I'm sorry I must not have explained it properly. What I'm looking for is an app that keeps telling me how far (e.g. 2% of file 10% of all files) it is in the copying process. cp -v just informs me when it is done with a file.
What I'm looking for is something like this (this is output from my copy script)
```
X@TLE32:~$ copy multimedia/video/0.33\ DVD/* .

COPIED: averylargefile.dat     in 0m 56s     at 26,6MB/s

FILE:11%,   35,4MB/s   ALL FILES:22%,   Passed: 1m 2s,   Total: 4m 37s,   Remaining: 3m 35s
```
Only, as I pointed out this copy script doesn't have a -r options, which I really miss

---

### Post by TLE on 2006-03-28
Nobody has a idea for this one? I'm sure someone has written an app. like that, It's just a matter of finding it

---

