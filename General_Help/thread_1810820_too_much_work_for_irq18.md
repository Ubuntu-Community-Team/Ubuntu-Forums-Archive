---
title: "too much work for irq18"
date: 2011-07-23
forum: General Help
---

### Post by Manolicious on 2011-07-23
I've had this problem on and off since 9.10.  My system is at 10.04 LTS (2?) now with 2.6.32-33-generic kernel.  Typically it happens at start up, right about when I arrive at the login screen I notice it.  Either if I'm signed in or not I can go to one of the virtual terminals (ctrl alt f#) and see the following message repeat.

[####.######]serial8250: too much work for irq18

With # representing some digit.  The first for digits in the bracket usually appear to start at 200 something and they would start increasing with each repeat of the message.  With a new large sata hdd I mounted it went up last time to +1400.  Before the process would put drag on my processor, but recently with the new hdd it couldn't even stop, so much that even moving my mouse in the gui was nigh impossible.  I had to hard restart.

Last time I researched this I think it had to do with the age of my computer (from ~03-04) and that it's not used to large sata drives, so I guess irq18 has something to do with scanning blocks (or fscking?).  Also my file system is ext3, would that be a problem?

---

