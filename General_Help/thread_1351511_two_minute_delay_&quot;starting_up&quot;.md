---
title: "two minute delay &quot;starting up&quot;"
date: 2009-12-10
forum: General Help
---

### Post by olithered on 2009-12-10
My computer has recently been upgraded and now there is a long pause after the words "Starting up" are displayed and before any further hdd access or boot progress.

According to the timings in the dmesg log it is over two minutes (127 seconds)!

I found the following bugs which may or may not be related:
  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337355](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337355)
  [https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/100110](https://bugs.launchpad.net/ubuntu/karmic/+source/linux/+bug/100110)

====
Linux lnc 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 21:27:25 UTC 2009 x86_64 GNU/Linux

---

### Post by NT4usB on 2009-12-10
Laptop or desktop?

A quick google on the last task before the hang finds [this]("http://ubuntuforums.org/showpost.php?p=3186536&postcount=4")
Thats two votes for [USB issues]("http://ubuntuforums.org/showthread.php?t=705849")

Possible debugging idea [here]("http://www.gossamer-threads.com/lists/linux/kernel/1012521#1012521")

---

### Post by MartyBuntu on 2009-12-10
Many people who dual boot (OS's on two seperate physical drives) are reporting boot delays.

---

### Post by Xbehave on 2009-12-10
try installing bootchart then uploading your bootchart (the png and the tgz) as it may give more info.

---

### Post by olithered on 2009-12-11
It is a desktop machine.

I've installed bootchart but it seems I need to wait until I've rebooted again for it to make the chart...

---

### Post by olithered on 2009-12-28
Here is the bootchart graph...

---

### Post by olithered on 2010-01-18
Bug submitted:
  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509342](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509342)

---

