---
title: "atime option being ignored"
date: 2010-07-13
forum: General Help
---

### Post by erythros on 2010-07-13
I need to enable atime on a specific drive. I edited /etc/fstab to include the atime option. After remounting, 'cat /proc/mounts' shows that the drive was mounted with relatime. The option noatime works. Why is the atime option being ignored?
 
The drive in question is using XFS.

---

### Post by gmargo on 2010-07-13
Try using the **strictatime** option.  See the **mount** man page for more info.

---

### Post by erythros on 2010-07-14
Thank you gmargo!
 
The strictatime option worked.
 
I've fallen into the bad habbit of using the linux.die.net man page repository, which makes no mention of the strictatime option...
 
From now on I will refer to the Ubuntu specific man pages.

---

