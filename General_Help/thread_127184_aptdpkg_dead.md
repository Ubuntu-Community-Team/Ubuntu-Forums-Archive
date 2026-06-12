---
title: "apt/dpkg dead"
date: 2006-02-08
forum: General Help
---

### Post by Paool on 2006-02-08
I can't install anything from repo and packages... I've removed fuse packages and now I've got error:

dpkg: syntax error: unknown group `fuse' in statusoverride file 
Press <enter> to exit...

---

### Post by Paool on 2006-02-08
this solved my problem :)

sudo groupadd fuse

---

