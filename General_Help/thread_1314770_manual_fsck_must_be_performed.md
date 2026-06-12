---
title: "manual fsck must be performed"
date: 2009-11-04
forum: General Help
---

### Post by cmatwood1 on 2009-11-04
I have tried running manual fsck on my server.  Can get it to complete.  I am very Linux "Green".
 
I tried stuff like sudo fsck -y  and fsck /dev/hda5  
 
Not resolving my issue.  Anyone have any insight?

---

### Post by mikewhatever on 2009-11-05
Is hda5 really the system partition? What's the output of sudo fsck -vp /dev/hda5?

---

### Post by doas777 on 2009-11-05
is your disk mounted? if so, reboot into recovery mode, and try the fsck again.

---

