---
title: "badblocks reading drive too quickly?"
date: 2010-09-11
forum: General Help
---

### Post by andymcca on 2010-09-11
Hey all,

I'm running badblocks on some new disk drives just to be safe before my return period expires.

I'm running the command```
sudo badblocks -b 4096 -p 4 -c 65536 -w -s /dev/sdb1
```on an empty partition taking up the entire device. I am getting the following output:```
Testing with pattern 0xaa: done                                
Reading and comparing: done                                
Testing with pattern 0x55: done                                
Reading and comparing: done                                
Testing with pattern 0xff: done                                
Reading and comparing: done                                
Testing with pattern 0x00: done                                
Reading and comparing: done                                
Testing with pattern 0xaa: done                                
Reading and comparing: done                                
Testing with pattern 0x55:  76.86% done, 14:08:46 elapsed
```There are two issues that make me worry:

1) When it gets to the "reading and comparing" phase, it seems to complete in <1s. I see other posts where people say this takes them as long as it took to write to the drive. I don't see any mention of this being quick, so I'm just afraid that badblocks is being denied read access or something.. Anyone familiar with this behaviour?

2) Obviously since it is on a sixth pass, badblocks thought that it found new bad blocks on the second pass (or later). When I check SMART, though, the drive has not re-allocated anything (despite having plenty of spares)... Doesn't this seem odd? Is there some reason why the disk would not step in upon a write fail? In fact, I thought a write fail should be transparent... Which makes me wonder if question 1 (above) is causing this...

Any help, thoughts, musings, etc. would be appreciated! Thanks!

---

### Post by andymcca on 2010-09-11
So it appears I am just oblivious. Regarding my two concerns:

1) I am now watching a "reading and comparing" take a fair ammount of time:
```
Testing with pattern 0x55: done                                
Reading and comparing:  66.29% done, 15:22:32 elapsed
```so somehow when I thought I saw the read complete instantly, I had missed the fact that it had been reading for the last hour.

2) Apparently when running with multiple write values (ie 0x00, 0x55, 0xaa, 0xff by default), a full set of four passes counts as a single pass for the -p parameter. Sooo I'll report back in a few days. :D

---

