---
title: "vlc filled up my hard drive"
date: 2011-04-30
forum: General Help
---

### Post by davidstoll on 2011-04-30
I used vlc to view /dev/video2 (a hauppauge HDPVR).  Well, it crashed, but evidentially, the process was still running.  It ran all night and my hard drive is now full, but I can't figure out where it put it's cache/temp file(s).

Here is what I ran:

```
vlc -f /dev/video2
```

I tried to find large files using this, but it didn't find anything, so maybe it broke it's files up into many smaller pieces or something...?  Maybe the code above is wrong?

```
find ./ -type f -size +100k -print
```

I'm running Mythbuntu 10.10 32bit.

Now it just puts me to a command line login prompt, but keypresses are intermittent.  I have to ssh in to do anything.

---

