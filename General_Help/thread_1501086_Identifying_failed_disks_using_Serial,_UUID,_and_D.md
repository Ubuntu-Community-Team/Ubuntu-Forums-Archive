---
title: "Identifying failed disks using Serial, UUID, and Device Name"
date: 2010-06-03
forum: General Help
---

### Post by xoddoza on 2010-06-03
Hey there.

This is more a of a theoretical question than an actual problem i'm having right now. I'm just looking to clarify the expected behavior of Ubuntu 10.4 (looking at installing server edition) when a hard drive thats part of the raid 6 mdadm array fails.

Now, as I udnerstand it, a hard drives device name ie sda etc will change as hard drives are added or removed and as controlers are added or removed when pcs are rebooted.

While this wont cause any problem with the arrays fuction as it uses UUIDs, it makes determining the hard drive that has failed difficult. I've used smartmontools as a way of finding a drives serial number giving its device name.

Is there any easy way to be able to determine which drive has failed in an array? As it is now, I think youd have to find which serial numbers are still conected to find out the failed one?

All my drives have the serial number in a special sticker on the rear so you can see them whilst all plugged in.

Thanks

---

