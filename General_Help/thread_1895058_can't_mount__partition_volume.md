---
title: "can't mount  partition volume"
date: 2011-12-14
forum: General Help
---

### Post by sekacorn on 2011-12-14
i can't mount my partition i  stayed up all night and another one is coming. it says file driver not install

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
how can i mount it

---

### Post by ajgreeny on 2011-12-14
Is this your root partition, ie, the main ubuntu partition that will not mount, and is this a new installation that has not booted successfully before?

More information is needed before an answer can be given.

---

### Post by sekacorn on 2011-12-14
[IMG]http://i613.photobucket.com/albums/tt213/sekacorn/Screenshotat2011-12-14154918.png[/IMG]

I am trying to mount sda1. this partition couldn't boot successfully boot at all

---

### Post by Mark Phelps on 2011-12-14
Partition is shown as "hfs" format! Is that what you expected?

Or was it something else and the format got corrupted?

---

### Post by sekacorn on 2011-12-14
yes that is what i expected it to be. i was trying to recover my mac partition and i did but i can't access it or even mount it

---

### Post by larrypg on 2011-12-14
Hello,

Not sure how mac changes things but it seems you have 7 partitions and it does not look like any are in an extended partition. That could be the problem.

---

### Post by sekacorn on 2011-12-14
i can't acces the partition so i have decided to see use a live cd rEFIT. everytime i tried tto boot he CD, it would be  would be ejected

---

