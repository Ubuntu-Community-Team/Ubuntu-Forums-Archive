---
title: "[Gnome3]Change automount options for a specific partition?"
date: 2011-08-20
forum: General Help
---

### Post by Githlar on 2011-08-20
I have a specific NTFS partition on a USB drive that I wish to enable execute support for. The only way I've found to do this is to add the partition in /etc/fstab with a umask. This poses some problems:

1. Only root can mount it, making it a pain to mount (open terminal, `sudo mount (path from /etc/fstab)`, enter password, close terminal).
2. The system will hang at start if the UUID is unavailable (or, the external disk is unplugged). I run several servers from my machine, so if I do a remote restart it will not come back up because of the hang.

Is there a way to specify to FUSE (which I believe is the handler for auto-mounting in Nautilus) that this partition should have execute access to files?

---

### Post by raja.genupula on 2011-08-20
[http://ubuntuforums.org/showthread.php?t=1507162](http://ubuntuforums.org/showthread.php?t=1507162)

try it :)

---

