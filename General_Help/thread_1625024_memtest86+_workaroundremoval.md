---
title: "memtest86+ workaround/removal?"
date: 2010-11-18
forum: General Help
---

### Post by purple-spear on 2010-11-18
My computer is old, and it has faulty memory, but it still runs fine. I have had no problems with downloading/installing updates and programs, and everything worked fine. Until memtest came along. It ran by itself (I think my dad made it the first boot option in grub), and now if I try to install any packages or programs, it will either say "Grub installation failed" or that any packages I tried to install failed. If I removed memtest, would that make it possible for me to install stuff again? Or is there a way to work around it?

If it helps, the main error report I get is: "E: memtest86+: subprocess installed post-removal script returned error exit status 127"

---

### Post by drs305 on 2010-11-18
Try running this to repair the package:
```
sudo apt-get install -f
```

If that doesn't work, this command will rename the post-rm script for memtest so it won't complain. It is a way *around* the problem, not really a solution:

```
sudo mv /var/lib/dpkg/info/memtest86+.postrm /var/lib/dpkg/info/memtest86+.postrm.bad
```

---

