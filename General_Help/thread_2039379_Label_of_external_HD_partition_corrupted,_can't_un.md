---
title: "Label of external HD partition corrupted, can't unmount, Disk Utility won't fix."
date: 2012-08-08
forum: General Help
---

### Post by james_mcl on 2012-08-08
I backed some data up onto my external HD today, and after reconnecting it to do a check, discovered that the label/name of the partition in question had become corrupted (including, in particular, a newline character and one that wasn't ASCII)

If I right click on the mounted partition and choose "Properties" I get:

P
rZi#

as the name (actually, there's a non-ASCII one-of-those-squares-with-four-numbers-in character between the i and the #, but it doesn't seem to have pasted in.)

If I try to use "Safely Remove Drive", I get a dialog box telling me

"Failed to eject medium; one or more volumes on the medium are busy."

The output of mount for the other two partitions on the external drive is correct, but not for this one:

```

/dev/sdc1 on /media/External_HDD type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdc3 on /media/66b9f268-08f9-4e46-b15b-700419aa7d13 type ext3 (rw,nosuid,nodev,uhelper=udisks)
rZi# type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

```

- note that the /dev/sdcNUMBER isn't shown for that one, but is for the others.

If I go into Disk Utility, I can use "Unmount Volume" on the other partitions, but not this one. I'm informed that the device is /dev/sdc2, that the mount point is /media/P, and when I click on "Unmount Volume" I get "Error unmounting: umount exited with exit code 1: umount: /media/P: not found".

Any ideas? Anyone?

---

### Post by dcstar on 2012-08-10
> **james_mcl said:**
> 
........
If I go into Disk Utility, I can use "Unmount Volume" on the other partitions, but not this one. I'm informed that the device is **/dev/sdc2**, that the mount point is /media/P, and when I click on "Unmount Volume" I get "Error unmounting: umount exited with exit code 1: umount: /media/P: not found".

Any ideas? Anyone?

```
sudo umount /dev/sdc2
```

---

### Post by james_mcl on 2012-08-19
Belated thanks to David (After this thread didn't get replied to for a couple of days, I stopped checking it.) - this allows me to unmount successfully, which in turn allowed me to rename the volume to something better than 

P
rZi#

- nice one!

---

