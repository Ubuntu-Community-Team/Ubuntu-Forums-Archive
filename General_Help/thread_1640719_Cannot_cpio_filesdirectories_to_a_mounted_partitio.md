---
title: "Cannot cpio files/directories to a mounted partition"
date: 2010-12-08
forum: General Help
---

### Post by jgsylvester on 2010-12-08
I am trying to copy my /home directory to a separate partition. I have seen a lot of info on this on the internet. Most of the information uses cpio to copy the files. The destination partition has been successfukky mounter. From /home, I enter
find . -depth -print0 | cpio --null --sparse -pvd /mnt/home


I get the following typical errors:
cpio: cannot make directory `/mnt/home//./joe': Permission denied
cpio: /mnt/home//./joe/.openoffice.org/3/user/uno_packages/cache/uno_packages/jPBRgQ_/oracle-report-builder.oxt/registry/schema/org/openoffice: Cannot mkdir: No such file or directory
/mnt/home//./joe/.openoffice.org/3/user/uno_packages/cache/uno_packages/jPBRgQ_/oracle-report-builder.oxt/registry/schema/org/openoffice
cpio: cannot make directory `/mnt/home//./joe': Permission denied

for every directory/file. I can copy individual files/directories using cp. What am I doing wrong?

---

### Post by jgsylvester on 2010-12-08
[Solved]. I changed permissions of /mnt/home to 777, and everything works as expected.

---

### Post by dcstar on 2010-12-08
> **jgsylvester said:**
> [Solved]. I changed permissions of /mnt/home to 777, and everything works as expected.

The thread is NOT solved until YOU mark it. Read below.

---

