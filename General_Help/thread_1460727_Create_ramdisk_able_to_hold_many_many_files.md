---
title: "Create ramdisk able to hold many many files?"
date: 2010-04-23
forum: General Help
---

### Post by dxxvi on 2010-04-23
Hi All,

I created a ram disk with this command:

sudo mount -t tmpfs -o size=2048M,nr_inodes=500k,mode=777 tmpfs /var/cache/apt-build/build

When I run apt-build, I got an error message that the disk is full (unable to copy file or something). But no disk was full when I checked with 'df'.

Can we know the maximum of files created from the nr_inodes number? Or is there any other option that determines the max number of files created?

Thanks.

---

### Post by psusi on 2010-04-23
How full does the tmpfs get when you are building?  And how much ram do you have?  I'd suggest running a watch df -h in another terminal while you build.

---

### Post by dxxvi on 2010-04-23
> **psusi said:**
> How full does the tmpfs get when you are building?  And how much ram do you have?  I'd suggest running a watch df -h in another terminal while you build. I have 4gig on my machine and I used 2gig for the ramdisk. I didn't check how full the tmpfs was when apt-build was running (I'll do that next time), but when I saw the errors, the tmpfs was occupied for only 15% (maybe apt-build deleted something after it threw the error).

---

