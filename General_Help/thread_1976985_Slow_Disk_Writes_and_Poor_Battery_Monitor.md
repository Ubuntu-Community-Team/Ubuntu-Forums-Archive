---
title: "Slow Disk Writes and Poor Battery Monitor"
date: 2012-05-09
forum: General Help
---

### Post by vinpa on 2012-05-09
Hello,

Let me first start by saying that I was really impressed when I made the leap from 10.04 to 12.04. I own a Samsung NP700Z5A-S01CA laptop and upon booting from the CD all hardware (except Fn-key mapping, which I also could not figure out) was detected and after installation, the laptop was ready to go.

Now for the issue:

Whenever I copy/paste or attempt to write to disk in general, it is painfully slow. Not only that, but the write speed actually continuously decreases. Normally I don't take the time to write a post in a forum, EVER, but I have not been able to find a solution to this. Not only does it reportedly take over 2 hours to copy 4GB of data on this laptop, but also the batter seems to drain exceedingly fast.

These two problems are making it very difficult to migrate to Ubuntu from (you guessed it). Any HELPFUL feedback is greatly appreciated. I will gladly post any information required to make a diagnosis. (I prefer not to paste a bunch of text that may not be of any use to the support community).


All the best, and thank you all in advance.

vinpa

---

### Post by idoitprone on 2012-05-10
> **vinpa said:**
> Hello,

Let me first start by saying that I was really impressed when I made the leap from 10.04 to 12.04. I own a Samsung NP700Z5A-S01CA laptop and upon booting from the CD all hardware (except Fn-key mapping, which I also could not figure out) was detected and after installation, the laptop was ready to go.

Now for the issue:

Whenever I copy/paste or attempt to write to disk in general, it is painfully slow. Not only that, but the write speed actually continuously decreases. Normally I don't take the time to write a post in a forum, EVER, but I have not been able to find a solution to this. Not only does it reportedly take over 2 hours to copy 4GB of data on this laptop, but also the batter seems to drain exceedingly fast.

These two problems are making it very difficult to migrate to Ubuntu from (you guessed it). Any HELPFUL feedback is greatly appreciated. I will gladly post any information required to make a diagnosis. (I prefer not to paste a bunch of text that may not be of any use to the support community).


All the best, and thank you all in advance.

vinpa

hmmm problem with not much hardware or system configuration info?
that is not helpful

post output of
```

lspci -nnk
cat /etc/grub/default
blkid
cat /proc/cmdline 
```

---

