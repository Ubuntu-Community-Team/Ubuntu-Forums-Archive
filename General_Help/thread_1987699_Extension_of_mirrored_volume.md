---
title: "Extension of mirrored volume"
date: 2012-05-26
forum: General Help
---

### Post by W29 on 2012-05-26
Hi

I was trying to extend a logical volume with the next command:
```
lvresize -L +100GB /dev/vg/FSalumni
```It gives me the next error:
```
Not enough PVs with free space available for parallel allocation.
Consider --alloc anywhere if desperate.
```Free space:
```
Free  PE / Size       111357 / 434.99 GiB
```which should be enough.
After some research, I found that it has something to do with mirrored drives.
```
~$ lvs -a -o +stripes,devices
  LV        VG   Attr   LSize   Origin Snap%  Move Log Copy%  Convert #Str Devices                                           
  FSalumni  vg   -wi-ao 100.01g                                          3 /dev/md1(85762),/dev/md1(94296),/dev/md1(103684) 
```My question: How can I resize a mirrored/striped volume?

---

