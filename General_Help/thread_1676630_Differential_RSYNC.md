---
title: "Differential RSYNC"
date: 2011-01-27
forum: General Help
---

### Post by dsprankle on 2011-01-27
I have an Ubuntu 10.10 server (bignixbox) sharing a 10TB RAID5. I also have a Macpro w/ Mac OS X 10.6.6  (bigmac), with 2TB of available space, which backs itself up to Carbonite.

1. I want to be able to do, say a nightly 2TB worth of data rsync to "bigmac" from "bignixbox" then 'bigmac will sync up with Carbonite.

2. Then have that 2TB worth of data on BigMac deleted (which is now saved on Carbonite server), and repeat process for next 2TB worth of data. After the initial 10TB worth of data are all up on Carbonite, I'd like to just back up files that have been added or changed on "bignixbox"in a 24hr. period.

3. I have a basic understanding of rsync and have had success backing up a few test directories from "bignixbox" to "macpro" using rsync over ssh, I just don't understand how to put it all together and 
tell it to do what I am trying to achieve. 

Thanks,
Dale

---

### Post by dsprankle on 2011-02-05
Bump.

---

