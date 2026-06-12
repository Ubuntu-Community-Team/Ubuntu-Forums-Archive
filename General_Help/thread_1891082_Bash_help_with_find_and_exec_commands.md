---
title: "Bash help with find and exec commands"
date: 2011-12-04
forum: General Help
---

### Post by rng on 2011-12-04
I am trying following script which finds files and makes soft links to them in display folder.

```
#!/bin/bash
find $(pwd) -iname "*$1*" -exec ln -sv {} $(pwd)/display/ \;  
```The script is working on ntfs partition of hard disk but not on fat32  (vfat) partitions (tried both hard disk and usb flash drive). The error messages from ln is 'operation not permitted'. I am  otherwise able to create files on fat32 partitions from linux.

How can I resolve this?

---

### Post by papibe on 2011-12-05
Hi rng.

Sadly you can't do anything about it because FAT does not support either symbolic or hard links.

Kind Regards.

---

### Post by rng on 2011-12-05
Thanks for the info.

---

