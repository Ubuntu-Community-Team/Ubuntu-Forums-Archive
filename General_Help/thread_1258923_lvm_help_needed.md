---
title: "lvm help needed"
date: 2009-09-05
forum: General Help
---

### Post by emarkd on 2009-09-05
Hello all,

I'm not very familiar with using LVM and I've got a problem.  I had a 3-disk lvm group called 'media'.  One of the disks failed and now I can't access the other two.  When I run 'sudo vgdisplay', I get:

```

  Couldn't find device with uuid 'DeyDeF-5Oob-aXeE-rReB-WaV5-dLvp-UFqjZc'.
  Couldn't find all physical volumes for volume group media.
  Couldn't find device with uuid 'DeyDeF-5Oob-aXeE-rReB-WaV5-dLvp-UFqjZc'.
  Couldn't find all physical volumes for volume group media.
  Couldn't find device with uuid 'DeyDeF-5Oob-aXeE-rReB-WaV5-dLvp-UFqjZc'.
  Couldn't find all physical volumes for volume group media.
  Couldn't find device with uuid 'DeyDeF-5Oob-aXeE-rReB-WaV5-dLvp-UFqjZc'.
  Couldn't find all physical volumes for volume group media.
  Volume group "media" not found

```

What now?

Thanks for your time,
-Mark

---

