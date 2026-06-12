---
title: "Data migration recommendation request"
date: 2009-11-22
forum: General Help
---

### Post by deepsiks on 2009-11-22
Need some suggestions, server has two 1TB HDD's in Raid 0 configuration.  I have two more matching 1TB HDD's that I want to add to the system, really would like to wind up with all four in a Raid 5 configuration but space to shuffle data around is the problem.  The only thing I can think of is to create a Raid 5 with the two new HDD's, copy over as much data as possible and then delete the Striped set and add them to the Raid 5.  Anyone have a better idea?

---

### Post by i.r.id10t on 2009-11-22
Well, you won't be able to create a raid 5 with just 2 1tb disks - you need a 3rd.

I'd say suck it up spend the extra $100 on a 3rd 1tb drive, set it up as raid5, copy all the data, then use the 2 1tb drives from the raid0 either as hot swap or set 'em back up as a raid-1 to do more storage, etc with.

---

