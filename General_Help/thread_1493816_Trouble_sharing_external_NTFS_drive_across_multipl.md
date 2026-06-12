---
title: "Trouble sharing external NTFS drive across multiple users"
date: 2010-05-26
forum: General Help
---

### Post by HyperFlexed on 2010-05-26
Hi, I have an external USB hard drive at /dev/sdb1 (NTFS)

2 users: johnny, audio

for some reason this drive is mounted at /media/TREKSTOR_ with johnny as the owner. I can't seem to chown the drive to audio. If I unmount the device, and remount it, the owner is set to johnny again. I need to access this drive from the audio account.

Any help would be appreciated. It's a 1TB drive, so I wouldn't be able to reformat it to EXT3 easily as it's almost 60% full.

---

### Post by dino99 on 2010-05-26
add johnny to audio group, and audio to johnny group (system admin user & group)

or install mountmanager and set your prefs for all devices and partitions (system admin mountmanager)

---

