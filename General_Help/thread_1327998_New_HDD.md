---
title: "New HDD"
date: 2009-11-16
forum: General Help
---

### Post by Patricrawley on 2009-11-16
I just installed a new 100 GB HDD and I formatted it to fat32 and now I want to mount it. 

I want it to be mounted in /storage so I used ```
sudo chown -R patrick:patrick /storage
```

My fstab entry is correct ```
UUID=1E55-6F47	/storage     vfat	defaults     0	   0
```

---

