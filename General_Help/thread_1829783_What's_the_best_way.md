---
title: "What's the best way"
date: 2011-08-20
forum: General Help
---

### Post by Brad55 on 2011-08-20
What is the best way to down grade from U10.10 to 10.04?

I want the LTS that U10.04 has but I have U10.10 installed, I really don't want to lose what I have in my home but it can be formated if need be.

Would I still have all my info and settings if I just formated root, and installed U10.04? Or would there be a lot of left over settings?

---

### Post by Frogs Hair on 2011-08-20
Backup your data and do a clean installation of 10.04 . There is no way to downgrade as far as I know .

---

### Post by Ocxic on 2011-08-20
You will need to reinstall, and yes you can keep your home partition, I've done this several time before, but I would suggest creating a temporary user upon installing the replacement OS to avoid data loss. just recreate you user after the install is finished and get it to use the existing home folder.

---

### Post by Brad55 on 2011-08-24
Thanks for the information, I will try it out.

---

### Post by haqking on 2011-08-24
> **Frogs Hair said:**
> Backup your data and do a clean installation of 10.04 . There is no way to downgrade as far as I know .


There is a way [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)


however i dont like it, its messy and i would never receommend it.

Clean Install.

Or best bet which is what i do, always have a image of a clean install so you can always clone it back.  I use Clonezilla.

peace

---

### Post by Topsiho on 2011-08-24
I too think the best thing to do is a clean install.

If you already have a separate partition for /home, then you'll have to be careful NOT to format this partition.

If you don't have /home sitting in it's own partition, then best thing to do is creating a partition for /home, set it's mountpoint to /home, filesystem ext3 or ext4 (ext4 is newer, and well tested by now). So next time when doing an install, you can leave it unformated, and so keep your personal files and settings.
ALWAYS DO A BACKUP, though.

When creating a new partition for /home, you need to know that on a disk no more than 4 Primary partitions may exist. If you need more (and you already need three partitions: /, /home and swap; best thing to do is create Logical partitions for /home and swap. For / a logical partition is OK too, but I have noe experience with this.
Logical partitions sit in an Extended Partition, which is a Primary partition used as a container for the Logical partitions.

Topsiho

---

