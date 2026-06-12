---
title: "Corrupted Partition on Hard Disk"
date: 2011-05-11
forum: General Help
---

### Post by Abacus Man on 2011-05-11
Basically, I just installed Ubuntu over Windows Vista because I was getting fed up with the performance on it.
During install I set up a partition, one for Ubuntu and one for data. However, my second, larger partition gives this error when I try to mount it...
> 
Error mounting: mount exited with exit code 12: Failed to read last sector (976764927): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

Any ideas as to what may solve this and what I can do in the future to help prevent it from happening?
Thanks in advance :)

---

### Post by coldraven on 2011-05-11
Someone else will know better than me, but in the meantime....
What did you format this "data" partition as?
Run Gparted and check it, then maybe try to re-format it. (right click on it and select format)
I usually just use ext4 formatting on my internal drive but NTFS on my external USB drive to have the option of plugging it into Windows.

---

### Post by Abacus Man on 2011-05-11
Now it doesn't give me an error either...

---

### Post by ThatCoolGuy220 on 2011-05-11
I sugest to Format all your hardrive

OR


you can create a bootable USB with Gparted Live Cd (Make sure is latest version)

To erase or format them...



Last hope is to use something stronger to Wipe Your HDD 
(I did it cause i had a lot of problems but now they vanished)

but dont worry if my suggestion doesnt solve your problem, Surely someone else will do it.

---

