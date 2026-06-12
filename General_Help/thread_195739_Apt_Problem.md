---
title: "Apt Problem"
date: 2006-06-13
forum: General Help
---

### Post by Ratman on 2006-06-13
I seem to have a problem with apt. When upgrade/install some programs that uses some sort of command like ldconfig during the installation the installation fails and tells me that the command wasn't found and the the PATH isn't configured. The PATH seams to be configured correctly as I can type ldconfig in a terminal both as user and as sudo (root).

I found that one solution is to edit the .postinst and .postrm files in /var/lib/dpkg/info for the each file that had the problem and and the path to ldconfig.

Does any one have a better solution?

---

