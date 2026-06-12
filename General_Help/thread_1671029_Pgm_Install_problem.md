---
title: "Pgm Install problem"
date: 2011-01-19
forum: General Help
---

### Post by Johnym11 on 2011-01-19
I try install PGM as root:
dpkg -i thumbnailme_2.1_amd64.deb
dpkg: error processing thumbnailme_2.1_amd64.deb (--install):cannot access archive: No such file or directory
Errors were encountered while processing:thumbnailme_2.1_amd64.deb

Please help, im novice, Thanks.

Now wite this and I set chmod 777 for all directory:
sudo dpkg -i tamd64.deb
(Reading database ... 23979 files and directories currently installed.)
Preparing to replace thumbnailme 2.1 (using tamd64.deb) ...
Unpacking replacement thumbnailme ...
Setting up thumbnailme (2.1) ...
chmod: cannot access `/usr/bin/thumbnailme': No such file or directory
chmod: cannot access `/usr/bin/mtncore': No such file or directory
chmod: cannot access `/etc/thumbnailme/': No such file or directory
chmod: cannot access `/usr/share/thumbnailme/': No such file or directory

chmod 777 for usr/bin,etc and usr/share


Please hepl.

---

