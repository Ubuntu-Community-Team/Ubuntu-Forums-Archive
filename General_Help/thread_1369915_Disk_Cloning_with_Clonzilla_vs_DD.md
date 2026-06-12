---
title: "Disk Cloning with Clonzilla vs DD"
date: 2010-01-01
forum: General Help
---

### Post by Jestersage on 2010-01-01
Is there any reason why is DD still prefer over clonezilla for disk cloning?

---

### Post by VastOne on 2010-01-01
> **Jestersage said:**
> Is there any reason why is DD still prefer over clonezilla for disk cloning?

I prefer DD for its simplicity but it is a matter of taste or choice IMO

---

### Post by cbraxton on 2010-01-01
> **Jestersage said:**
> Is there any reason why is DD still prefer over clonezilla for disk cloning?

Clonezilla understands the filesystem being cloned and does a file-by-file copy, skipping unused sectors. On the other hand, dd just does a sector-by-sector copy of the entire disk.

On a large drive with a lot of empty space dd will take a lot longer to complete the job. However if you are imaging a drive for forensic or data recovery purposes you will want to use dd or a similar tool (I like dd-rescue) to copy all sectors that may contain data.

---

### Post by Jestersage on 2010-01-02
I see. What about Partimage?

---

### Post by Cheesemill on 2010-01-02
Clonezilla actually uses partimage as it's back end.

---

### Post by Mark Phelps on 2010-01-02
> **Jestersage said:**
> I see. What about Partimage?

Partimage does not work with the newer Ext4 filesystem -- the one used by default in new installations of Ubuntu 9.10.

---

### Post by kaibob on 2010-01-02
Just as a FYI, the "Alternative (Ubuntu-based)" version of Clonezilla does work with the EXT4 file sytem. I did a clean install of Karmic when it was released and used the EXT4 file system and grub2. I have created and restored Clonezilla images of this drive on multiple occasions without issue. I always accept the default options when using Clonezilla, which I believe includes the use of partimage.

---

