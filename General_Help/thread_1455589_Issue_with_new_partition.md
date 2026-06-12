---
title: "Issue with new partition"
date: 2010-04-16
forum: General Help
---

### Post by mrwpink on 2010-04-16
Hi,

I have created a new partition

/dev/cciss/c0d0p2            8489       17709    74067682+  83  Linux

I formatted it with

 mkfs.ext3 /dev/cciss/c0d0p2

Labelled it

e2label /dev/cciss/c0d0p2 /data

then mounted it

LABEL=/data    /data        ext3    defaults    1 1

I changed the owner:group to will:will on data

chown -R will:will /data

but when I try and access it I get a permission denied 

will@node:/data$ ls
ls: cannot open directory .: Permission denied

Has anyone got any ideas on what it could be? I have never had this happen before 

Distributor ID:    Ubuntu
Description:    Ubuntu 8.04.3 LTS
Release:    8.04
Codename:    hardy

Thanks,
Will

---

