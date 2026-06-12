---
title: "Resuming interrupted copy"
date: 2011-05-16
forum: General Help
---

### Post by verevie on 2011-05-16
I'm backing up an old hard drive and copying about 300GB of files. It  had about 50GB left when I got a kernel panic and now I want to resume  the copying. Is there a way to do this in Ubuntu? (A don't copy if file  already exists but copy all files that don't already exist argument?)

---

### Post by oldos2er on 2011-05-16
The -n or --no-clobber option is what you're looking for. See **man cp**

---

