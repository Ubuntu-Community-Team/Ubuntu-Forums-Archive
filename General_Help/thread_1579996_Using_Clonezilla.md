---
title: "Using Clonezilla"
date: 2010-09-22
forum: General Help
---

### Post by lsutiger on 2010-09-22
I have used clonezilla in the past only twice, once with a bootable drive. Both times I was successful. 



I bought a new hard drive. This new drive is a boot drive. The new drive is 150GB, the old drive is 74GB. I partitioned and formatted the new drive with a 10GB / partition, a 4 GB swap partition, and the rest for /home.

I then used clonezilla to do a local partition to partition copy. I used all default settings.
When done, I hooked up the new drive, but could not boot. Hooked up the old one as the boot drive, ran Gparted and noticed the new drive's / partition was not flagged as boot, so I did so.
Rearranged the drives to boot off of the new and still could not boot.


Any ideas on how to troubleshoot this, or a setting I should have used?

---

### Post by Mark Phelps on 2010-09-23
Don't know a specific fix, but I do know that Clonezilla has a clone disk option -- that copies everything from the old drive over.

I would have tried that first.  If that worked, you could boot from Clonezilla and do partition resizing once the machine is booting OK.

---

### Post by lsutiger on 2010-09-23
OK will try that.
Than you

---

### Post by lsutiger on 2010-09-24
Thank you, disk to disk worked...now how to resize the partition. Off to googling.

---

