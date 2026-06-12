---
title: "Default torrent client problem"
date: 2009-09-22
forum: General Help
---

### Post by avangerx on 2009-09-22
Hi everyone, 
Recently when I use the default torrent client it starts downloading torrents that I choose and in mare seconds it says "permission denied: and stops downloading the torrents. I did not have this issue before and did not change anything. Any ideas?
Thanks.

---

### Post by prem1er on 2009-09-22
You probably changed the permissions on the directory where Transmission downloads to.  Open a terminal and do 

```
ls -lrt <download dir>
```

on the directory where the client is set to download into.

---

