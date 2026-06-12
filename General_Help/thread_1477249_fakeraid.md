---
title: "fakeraid"
date: 2010-05-08
forum: General Help
---

### Post by maudigan on 2010-05-08
I've been trying to get fakeraid setup on this supermicro board. I'm having some issues though. Off the top of my head I think the raid controller is an ICH10. I've tried booting with the live CD and creating the partitions. When i'm in gparted I see 1 volume, the volume I created in the bios. As well as the 4 individual discs, 4 x 250gig WD drives. It is raid 10, and in gparted shows up as a 500gig drive appropriately.

When I boot 9.10 server, it recognizes raid, I activate it, but it shows up as 2 x 250gig drives. In the bios I named them "test", they show up in the 9.10 server as "blahblah_test-0" and "blahblah_test-1". Its as if the mirror portion of the raid is working correctly, but not the stripe portion. That is the behavior I get using the intel bios. Using the adaptec bios I get NO drives showing up.

The issue is the same in 10.04 server. Anyone have any clues on what I can do to fix this?

---

