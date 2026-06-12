---
title: "Can't read hebrew filenames on NTFS partitions"
date: 2005-02-07
forum: General Help
---

### Post by Michael on 2005-02-07
Hi all.

this is how the relevant fstab lines look like:
/dev/sda1	/mnt/Windows	ntfs	umask=000,rw,exec,users,auto,nls=iso8859-8 0 0
/dev/sda2	/mnt/Data	ntfs	umask=000,rw,exec,users,auto,nls=iso8859-8 0 0


All the hebrew files look like this: "????????.xyz (invalid encoding)"

I use the updated hoary (problem was same in warty).

---

### Post by 3david on 2005-10-27
add "utf8" before nls=...
(i don't think u need nls btw)

---

