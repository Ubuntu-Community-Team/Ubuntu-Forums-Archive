---
title: "Virtualization + boot on USB key : pb with VMWare. Debug or alternative ?"
date: 2009-06-26
forum: General Help
---

### Post by aurelieng on 2009-06-26
Dear all,

A few month ago, I installed ubuntu on several USB keys. Using VMWare Server 1.x, I was able to boot directly from the USB key, by adding them as "Raw disks" to the VM. This was really convenient since it was possible to configure Ubuntu without having to generate an ISO, and to boot on the key from within an existing OS.

Recently, I upgraded to VMWare server 2, and the "raw disk" option is gone. I found the thread [http://communities.vmware.com/thread/177112](http://communities.vmware.com/thread/177112), suggesting to use the SCSI passthrough with /dev/sg* (/dev/sg3 in my case). Upon boot, however, the VM seems to hang when looking for the bootloader, and my USB key LED keeps blinking. I know that the USB key I am testing is OK since it is possible to boot a physical computer from it.

What do you think the problem could be ?
How to debug this strange behaviour ?
Are there other simple solutions around to boot from a USB stick in a virtual machine (virtualbox, qemu) ? 

Cheers,

Aurélien.

---

