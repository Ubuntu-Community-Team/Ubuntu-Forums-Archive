---
title: "mtab being overwritten??"
date: 2010-05-13
forum: General Help
---

### Post by bbrand on 2010-05-13
Hey all

v10.4 in place, new install.

Now this is really weird, my mtab keeps on being replaced with a default mtab (from where?). I loose my NFS mounts and only notice when they cannot be reached. This also happens it seems randomly (just make it easier to debug and fix)

Easy fix but irritating and very confusing.

Now what process has the ability/authority to replace my mtab, that process should have sudo authorization, correct? Is there some kind of silly root kit doing this?

Been with Ubuntu for years and years now but have never come across this one..

---

### Post by DawieS on 2010-05-13
The **/etc/mtab** file is a system file that is constantly being updated by the system. You may view the file to see what devices is currently mounted. Thsi file is not supposed to be edited.

The **/etc/fstab** file was traditionally being used to adjust disk mounting options.:smile:

---

### Post by bbrand on 2010-05-14
Thank you sir!! My understanding was that mtab did the actual mount. I tweaked fstab (added "auto" to the appropriate lines there) and it now does mount at boot time.

cheers
Ben

---

