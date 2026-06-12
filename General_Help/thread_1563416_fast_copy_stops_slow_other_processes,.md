---
title: "fast copy stops slow other processes,"
date: 2010-08-29
forum: General Help
---

### Post by aboud on 2010-08-29
The local files copy speed from one disk to another is satisfyingly 60+MB/s, but this cause problem to other application, windows gray out, firefox freez, basically i have to wait for the copy to end to return to the computer.  any why to slow the copy speed down ?

---

### Post by McNils on 2010-08-29
Thats because the applications needs to access the disk and gets blocked by the high disk activity. You see this with top as wait (wa) goes up and the load usually increases as well.
I don't know how avoid this problem, better file systems???. I usually notice this when packing and unpacking compressed archives.

---

### Post by aboud on 2010-08-29
there are not many choices, I have ext4 . I wonder if changing the job priority somehow, can help.

---

### Post by usagiakumu on 2010-08-29
> **aboud said:**
> there are not many choices, I have ext4 . I wonder if changing the job priority somehow, can help.

There are like 30 or so choices. Personally I use ReiserFS, others have reported that XFS is good too, tinker around and see if one works for you. I generally like ReiserFS as it copies and archives and unarchives much faster than EXT3 ever did, and it still seems better than EXT4 in certain instances, for me at the very least. It should be noted that it is less compatible, and you are unable to see it from Windows. I know it's quirks very well, but it is way more stable than EXT3/4, but if you don't back up often and it has issues, then getting data recovered is a bit tricky. It has this tendency to be incompatible with certain versions of the Linux kernel at times and it likes to freak out and hang. I haven't seen this recently with the later versions, but it used to in the past. Happy hacking :)

---

