---
title: "Making a linear RAID persistent"
date: 2010-01-15
forum: General Help
---

### Post by summersab on 2010-01-15
I have three drives:

/dev/sda   1000 GB
/dev/sdb   500 GB
/dev/sdc   500 GB

I currently have a working install on /dev/sda1 with over 900 GB of data stored on it (VHS archives and the like). Ideally, I would like to make a linear RAID of all three drives so that they appear as one. However, since /dev/sda1 is active with my root partition on it, I can't use mdadm to start a RAID device. How, if possible, do I go about doing so and then modifying GRUB2/fstab/anything else to make the array persistent and bootable?

If it ISN'T possible, I know how to make an array of the two 500 GB drives, but how do I make it autodetectable upon boot and give it user privileges? I can create the array and mount it (even gives it a special icon as a "multiple disk array" - Ubuntu is so smart), but upon restart, it disappears, and when mounted, it is only accessible as super user. Thoughts?

Thanks, community - you're freakin awesome!

---

