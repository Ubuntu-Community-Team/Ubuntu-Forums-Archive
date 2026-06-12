---
title: "Is there a quick way to mount a drive at login?"
date: 2011-02-04
forum: General Help
---

### Post by MR.UNOWEN on 2011-02-04
Hello,

With the most recent build of Ubuntu, is there a quick way to have a FAT partition mount at login?

---

### Post by Rhizoid on 2011-02-04
Add it to fstab

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Or there's a GUI tool listed here:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

How are you mounting it at the moment?

---

### Post by MR.UNOWEN on 2011-02-04
Thanks,

BTW, why isn't there a default utility to do this already. I'd  imagine the everyday user would like certain partitions always mounted. For example I have my music on a separate partition so Windows can get to it.

---

### Post by Rhizoid on 2011-02-04
You can mount it on the fly with a couple of mouse clicks if it's visible in Places - it'll determine it's own mount point in /media usually based on the label or UUID of the partition - I guess that's the most likely reason.

If you want a fixed or special location - eg you want to mount a separate partition as /home then fstab is a better way to achieve that.

---

