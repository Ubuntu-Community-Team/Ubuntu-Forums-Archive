---
title: "Free space is misteriously disappearing with time without adding new packages"
date: 2012-09-10
forum: General Help
---

### Post by yoreei on 2012-09-10
Hi. I installed ubuntu through the minimal CD following this guide : [http://ubuntuforums.org/showthread.php?t=1201273](http://ubuntuforums.org/showthread.php?t=1201273) on an old laptop with only 60 GB HDD. I actually don't need more than this but here is what happened:
At the beginning of the day I installed the OS adding only **xinit, flwm, transmission, bleachbit **and** firefox**. Running the '*df*' command showed that only 3% of the / partition was filled leaving the other 52GB free.

So I started downloading a torrent that takes about 30GB and left the lappy do its job. Later the same day I checked what was going on and saw that 4.5GB (15%)  of the torrent was downloaded but '*df*' showed that 57% (30GB) of the / partition is filled.

About 23GB of the / partition is free but the torrent has 25GB left to be fully downloaded. I have no idea where this free space has gone. I haven't installed anything between the two df checks (and no one else has even touched the computer) 

So my question is: Is there some way to recover my lost HDD space and how do I do this?

Here is the output of '*df*':

```
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda1       56660284 30300760  23481268  57% /
udev              500568        4    500564   1% /dev
tmpfs             203140      348    202792   1% /run
none                5120        0      5120   0% /run/lock
none              507848        0    507848   0% /run/shm
```I ran Bleachbit with all options checked but only 6.4MB was recovered...

Thank you and sorry for long post.

And BTW, while I was installing Ubuntu I enabled automatic security updates (or something like this). Could it be possible that these take up so much disk space?:confused:

---

### Post by Cheesemill on 2012-09-10
Alot of torrent clients pre-allocate the entire space needed to download a torrent as soon as you start it (to ensure that you don't run out of space mid-download).

This means that your torrent may only be partially downloaded but it still take's up it's finished size on the disk.

This is nothing to worry about.

If you tell us what torrent client you're using then I can tell you how to check if this is what's happening.

---

### Post by iponeverything on 2012-09-10
> So my question is: Is there some way to recover my lost HDD space and how do I do this?

delete all the torrents from the queue..

---

### Post by yoreei on 2012-09-10
> **Cheesemill said:**
> 
If you tell us what torrent client you're using then I can tell you how to check if this is what's happening.
It's **transmission**. And.. thanks! I will now start the downloading again and see if more space is taken up
;)

---

### Post by yoreei on 2012-09-11
Thank you soo much! The torrent is almost finished but '*df*' shows that the partition stays at 57% :guitar:. If you hadn't told me this I would have reinstalled the whole OS... :p

---

