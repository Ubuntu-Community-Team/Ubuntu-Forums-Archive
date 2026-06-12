---
title: "Virtual drive for Ubuntu?"
date: 2009-10-18
forum: General Help
---

### Post by Szat on 2009-10-18
Hello everyone, I was wondering if there was virtual drive software like Daemon Tools for Ubuntu. Thanks

---

### Post by KlinerDraken on 2009-10-18
use the mount command 
```
mount -o loop -t iso9660 foo.iso /mountpoint
```

or install a gui

```
sudo apt-get install gmountiso
```

---

### Post by Szat on 2009-10-18
Thanks a lot!

---

