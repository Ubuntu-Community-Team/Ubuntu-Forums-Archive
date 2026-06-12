---
title: "Samba/CIFS - denied if file open at other end"
date: 2010-06-29
forum: General Help
---

### Post by kristianz on 2010-06-29
I have a problem with Samba (mounted with CIFS).

I'm downloading stuff at computer A (Windows XP) by uTorrent, sharing the folder over the network while the files are still being seeded, and mounting that folder on computer B (Ubuntu 10.4) with CIFS. The problem is, files that are open in uTorrent on computer A, get "permission denied" when I try to access them on B.

I've mounted the share as 'ro' with 444 permissions, still same problem.

---

