---
title: "How do I resize my LVM2 partition?"
date: 2010-02-19
forum: General Help
---

### Post by s3a on 2010-02-19
Can someone please explain to me how to do this in easy to follow instructions? (because a google search provides me with difficult (and risky - in my opion) tips.)

One of the benefits of LVM is that I can resize it WHILE using my OS, right? So, how do I do it? I have /home and / (root) LVM partitions, and I have a /dev/sdb1 /boot partition (all are ext4). I do not have whole drive/partition encryptions.

Any help would be GREATLY appreciated!
Thanks in advance!

P.S. I desperately need to shrink my /home and increase the size of my / (root) because I have ~115MB free and I can't even update/upgrade my system!

---

### Post by s3a on 2010-02-26
Anybody know?

---

### Post by Turtle.net on 2010-02-27
I'm looking for the same thing.
I'll try to use pvresize [http://manpages.ubuntu.com/manpages/hardy/man8/pvresize.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pvresize.8.html)

---

### Post by s3a on 2010-02-27
Thanks! You're the only one that ever answered this question of mine! I just googled pvresize and saw that this is part of the lvm2 package so I am guessing that I already have this installed! I'll look into this soon enough whenever I am not busy with school but I just wanted to say thanks again for leading me in the right direction!

---

