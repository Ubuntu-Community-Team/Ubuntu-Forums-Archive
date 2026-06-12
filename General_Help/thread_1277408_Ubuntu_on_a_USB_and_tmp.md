---
title: "Ubuntu on a USB and /tmp"
date: 2009-09-28
forum: General Help
---

### Post by viralmeme on 2009-09-28
I'm running Ubuntu from a USB device with 512MB reserved space. df reports /tmp at 63%. I also notice that Youtube vids are downloaded here, while playing. Except the lookahead progression bar stops when /tmp fills up.

Is it possible to mount a second USB and remount /tmp here. I figure a script would need to, stop X, remount /tmp, restart X.

df reports the current USB as 30% full. So where is all that free space. If I select anythng more than 512 for reseved space then it hangs at boot, at initialising RAMFS. Is it still possible to create a casper-rw partition on the USB and the system will store files here?

/dev/sdb1 3.9G  1.2G  2.7G  30% /cdrom
tmpfs 513M  307M  181M  63% /tmp

---

