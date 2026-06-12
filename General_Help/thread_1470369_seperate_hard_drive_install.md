---
title: "seperate hard drive install"
date: 2010-05-02
forum: General Help
---

### Post by spiritech on 2010-05-02
hi

just a notion i would like an answer to -

does a computer run faster if the OS and all relative software partition is on a separate hard drive than the storage data. 

i figure it might be quicker because data is travelling one way instead of two.

:popcorn:

---

### Post by marshmallow1304 on 2010-05-02
In many cases, yes.  This is the purpose of [RAID 0]("http://en.wikipedia.org/wiki/RAID#RAID_0").  I don't think it would be all that noticeable unless you're doing large file transfers.  Best to just get a faster hard drive.

---

### Post by spiritech on 2010-05-02
so it is faster. thats good. 

if i decided to try this method would i have to do the partitioning on the install manually or will the install give me an option if it detects two hard drives.

you say it wouldnt be that noticeable unless i was doing large FTP, how large ? i often back my work up to a second computer through FTP, with files as large as 100 GB it does not take to long ( around 23 mins ) at current. maybe this could be faster as the bottle neck is definitely at the hard drive read/write speed.

what are the fastest ( reasonably priced ) hard drives on the market. are hard state hard drives faster or slower than standard disk drives. """ idea""" ( maybe it would be cool in the future to have some kind of integrated hard OS memory built onto ( not into, ie removable, upgradable sizes ) that could run super fast.

if i decide to set up raid in Ubuntu is it difficult.

---

### Post by akand074 on 2010-05-02
Its faster even without RAID 0. Your hard drive speed is kind of like a single core processor. If your reading data to run the operating system/applications, it will slow down things like copy/pasting data and such. If they are on separate hard drives, you'll get a performance boost. Not a big one really, but a small performance boost.

---

### Post by spiritech on 2010-05-03
so all i need to do is install the OS on a separate hard drive ?

---

### Post by marshmallow1304 on 2010-05-03
> **spiritech said:**
> so all i need to do is install the OS on a separate hard drive ?

Yes.  Then you'd have your data (maybe /home) on a separate hard drive.  I should have been more clear - RAID 0 is an example of one way to use multiple hard drives for a performance boost, but it is not required.

---

