---
title: "Fast way to verify huge files...."
date: 2010-10-29
forum: General Help
---

### Post by ragtag on 2010-10-29
I'm looking for a fast way to verify a copy of a folder with 150Gigs of data, in 33 files. Some of the files are a few kb, while a few are 20-30Gigs.

I've done a file count, which is quick, but doesn't verify that all the files are intact.

I tried running md5sum on them, which works, but will probably take as long as copying the files in the first place.

diff works too, but is slow too.

Any suggestions?

:)

---

### Post by EBT on 2010-10-29
something like "diff"ing the outputs of source and target "ls -lRa".. should be enough. comparison of filesizes may be all that you want to do,

---

