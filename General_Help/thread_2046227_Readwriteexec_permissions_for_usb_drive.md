---
title: "Read/write/exec permissions for usb drive"
date: 2012-08-22
forum: General Help
---

### Post by Klasanov on 2012-08-22
How do I get this to work?

I just reformatted a usb drive to the ext4 format, and made a smaller partition to fat32 so that I can use files with windows/mac os.

However, now I am completely unable to read, write, or execute files within the ext4 partition on my usb drive. Before, with the fat32 parititon (which it was fully before I reformatted it), I was able to read and write (but not exec)

I am unable to change the permissions.

How do I fix this?

---

### Post by ajgreeny on 2012-08-22
The best way is to give the external drive ext4 partition a label so it will always mount to /media/*labelname* then run terminal command ```
sudo chown user:user /media/*labelname*
```

---

