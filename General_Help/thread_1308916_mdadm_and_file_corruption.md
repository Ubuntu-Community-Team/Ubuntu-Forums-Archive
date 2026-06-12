---
title: "mdadm and file corruption"
date: 2009-11-01
forum: General Help
---

### Post by david90 on 2009-11-01
Has anyone ever encountered a case where mdadm corrupts the raid file system which lead to data lost?

---

### Post by Cr0n_J0b on 2009-11-01
I'm not sure what kind of corruption you are referring to.

I've been using mdadm for some time now and it works pretty well.  Most of my issues are related to flaky disks that go bad and mess up the setup.  In the last case i had a bad drive throw off all my device assignments...at the same time, I was trying to setup a new md volume...and...i used the zero-superblock to clean up an old disk...and...well...it actually belonged to an active raid volume.  Needless to say, I'm rebuilding that volume now.  ;)

---

