---
title: "Dual Boot with XP - Delete existing ext4 partition..possible?"
date: 2010-02-03
forum: General Help
---

### Post by Stan_1936 on 2010-02-03
Windows XP installed on ENTIRE hard drive.

I am comfortable with installing Ubuntu(it would be installed 2nd) so as to dual boot it with Windows XP.  If I remember correctly(I haven't dual booted for a while), it would create a swap partition and an ext4 partition.  I don't care about a separate home partition and won't ever be creating one.

Here's the thing.....I to UPGRADE everytime a new version of Ubuntu is released.  I know that there may be other ways to do it but this is what I want to do(**all from the partition editor in an Ubuntu 32-bit Live CD**):

- Delete the ext4 partition, resulting in unpartitioned space
----> Apply Changes
- leave the swap partition untouched
- Create a new ext4 partition in the unpartitioned space
----> Apply Changes

Using the Manual Partition option, install the the new version of Ubuntu to the freshly created ext4 partition and also use the existing(untouched) swap partition when the installer(manual) prompts for a SWAP area.

**[COLOR="Red"]Questions:[/COLOR]**
1.  Can this be done?  IF not, how could I achieve an easily upgradeable dual boot setup?
2.  Presumably, the old GRUB would be deleted when I delete the old ext4 partition......if the answer to question 1 is YES, then would I need to do anything additional/fancy to GRUB?  OR would the fresh installation take care of GRUB?  IF the answer is NO, what would I need to do in terms of GRUB?

---

### Post by audiomick on 2010-02-03
That should work. You will need to choose the manual partitioning option during the re-install and mount the swap partition.

In fact, you could do the re-format of the old install during the installation if you want to.

---

### Post by Stan_1936 on 2010-02-03
> **audiomick said:**
> ...you could do the re-format of the old install during the installation if you want to.

How?

By selecting the Manual Partition option in the installation?  Will that give an option to format the old ext4 partition?  OR will it only give the option to format the WHOLE hard drive?

---

### Post by tudor117 on 2010-02-03
It works just fine.
I do it every release. However I have a separate partition for my home folder. That way all my configs are kept.

---

### Post by audiomick on 2010-02-03
> **Stan_1936 said:**
> How?

By selecting the Manual Partition option in the installation?  Will that give an option to format the old ext4 partition?  OR will it only give the option to format the WHOLE hard drive?
If you select the manual partitioning option during the install, it starts gparted. You can do pretty much anything there that you can do with gparted.

---

### Post by Stan_1936 on 2010-02-03
Right.....sounds like it will work then.

I'm going to wait until the weekend, when I try it, before marking the thread as solved.

---

