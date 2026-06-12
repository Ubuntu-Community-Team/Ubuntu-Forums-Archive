---
title: "Issue Mounting Esata drive"
date: 2010-07-31
forum: General Help
---

### Post by dmarquard on 2010-07-31
I am mounting a new esata hard drive connected to a sata port by way of sata to esata connector in the box and Esata cable to the Esata Drve.
I partitioned and formated the drive just fine.
When I tried to mount it I could only access as root.
The mount point /dev/sdc1 to /mnt/fantom rwxr-x-r-x root:root after mounting it is the same.
I have a second sata internal that mounts /dev/sdb1 to /mnt/d2   rwxr-x-r-x root:root but it changes to david:david upon mounting and I can read write to it w no problem.
In both cases I mount w sudo mount /dev/sd** /mnt/<dir> using no options.
In the case of /mnt/fantom I can only write as root.
I mount both manually and have nothing in fstab for either.
Any suggestions on how to get mount to /mnt/fanton to work correctly.
Im using Ubuntu 10.04.

---

