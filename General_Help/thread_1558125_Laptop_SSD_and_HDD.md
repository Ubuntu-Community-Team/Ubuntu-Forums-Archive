---
title: "Laptop SSD and HDD"
date: 2010-08-21
forum: General Help
---

### Post by drdanielfc on 2010-08-21
Hello,
I'm purchasing a laptop with both a primary drive as an SSD and a HDD for storage ([http://www.buy.com/prod/toshiba-qosmio-x505-q890-18-4-notebook-intel-core-i7-740qm-1-73ghz-6gb/q/loc/101/216459080.html](http://www.buy.com/prod/toshiba-qosmio-x505-q890-18-4-notebook-intel-core-i7-740qm-1-73ghz-6gb/q/loc/101/216459080.html)). Does anybody have any suggestions for gaining speed and convenience (ie moving /home to the hdd)?

Thanks ahead of time,
 Daniel

---

### Post by J V on 2010-08-21
Yes, install /home on the HDD and swap and / on the SDD...

If its a large SDD (50g +) you can install /home on it as well and make an entire data partition for the HDD...

When you get to the partitioning scheme say "Specify partitions manually", here you can create and more importantly, choose how to mount, partitions.

Make one on the SSD (10gigs should do it for / if you want to put home there too) and the other on the HDD and select the mount points appropriately...

---

### Post by drdanielfc on 2010-08-21
Ok this is what I was planning on doing and the SSD is 64gb but I am going to be dual booting out of requirement (VB required for schoolwork).

I'm also curious about /var/tmp and /var/log on the HDD as was described in the description of [http://www.youtube.com/watch?v=_WnujXu34tk&feature=related](http://www.youtube.com/watch?v=_WnujXu34tk&feature=related). Would there be any noticeable speed difference or improvement SSD life?

Finally, (last question) would setting the home partition like that allow me to reinstall ubuntu but reuse the home dir?

~Dan

---

### Post by J V on 2010-08-22
/var on the HDD might speed things up a little...

Yes, seperate home folder means you get to keep all your settings...

---

### Post by john newbuntu on 2010-08-22
With 6GB RAM, I was wondering if it is worthwhile puting swap on HDD and /tmp on tmpfs.  Also if you do not care about access times on files, might speed things up a bit if you remove relatime and add noatime in fstab for all filesystems except swap.

---

