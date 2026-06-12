---
title: "Legacy Grub - #groot="
date: 2010-03-15
forum: General Help
---

### Post by Barriehie on 2010-03-15
Learned a new thing about grub today; although the experience wasn't planned!  For whatever reason my menu.lst file was trying to boot the image files from (hd0,3) when in actuality they were on (hd0,0).  They used to be on (hd0,3) until I moved my OS from hda2 to hda1.  So anyway, I muddled through getting it to boot and then took a long slow look at menu.lst and noticed:
```

#groot=(hd0,3)
```  After googling a bit that got edited to ```
#groot=(hd0,0)
``` and it booted like it's supposed to.  So, if anyone else gets that weird issue with the wrong partition being displayed for booting then **groot** might be a place to look!

---

