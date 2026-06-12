---
title: "BtrFS"
date: 2010-07-12
forum: General Help
---

### Post by agamjain on 2010-07-12
I read in the UWN that the current ext4 filesystem is being replaced by BtrFS in Ubuntu 10.10 Maverick Meerkat. So, when I upgrade from Ubuntu 10.04 will my filesystem automatically change or do I have to reinstall the entire OS once again?

---

### Post by marshmallow1304 on 2010-07-12
AFAIK, BtrFS will be available in MM, but at the moment it's doubtful that it will be the default.

---

### Post by Blue Beard on 2010-07-12
There is a utility to convert to convert ext3 or ext4 to brtfs documented at [https://btrfs.wiki.kernel.org/index.php/Conversion_from_Ext3](https://btrfs.wiki.kernel.org/index.php/Conversion_from_Ext3).

Most-likely btrfs will not be default in 10.10 but a manual format option.

Btrfs has no advantage unless you want the extra features such as snapshots used in Fedora for software installation rollback.

---

### Post by agamjain on 2010-07-12
> **Blue Beard said:**
> There is a utility to convert to convert ext3 or ext4 to brtfs documented at [https://btrfs.wiki.kernel.org/index.php/Conversion_from_Ext3](https://btrfs.wiki.kernel.org/index.php/Conversion_from_Ext3).
 
Most-likely btrfs will not be default in 10.10 but a manual format option.
 
Btrfs has no advantage unless you want the extra features such as snapshots used in Fedora for software installation rollback.
 So, it's better to stay on ext4?

---

### Post by foxmulder881 on 2010-07-12
For now, stick with ext4. Above posts are correct, btrfs will not be default, not on Ubuntu anyway. It's too young. Possibly on Fedora 14 though.

---

### Post by agamjain on 2010-07-12
One more question. If there are some corrupt configuration files on my system, would they be corrected when I upgrade?

---

### Post by jerenept on 2010-07-12
In before the Community Cafe.

I do not believe that it will be important to the average user, but BTRFS can fsck while online (i think).

Ext4 is probably going to remain default.

---

### Post by cariboo on 2010-07-13
There is a btrfs [thread]("http://ubuntuforums.org/showthread.php?t=1481973&highlight=btrfs") in the Maverick Testing and Discussion sub-forum if anyone is interested.

---

### Post by 3rdalbum on 2010-07-13
> **agamjain said:**
> One more question. If there are some corrupt configuration files on my system, would they be corrected when I upgrade?

You'll be asked if you want to keep your configuration files, or use the package maintainer's version (only for files that are different on your system to how the new ones are). You'd select "Use package maintainer's version". You also get the ability to look at the new and old files to determine what you want to do.

---

