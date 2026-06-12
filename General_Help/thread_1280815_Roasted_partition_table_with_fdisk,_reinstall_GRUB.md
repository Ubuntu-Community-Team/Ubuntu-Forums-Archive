---
title: "Roasted partition table with fdisk, reinstall GRUB?"
date: 2009-10-02
forum: General Help
---

### Post by alphaniner on 2009-10-02
I intended to partition a blank disk but accidentally chose my boot disk.  I only realized it after I wrote the changes to disk and was told the device was busy.  I recreated the partitions (thankfully I had fdisk -l output) and I didn't format, so I think my data should be intact.  However, I used the fdisk 'o' option (create a new empty DOS partition table) which I'm afraid may have wiped the MBR (and GRUB).  Is it possible to check if GRUB is still installed and/or re-install it from the running system?

---

### Post by Giblet5 on 2009-10-02
Run ```
sudo fdisk -l
```

What is the first disk? /dev/sda?

```
sudo grub-install /dev/sdNNN
``` where NNN is the drive letter from fdisk.

That'll rewrite the MBR and it will print out what it thinks the first disk drive is.

---

### Post by alphaniner on 2009-10-02
That seemed to work, but how will it know where to look for menu.lst?

edit: Nevermind, I see the line in the output indicating it already found it.  Thanks.

---

### Post by oldfred on 2009-10-02
The MBR has two parts one tells the system where to boot and the other defines the DOS partitions.

You need to run testdisk to recover the partitions.

---

