---
title: "mdadm ignores /etc/mdadm.conf"
date: 2012-03-07
forum: General Help
---

### Post by jon_herr on 2012-03-07
I have, for years now, been dealing with an mdadm problem.

My /etc/mdadm has two arrays defined in it, one is a raid 1 array for boot purposes the other is my /home folder.   Pretty basic.

Problem is...  on the /home folder UUID defined mount point is ignored by mdadm for assembly...  and my server halts with a warning about the array missing.

Not to say that it doesn't try to assemble an array.. it takes pieces of my /dev/md0 array and turns it in to /dev/md_d0 and etc...

Yet the boot array, /dev/md3/ ALWAYS works.  It's only the home folder that doesn't work.

What should I do?

The mkconf utility reports the wrong UUID for the array.
blkid agrees with the arry UUID

The UUID assigned to the /dev/md_d0 array is always different...  how can I mount it?

I'm stuck.

---

