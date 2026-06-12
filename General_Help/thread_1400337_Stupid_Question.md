---
title: "Stupid Question?"
date: 2010-02-06
forum: General Help
---

### Post by vacancy77 on 2010-02-06
Hey all. I'm running an iMac from a Ubuntu Live CD. I've got a questionable hard drive, but I'm able to view all my files with thumbnails in Nautilus. When I attempt to copy them to an external LaCie drive, it says "the destination is read-only".

Is this the right forum to be asking? Can someone point me in the right direction?

Thanks

Jonah

---

### Post by cariboo on 2010-02-06
Moved to General Help, as this isn't a security question.

Press Alt-F2 and type:

```
gksu nautilus
```

This command will open the file manager as root, and allow you to copy the files to your external drive.

---

