---
title: "No possible to install Firefox extension if profile is on NTFS (NTFS-3g) volume."
date: 2010-07-16
forum: General Help
---

### Post by bubbles.way on 2010-07-16
Reproducible with Firefox 3.6.6 (installed from Ubuntu 10.04 repository), on Dell D620, Ubuntu 10.04
Steps to reproduce:
1) start Firefox from command line &quot;firefox -P&quot;
2) create new Firefox profile on NTFS volume (mounted with NTFS-3g)
3) add NoScript extension (through extension manager Get Add-ons), restart Firefox as suggested
4) extension is not added to Firefox
 In case at step 2) profile is created on Linux volume, at 4) extension is added to firefox.
I'm not 100% sure, but I think this bug is related to Firefox 3.6 update (no problems with Firefox 3.5).
 I did not make proper investigation, but I have feeling same problem applies to Thunderbird 3.1.
 Did anyone experience same problem?  This issue does not allow to share Firefox/Thunderbird profile on dual boot machine (Ubuntu/WindowsXP).

---

### Post by bubbles.way on 2010-07-22
Problem is solved. It is necessary to mount ntfs drive with uid of user that Firefox profile belongs to:

e.g.:
UUID=14DF7D00C4778279 /mount/ntfs_drive         ntfs    defaults,nls=utf8,umask=007,uid=1001,gid=1001 0       0

Without that it is possible to write to the drive, but all new files belong to root and Firefox/Thunderbird has a problem with it.

---

