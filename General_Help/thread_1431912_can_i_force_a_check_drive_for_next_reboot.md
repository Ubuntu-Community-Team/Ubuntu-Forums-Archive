---
title: "can i force a check drive for next reboot?"
date: 2010-03-17
forum: General Help
---

### Post by eival on 2010-03-17
todays update required a restart an then it went into check disc mode but i dont have time to wait and ended it.

is there a way to force a check disc on a reboot when i do have time?

---

### Post by sisco311 on 2010-03-17
Yes, set the mount count of the filesystem to a value greater than 40:
```
sudo tune2fs -C 50 /dev/sda1
```
replace /dev/sda1 with the actual device name. To get the device names & mount points of the mounted partitions type:
```
mount
```

NOTE: Linux is case sensitive, that's an uppercase c in the command.

---

### Post by mcduck on 2010-03-17
> **eival said:**
> todays update required a restart an then it went into check disc mode but i dont have time to wait and ended it.

is there a way to force a check disc on a reboot when i do have time?

yes, just create an empty file called "forcefsck" in the root of the dirve you wish to be checked on next boot.

For example:
```

sudo touch /forcefsck
```
This will create the file on your root partition, causing it to be checked on next boot. (the file will be automatically removed afterwards)

---

### Post by SabreWolfy on 2010-11-15
> **sisco311 said:**
> Yes, set the mount count of the filesystem to a value greater than 40:
```
sudo tune2fs -C 50 /dev/sda1
```
replace /dev/sda1 with the actual device name. To get the device names & mount points of the mounted partitions type:
```
mount
```

NOTE: Linux is case sensitive, that's an uppercase c in the command.

Why 40?

---

### Post by sisco311 on 2010-11-15
The max mount count of a partition is usually between 20 and 40. I think, by default, in Ubuntu it's 20 for the root partition and 30 for other partitions, but you can always check it: 
```
sudo dumpe2fs -h /dev/sd**XY**
```

---

### Post by SabreWolfy on 2010-11-20
Thanks.

Ubuntu 10.04 Server: / Maximum mount count is 36; /home is 22.

Ubuntu 10.04 Desktop: / Maximum mount count is 32; /home is 37.

---

