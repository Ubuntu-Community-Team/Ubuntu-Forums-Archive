---
title: "root / trash / deleted folders"
date: 2010-12-03
forum: General Help
---

### Post by Red_Steve on 2010-12-03
Hey there.

I've followed this tutorial [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

to create a separate home partition.

After checking that everything went right I did a big mistake.
Instead using the rm -rf command I manually moved the home_backup folder into the trash bin where it completely vanished.

I found out that it resides in /root/.local/share/Trash/files where I actually found it. But instead of moving it back and doing it the right way I did move it into the trash bin a second time. Now the folder is completely vanished while the storage media manager still shows that something that big is occupying the space.

So my question: Where did the folder now go?

Edit: Nevermind, found it: It will then reside in /.Trash-0

---

