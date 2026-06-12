---
title: "Hard disk full of dark matter."
date: 2009-08-23
forum: General Help
---

### Post by walthehippie on 2009-08-23
I've been working on this all day. It started when I couldn't boot, said hd full.

Can't be full, I use about 10 g on a 40 g hd.

Did the usual and whacked Gimp.

I tried df -h, ls -S, apt-get clean, apt-get autoclean,, apt-get autoremove, fdisk, and fsck.

Didn't see anything that could account for 20+g.

Tried Disk Usage Analyzer and downloaded Filelight. They both said 39g used but when I analyze they only show me 10g.

Tried this post [http://ubuntuforums.org/showthread.php?t=495692](http://ubuntuforums.org/showthread.php?t=495692)

No joy.

This problem is hard to search for answers because I can't figure out how to phrase it. Everybody wants to tell me how to clean the hard drive. 20 gigs worth?

Thanks for any help, I'll be in and out. I goota get this grass cut.

---

### Post by michy99 on 2009-08-23
Empty root's trash.```
sudo rm /root/.local/share/Trash/*
```If that doesn't do it, read this page for possible solutions.

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

---

### Post by walthehippie on 2009-08-23
Thanks, figured it out.

Started Disk Usage Analyser from root and it showed me where the problem was.

---

