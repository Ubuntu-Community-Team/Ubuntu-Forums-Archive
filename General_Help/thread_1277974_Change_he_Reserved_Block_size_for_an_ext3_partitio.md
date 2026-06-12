---
title: "Change he Reserved Block size for an ext3 partition"
date: 2009-09-28
forum: General Help
---

### Post by ikus060 on 2009-09-28
Hi all,

I wanned to change the 'Reserved block count' of my ext3 partition. I have a 1Tb disk ans so I found useless to have 5% of 1Tb reserved. So I want to change it to 2%.

I ran the following command line :
sudo tune2fs -m 2 /dev/sdd1

I try to umount, mount, reboot, etc and I don't see the change when I run df.

Is there something special to apply the modification?

Regards,

ikus060

---

