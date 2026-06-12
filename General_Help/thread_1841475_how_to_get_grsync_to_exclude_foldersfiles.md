---
title: "how to get grsync to exclude folders/files?"
date: 2011-09-09
forum: General Help
---

### Post by mamboze on 2011-09-09
Hi,

I'm using grsync to backup two networked computers. 
The source for grsync is:
/home/roy/grsync_test/
the destination: 
/media/network_backup/backups/prospero/

This works OK, but I've been unable to work out how to exclude this folder   xclude_this/cindy 

here's the absolute path
/home/roy/grsync_test/xclude_this/cindy

Grsync Advanced options>Additional options, is 
-e  --exclude-from=xclude_this/cindy/

Any help would be appreciated

---

### Post by mamboze on 2011-09-11
Got it! :D :D
Grsync Advanced options>Additional options, is
--exclude=xclude_this/

Now onto setting up a file containing all necessary exclusions.

---

