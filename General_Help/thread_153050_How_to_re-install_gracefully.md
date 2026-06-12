---
title: "How to re-install gracefully?"
date: 2006-03-31
forum: General Help
---

### Post by RoboJ1M on 2006-03-31
Hi,

I (may) want to try getting my ATI card working with a clean install of Ubuntu.

I have a 40Gb (/) and 80Gb (/home) partition.

My question is how do I format and re-install over / without breaking /home.

Is there an install-time option to say "My /home already exists and it's on /dev/hda/something-something"?

Thanks,

J1M.

---

### Post by teataster on 2006-03-31
When the partitioner starts, go for the manual editing option and set your desired partitions to root/home etc..  You do this by changing the mount point for that partition- the instructions during the install are very good.  If you don't set the partitioner to format your home folder, then it won't be touched.  You need to format the root folder, as otherwise the installation will cease.

You should also set up a swap partition of 500MB to 1GB while doing this.

HTH!

---

