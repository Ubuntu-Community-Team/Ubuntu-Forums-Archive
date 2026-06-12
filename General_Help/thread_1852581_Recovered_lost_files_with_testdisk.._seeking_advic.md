---
title: "Recovered lost files with testdisk.. seeking advice on clearing unwanted leftovers"
date: 2011-09-30
forum: General Help
---

### Post by sammya on 2011-09-30
So I recently used testdisk to recover files I had accidentally deleted. I got everything back fine but I have noticed a lot of files left over that I don't need. The partition is currently shown as 'unallocated space' but still has all these files there.

Also..wanting to do a complete brand new install of ubuntu 11.04 and wanted to completely wipe my disk (so no hidden files that you can find with testdisk etc). how would i go by completely wiping my hdd?

Ty

---

### Post by oldfred on 2011-09-30
See man shred for details on parameters
sudo shred -n2 -v /dev/sdb

Link to dban
[http://www.dban.org/](http://www.dban.org/)

Some may suggest dd, but I do not normally suggest it as its nickname is Data Destroyer. Any typo and you destroy something you did not mean to.
Entire Drive - May take a long time:
sudo dd if=/dev/zero of=/dev/XdY

---

### Post by An Sanct on 2011-09-30
Use [bleachbit]("http://bleachbit.sourceforge.net/download/linux") or some other wiping tool.

PS no need to wipe, unless you want the files to disappear totally.

---

### Post by CHEWS on 2011-09-30
SHred the entire drive with wiping live cd distro, then reset harware defualt by writing 0s to the entire disk

---

