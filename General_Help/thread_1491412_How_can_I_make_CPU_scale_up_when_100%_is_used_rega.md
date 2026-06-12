---
title: "How can I make CPU scale up when 100% is used regardless if 80% of that is &quot;io wait&quot;?"
date: 2010-05-23
forum: General Help
---

### Post by motin on 2010-05-23
When I run large rsync sessions (backup purposes), I often find that the cpu goes up to 100% on both cores, and the systems gets almost unusable as slow it is. Top reveals around 80% is reported as "wa", which is IO Wait right?

Well, using the CPUfreq applet, it is possible (but irritatingly sloow) to manually set the cpu frequency to the highest possible. After this the computer gets much more snappy. 

How can this be done without manual intervention, anyone knows?

---

### Post by dtfinch on 2010-05-23
I use "ionice -c 3" in my desktop backup script to give rsync's IO a lower priority than the rest of the system. I have it run every few hours, and I don't notice it.

My desktop's backup script looks like this, repeated for several folders:
```
/usr/bin/ionice -c 3 /usr/bin/rsync -rbutpog --delete --backup-dir=/store/past --modify-window=65 --ignore-errors /home/david/Documents /store/backup >> /store/backup.log 2>&1
```

I haven't noticed rsync using a lot of cpu though, unless maybe you're backing up to ntfs, but then it would be the ntfs-3g process using most if it. If it's just rsync causing the high cpu usage, you can probably add a /usr/bin/nice in front of it to lower cpu priority too.

I'd also check that you have -t (--times) in your rsync options, otherwise it's forced to recompare every single file which may increase the total time the backup takes. And if the backup is on a different kind of filesystem, rounding can cause modify times to be slightly different, and resync will recompare them anyways unless you use --modify-window with the max number of seconds difference you want it to consider as equal. I use about a minute.

---

