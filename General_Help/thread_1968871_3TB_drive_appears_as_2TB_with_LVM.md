---
title: "3TB drive appears as 2TB with LVM"
date: 2012-04-29
forum: General Help
---

### Post by wesg on 2012-04-29
I just bought a 3TB drive for the purpose of adding to the LVM pool in my server. After formatting it as Linux LVM, the LVM utilities are detecting it as 2TB only. fdisk -l shows 3TB. I've added all the space to a logical volume, because I thought another terabyte available to my other volumes. 

What can I do?

---

### Post by Cheesemill on 2012-04-29
Using a normal msdos partition table has a limit of 2TB for each partition.

You may need to format the drive with a GPT partition table to have all 3TB accessible.

You can do this with gparted - Device > Create Partition Table and then select GPT as type (this will erase alll data on the drive).
You will then be able to create a 3TB LVM partition that displays the correct size.

---

### Post by wesg on 2012-04-29
That's what I think it is, but I've already added it to the volume, so I think I'll leave it as is. Webmin reports it partitioned with GPT but doesn't show an LVM format, so I don't know. At this point, since it seems to work well enough, I'll leave it be and maybe rebuild it later in the year (hopefully when HDD prices drop).

---

