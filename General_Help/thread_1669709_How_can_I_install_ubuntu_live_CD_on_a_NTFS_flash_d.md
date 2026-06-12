---
title: "How can I install ubuntu live CD on a NTFS flash disk?"
date: 2011-01-18
forum: General Help
---

### Post by checoimg on 2011-01-18
I have ubuntu running on a SD but I can't install it when NTFS formatted wich works faster. What can I do?

Thanks in advance!!! :)

---

### Post by sohlinux on 2011-01-18
NTFS is not faster and neither does it support linux permissions so why not format as ext2 or ext3

---

### Post by checoimg on 2011-01-18
Well under widows I've seen it work faster on transfer. Compared to Fat32

---

### Post by Elfy on 2011-01-18
If you want to install ubuntu on it - format it to a filesystem that it will install to.

It'll not install on ntfs.

---

### Post by sohlinux on 2011-01-18
> **checoimg said:**
> Well under widows I've seen it work faster on transfer. Compared to Fat32

yes ntfs is faster than fat32 but ext3 is as fast or even faster than ntfs. linux will not install to ntfs, even if it did there would be no point in it.

---

### Post by Mark Phelps on 2011-01-18
> **checoimg said:**
> Well under widows I've seen it work faster on transfer. Compared to Fat32

That is when it is installed INSIDE MS Windows -- using Wubi.

You can't install it that way to a flash drive, because Windows installs it like any other app, and it won't let you install stuff to flash drives.

---

### Post by checoimg on 2011-01-18
Ok

---

