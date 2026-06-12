---
title: "Scrubbing free disk space"
date: 2011-04-29
forum: General Help
---

### Post by hojjat on 2011-04-29
I'm running [scrub -X](http://linux.die.net/man/1/scrub) to wipe out the free disk space on an Ubuntu machine. It keeps creating 1GB files in the temporary directory I assigned to it, and each file takes several minutes to get done. The one question that I couldn't find an answer to is, does scrub remove these files when it runs out of space (i.e. scrubs all the disk)?

---

### Post by hojjat on 2011-05-05
Since no one answered this, I tested it and the result is negative: The files are not removed. In fact scrub continues its process until it runs out of disk space. At that point, you will need to remove all files created by scrub manually.

---

