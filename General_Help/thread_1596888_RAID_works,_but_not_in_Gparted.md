---
title: "RAID works, but not in Gparted"
date: 2010-10-14
forum: General Help
---

### Post by willsomebody on 2010-10-14
Hi all,

I have a striped array set up on two disks.  It has an ntfs windows partition, an ext4 /home partition, and an ext4 / partition.  Both operating systems work flawlessly with this configuration.  I bought a new drive that I want to copy my partitions onto, so I installed gparted.  When I opened it up, it didn't see my partitions.  It has always worked for me in the past.  I am running a fresh (about a week old) install of ubuntu 10.10.  Before that, I had 10.04 and gparted saw my RAID drive and the partitions on it, in fact, I believe I originally created the partitions with it.  Does anyone have any clue why the new version would behave this way?

Thanks in advance,
will

---

### Post by ronparent on 2010-10-15
I thought that problem was fixed with 10.10. 10.04 wouldn't recognize raid partitons without a work around. This might work for your situation. In a terminal install kpartx:
> sudo apr-get install kpartx
Kpartx work with gparted and allows it to see raid drives. Let us know if this works.

---

### Post by willsomebody on 2010-10-16
Thanks!  That did the trick.

---

