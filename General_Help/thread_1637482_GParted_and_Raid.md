---
title: "GParted and Raid"
date: 2010-12-04
forum: General Help
---

### Post by jasonabullard on 2010-12-04
Ubuntu 10.10

I just installed GParted so I could shrink a volume to install Windows in a multi-boot config but am having a bit of trouble.  I am using a nVidia RAID0 setup which has been working with no problems at all.  I opened GParted expecting to see only one drive but it shows both drives that are a part of the RAID config.

I obviously don't want to make a change to any of the drives because it would then cause my RAID to fail.  So, how do I shrink a volume when all the partitioning applications show both drives and not the RAID config??

Thanks,
Jason

---

### Post by ronparent on 2010-12-05
You are so right, you DO NOT want to make any changes to the individual drives.

Your raid is not showing in gparted because of a bug. Although supposedly corrected upstream the change has not apparently shown up in the 10.10 distribution disks. The fix is simple. Install kpartx. Once that is installed the raid will show in gparted and all your changes to the raid will be valid.

---

