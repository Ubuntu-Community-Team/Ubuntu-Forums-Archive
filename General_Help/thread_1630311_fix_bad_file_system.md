---
title: "fix bad file system?"
date: 2010-11-25
forum: General Help
---

### Post by kylegio on 2010-11-25
OK my computer started giving errors on boot about checking of disk failing on boot and asking me if i want to ignore, skip...etc mounting the drive

i just skip so that i can get into ubuntu.

check the drive in disk utility, all it says is that it is "not clean"

tried using fsck 

```
sudo fsck.ext4 -f /dev/sda1 
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

```

smart data showing ONE bad sector. drive is a week old, 2TB western digital and is full... at the very least i need to be able to get data off of it.



any help?
thanks
kyle

---

### Post by cpu_medic on 2010-11-25
if you have another 2 tb drive sitting around, i would ghost the drive, and send the bad sector one back to WD to be fixed(replacement). is it still under warrenty?

---

### Post by carl4926 on 2010-11-25
To get the data off it you must have somewhere to send it.

It's not clear from your comments what part this HD plays in your system or if you can access it's data once Ubuntu is up and running.

Booting a live cd and starting Gparted, you can check partitions from there too. Did you try that?

---

