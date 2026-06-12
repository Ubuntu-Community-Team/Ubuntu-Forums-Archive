---
title: "How to unmount partitions using root privilege?"
date: 2010-11-05
forum: General Help
---

### Post by nisargshah on 2010-11-05
Hi, I have Ubuntu 10.10 installed on my PC. I want to unmount an NTFS partition using 'Disk Utility'. But when I click on the 'Unmount Volume' option, I receive an error which says - "An error occurred while performing an operation on "17 GB Filesystem" (Partition 5 of Partition 2 of ATA SAMSUNG HD080HJ): The operation failed."
  When I clicked on 'Details', it shows - 
"Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=8A8AC0518AC03C07 from /nisarg" [Where nisarg is the mount point of the volume]
     So please help me!

Thanks in advance,
Nisarg Shah

---

### Post by dcstar on 2010-11-05
> **nisargshah said:**
> Hi, I have Ubuntu 10.10 installed on my PC. I want to unmount an NTFS partition using 'Disk Utility'. But when I click on the 'Unmount Volume' option, I receive an error which says - "An error occurred while performing an operation on "17 GB Filesystem" (Partition 5 of Partition 2 of ATA SAMSUNG HD080HJ): The operation failed."
  When I clicked on 'Details', it shows - 
"Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount UUID=8A8AC0518AC03C07 from /nisarg" [Where nisarg is the mount point of the volume]
     So please help me!

Thanks in advance,
Nisarg Shah

```
sudo umount /dev/whatever
```

---

### Post by efflandt on 2010-11-05
In a terminal: **man umount**

Yes that is spelled properly with no "n" near the beginning.  But to do that as root you need to **sudo umount  /nisarg** [Where nisarg is the mount point of the volume].  Not sure how to do that with gui tools unless you have to be a member of group **disk** (I think group **fuse** is just for auto mounted disks like DC/DVD, usb mass-storage, and Places).

---

