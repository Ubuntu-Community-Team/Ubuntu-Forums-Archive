---
title: "Gparted make a Mac partition"
date: 2011-01-19
forum: General Help
---

### Post by avatarmonkeykirby on 2011-01-19
What partition type does Mac OS X use, and can gparted create one?

---

### Post by Blueshift1990 on 2011-01-19
It depends what you need to format and work with Mac OSX if it is just a jump drive fat 32 should work.

---

### Post by avatarmonkeykirby on 2011-01-19
Idyllically, it could run on the partition that gparted created; however I'm just trying so mimic the installation disk on the hard-drive. So fat32 sounds like it should work.

(Yes, I am well aware that this is very likely to not work.)

---

### Post by Blueshift1990 on 2011-01-19
In that case fat will not work. It can only support files up to 4gb in size not primary hardrive

---

### Post by avatarmonkeykirby on 2011-01-19
I see. In that case, I would like to reinstate my original question. Or rather, supposing I had a large jump drive (say an 8gb drive) what would I format it as so a Mac could read it?

---

### Post by Blueshift1990 on 2011-01-19
It can format the whole drive it just cant handle say a video file that is 4 GB in size but the jump drive could be up to 32GB and it could still be formated as Fat 32.

---

### Post by srs5694 on 2011-01-20
FAT32 can be up to 16 TiB, depending on the cluster size, according to [Wikipedia.](http://en.wikipedia.org/wiki/File_allocation_table) The main limit that's causing problems today is with file size, which is limited to one byte under 4 GiB.

It's still not clear to me what you intend to do, avatarmonkeykirby. "Run on the partition" and "mimic the installation disk?" Do you mean you want to install OS X to the partition you create? Make a backup of an OS X installation? Copy the OS X installation DVD to another medium and use it to install or upgrade a computer? Just what do you want to do, precisely, and from what OS?

To answer the original question, though, OS X uses the Hierarchical File System Plus (HFS+), aka Mac OS Extended filesystem. GParted can manage HFS+ partitions, but you've got to have some packages installed in Ubuntu for this to work. IIRC, you need the hfsplus and/or hfsprogs package, and maybe something else, as well.

The actual partition type code is 0xAF on a Master Boot Record (MBR) disk, or 48465300-0000-11AA-AA11-00306543ECAC on a GUID Partition Table (GPT) disk, but GParted hides these codes from users. OS X uses GPT natively for its partition table type, so depending on your needs, you might need to use GPT partitions on the disk.

---

### Post by theunbubba on 2012-03-13
> **srs5694 said:**
> FAT32 can be up to 16 TiB, depending on the cluster size, according to [Wikipedia.](http://en.wikipedia.org/wiki/File_allocation_table) The main limit that's causing problems today is with file size, which is limited to one byte under 4 GiB.

It's still not clear to me what you intend to do, avatarmonkeykirby. "Run on the partition" and "mimic the installation disk?" Do you mean you want to install OS X to the partition you create? Make a backup of an OS X installation? Copy the OS X installation DVD to another medium and use it to install or upgrade a computer? Just what do you want to do, precisely, and from what OS?

To answer the original question, though, OS X uses the Hierarchical File System Plus (HFS+), aka Mac OS Extended filesystem. GParted can manage HFS+ partitions, but you've got to have some packages installed in Ubuntu for this to work. IIRC, you need the hfsplus and/or hfsprogs package, and maybe something else, as well.

The actual partition type code is 0xAF on a Master Boot Record (MBR) disk, or 48465300-0000-11AA-AA11-00306543ECAC on a GUID Partition Table (GPT) disk, but GParted hides these codes from users. OS X uses GPT natively for its partition table type, so depending on your needs, you might need to use GPT partitions on the disk.

Thank you for actually giving a straight answer. HFS+ I went to 16 sites before finding your post. Lifesaver!

---

