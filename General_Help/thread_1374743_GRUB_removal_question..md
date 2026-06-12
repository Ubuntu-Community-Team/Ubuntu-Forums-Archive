---
title: "GRUB removal question."
date: 2010-01-07
forum: General Help
---

### Post by Confirmed on 2010-01-07
Hello, I installed Sabayon Linux and it's bootloader, but I did not like it. How do I remove it and its bootloader so only Ubuntus remains?:redface:

---

### Post by duanedesign on 2010-01-07
You can boot from a LiveCD and use gparted to format the partition that has Sabayon Linux.
Open a Terminal (Applications > Accesories > Terminal) and type in, or copy & paste, the following command:

```
sudo fdisk -l
```

This will show your partitions and format. Copy and Paste the output of the command into this thread. This will help forum members give you more specific information.

---

