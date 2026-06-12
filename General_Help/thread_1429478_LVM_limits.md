---
title: "LVM limits"
date: 2010-03-14
forum: General Help
---

### Post by zigi on 2010-03-14
1) What is the size of VG metadata?
[INDENT]a) How many LVs or PVs can contain by default?
b) How much space (bytes) does occupy the metadata of LV or PV?
c) Can I resize(grow) the metadata space later?
d) Or is it better to store it outside the VG (PV) somewhere on another disk and filesystem?[/INDENT]

2) How many VGs / LVs / PVs can I create / have in system?

3) From documentation of [RHEL - LVM]("http://www.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/5.4/html/Logical_Volume_Manager_Administration/lvm_metadata.html"):
> You can specify the size of metadata with the area -- metadatasize option of the pvcreate command.The default size is too small for volume groups with many logical volumes or physical volumes.
[INDENT]How many is "many"?[/INDENT]

---

