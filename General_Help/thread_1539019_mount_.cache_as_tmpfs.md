---
title: "mount .cache as tmpfs"
date: 2010-07-26
forum: General Help
---

### Post by kainalu on 2010-07-26
I mount my /tmp as tmpfs in fstab, and have no bad results, however, I was wondering what would happen if I mounted ~/.cache there as well. Any Ideas? Is this a bad move, or could it be detrimental?

Thanks!

---

### Post by kainalu on 2010-07-31
I think I can answer my own question now, in case other people care in the future.

.cache can be mounted as temp, but it may not be efficient if the system is rebooted often because some programs will attempt to create their needed cache at every start of the program if it isnt already there, and others keep stuff there semi-permanently ( eg. album covers in some music progs ) 

It doesnt seem to be detrimental to make it a ramdrive, but may cause small performance issues (eg. rebuilding the cache takes time when the program is started) or loss of minor data (eg. missing album covers). I did mount the google-chrome cache as a ramdrive, and am loving it.

---

