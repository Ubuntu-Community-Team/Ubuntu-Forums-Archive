---
title: "Append img file with fallocate Command"
date: 2012-05-16
forum: General Help
---

### Post by jgooch on 2012-05-16
I'm using a file for an iscsi block device. I made it using fallocate ( ```
fallocate -l 200g /mnt/iscsi/lun0.img
``` ) and with the "iscsitarget" package. 
 
Uisng Windows SBS 2011, I connected(iscsi initiator tool from Windows admin tools) to it and formatted it NTFS, and started using it as a local drive. So far, so good. 
 
But I'd like to append another 300G to it , for a total of 500G. I think this command will work ( from the man page ):
 
```
 
fallocate -o 200g -l 300g /mnt/iscsi/lun0.img

```
 
The thing that I'm uncertain is the offset( -o ), I'm not sure if its value should match the size, or should be 1 unit greater than the size of the existing .img file. 
 
Does anyone with experience using fallocate care to chime in? I'm new to iscstarget and fallocate, so I'm not yet confident in using them.

---

