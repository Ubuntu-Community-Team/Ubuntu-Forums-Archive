---
title: "Grub2 Windows 7 Error"
date: 2010-03-15
forum: General Help
---

### Post by johngreth on 2010-03-15
I am dualbooting Karmic, windows 7, and fedora. When I boot, Grub2 will boot everything but Windows 7. Instead it says

```
reloc offset is out of the segment
abort.
```

I've tried reinstalling and updating grub2 and I also tried grub. It wasn't a problem until I put Lucid on a 4th partition that's always been there. I let lucid install grub2 and after that windows didn't work, but I got the same error when I reinstalled it from karmic. I got a different error from grub (that I don't remember), but I wasn't positive about the configuration so that may have been my fault.

Any ideas?

---

### Post by johngreth on 2010-04-03
After much research I was able to fix it using fixboot on the windows 7 boot disk.

---

