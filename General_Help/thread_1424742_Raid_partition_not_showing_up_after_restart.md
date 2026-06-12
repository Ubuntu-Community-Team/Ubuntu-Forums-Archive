---
title: "Raid partition not showing up after restart"
date: 2010-03-08
forum: General Help
---

### Post by power78 on 2010-03-08
Hello,

I recently installed a RAID0 using three drives via a RAID card. I opened up gParted and formatted the array as EXT3. I was able to mount the device for it appears as /dev/mapper/sil_bgadabacbcbd with the partition as /dev/mapper/sil_bgadabacbcbd1. While trying to create an entry in fstab for auto mount on startup, I receive an error that the partition was not found. Upon inspection, the partition sil_bgadabacbcbd1 is no longer listed in dev/mapper. However, the device is. 

I then opened gparted and it made /dev/mapper/sil_bgadabacbcbd1 appear. What is gparted doing to create the /dev/mapper/sil_bgadabacbcbd1 device on my hard drive? What do I have to do to make the startup script work?

Thanks,

Jason

---

### Post by power78 on 2010-03-08
To clarify: I am only able to see the partition once gparted is started. Why is this? The only way I can mount the raid parition is to open gparted so it makes the parition appear in /dev/mapper, then run the mount command on this newly visible partition device. Any thoughts?

---

