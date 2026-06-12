---
title: "scp slow/stalled"
date: 2010-09-02
forum: General Help
---

### Post by kenm_uk on 2010-09-02
Hi. I am trying to copy a file from one server (Ubuntu 9.04) to another (Ubuntu 9.10) within my home network using scp.  (Both machines are quad-cores with SATA hard drives with plenty of RAM)

When I begin the transfer, the speed is initially shown as 2MB/s and gradually decreases each second until it runs at about 5-20 KB/s and intermittently showing the words "stalled".

However, if I try to copy a large file from my Windows XP machine to the target machine with WinSCP I get a transfer speed on the order of 1.6MB/s.

So I suspect there is something wrong with scp on the Ubuntu 9.04 machine. I have tried searching the web for a solution but have not yet found anything of relevance.  Can anyone please advise on how I might debug the slow copying via scp?

Thanks!

P.S. The most related post I have found is old and without a solution:
[http://ubuntuforums.org/showthread.php?t=1176435](http://ubuntuforums.org/showthread.php?t=1176435)

Edit: When I run scp with "-vvv" every few seconds it prints the line:
"ebug2: channel 0: rcvd adjust 131072"
What does this mean? Could it be related to the slow transfer speeds?

---

