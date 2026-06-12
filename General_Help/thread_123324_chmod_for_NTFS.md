---
title: "chmod for NTFS?"
date: 2006-01-29
forum: General Help
---

### Post by everdred on 2006-01-29
Quick question: how should the device file and mount point for my NTFS partition be **chmod**ded in order to make it readable by all users, or at least me as non-root? As it is now, I get a "Permission Denied" when doing stuff with it like **ls** unless I use sudo.

Here's the line from my fstab:
```
/dev/hda1 /media/hda1 ntfs defaults 0 0
```

:KS

---

### Post by RAOF on 2006-01-29
[QUOTE=everdred]Quick question: how should the device file and mount point for my NTFS partition be **chmod**ded in order to make it readable by all users, or at least me as non-root? As it is now, I get a "Permission Denied" when doing stuff with it like **ls** unless I use sudo.

Here's the line from my fstab:
```
/dev/hda1 /media/hda1 ntfs defaults 0 0
```

:KS[/QUOTE]
From [the wiki]("https://wiki.ubuntu.com/AutomaticallyMountPartitions?action=show&redirect=AutomaticallyMountMSWindowsPartitions"):

You want to change your fstab line - replace "defaults" with "ro,auto,user,fmask=0111,dmask=0000".

The reason you don't have permissions to the NTFS drive is that the kernel NTFS driver doesn't (and can't) support the NTFS security model, and the default mount options (given by "defaults") are no access for anyone but the owner - root.

---

### Post by everdred on 2006-01-29
Thanks! It worked right straight out of the box but I had tweaked some stuff and it no longer did... until now. :)

---

